---
title: "grub entry to boot to cli only"
date: 2022-06-17
forum: General Help
---

### Post by coley9225 on 2022-06-17
Hello again everyone. I'm looking for a way to make a menu entry in my grub to boot into a cli only setup, no graphics. I know it may sound like a strange desire for a person who has only been using computers for aprox 4 years, and linux for 3 or so, but like most old people(I'm knocking on 60 now), there are reasons for my insanity.

*OBJECTIVE: *To boot into a non-graphical setting from grub at startup (or reboot), and maintain the option to reboot int a full graphical environment if I want to. I want to boot into my current install, minus graphics, rather than install a new OS like ubuntu server, keep easy access to all my files and config settings.

*REASONS:* I often have trouble with my VMs. They are slow,as expected, but didn't expect this slow and sluggish. They slow host to a crawl. I'm thinking by dropping the graphics, I'll free up some resources, thereby making things run a little smoother. Not much help for 'test driving' a new distro, but installed the VMs to practice ssh, so I don't the graphics for that.

The other reason is, in a purely cli environment, I'm forced to use any apps at the basic level. I can't click on gparted, I have to use parted, Have to use terminal commands for timeshift,, etc. I will have to go bare-bones, so to speak. It will be a learning experience, and a better way to learn the inner-workings of linux. I will always have the option to reboot into my standard, graphical install, if I stumble on some things.

I want this mainly because of the VMs. I will likely use a tty console (ctrl+alt+2-6) for practice with using a cli only setting a lot of the time, that way a simple key combo gets me back to a graphical interface to google something if I need to. I researched this idea, and found conflicting methods to accomplish my goal of a menu entry. The one that made the most sense was to copy my current boot menuentry and modify that. Change menuentry from 'lubuntu 20.04' to 'lubuntu 20.04(text)', so I know which is the cli version. Edit the line starting with linux to have something like muti-user.target. And change some other line, I'd have to find it again. Some reply's to the post said it worked, some said it did not, hence my asking here today.

And again. as always, any help would greatly appreciated.

---

### Post by VMC on 2022-06-17
Here's one answer to your question:
[https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode](https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode)

What I do is edit grub then add "text" to end on linux line.

---

### Post by oldfred on 2022-06-17
You can copy grub's default entry in grub.cfg to a new entry in 40_custom.
Then edit/change quiet splash to text on linux line. As per VMC's suggestion above.
If you want it always to be command line, then edit /etc/default/grub and change quiet splash to text. And then run sudo update-grub

[https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub](https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub)

---

### Post by web-user on 2022-06-18
Looks like your Ubuntu is not booting because Grub doesn't know what to boot. You may want to regenerate Grub config using grub-mkconfig command (see man). Also, check the partitions according to your system type (MBR/EFI)

---

### Post by coley9225 on 2022-06-18
Thanks everyone. After reviewing what was offered, and a little more reading, this is what I came up with. Please review the noted changes and verify this is correct.

```


##  change "Lubuntu 20.04.4" to "Lubuntu cli mode" to seperate the 2 entries
menuentry "Lubuntu 20.04.4" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c95e8489-2208-4b25-b12f-69aaaf3d28c1' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  c95e8489-2208-4b25-b12f-69aaaf3d28c1
	else
	  search --no-floppy --fs-uuid --set=root c95e8489-2208-4b25-b12f-69aaaf3d28c1
	fi
	linux	/boot/vmlinuz-5.13.0-51-generic root=UUID=c95e8489-2208-4b25-b12f-69aaaf3d28c1 systemd.unit=multi-user.target ro ## added systemd.unit=multi-user.target 
	initrd	/boot/initrd.img-5.13.0-51-generic
}
```

Also, if I'm reading everything correctly, I copy this into my custom_40 file, save changes and run sudo update-grub. This will net the desired menu entry and boot me into a non-graphical instance. To get back to a graphical setup, I would simply reboot to my default lubuntu install, with full graphics again. 

If everything is correct, I'll remove the comments and proceed to copy into custom_40 file, reboot, and see what happens.

---

### Post by oldfred on 2022-06-18
Ubuntu adds links to most current kernel in /boot.
That makes it easier to always boot most current kernel, without having to edit 40_custom every time a new kernel comes out.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Related forum thread, now so long often better to start at end & work backwards for newest examples.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)

```
menuentry "Lubuntu cli mode" {
    set root=(hd0,2)
        linux /boot/vmlinuz root=/dev/sda2 ro systemd.unit=multi-user.target
        initrd /boot/initrd.img
}

```

You know install is in hd0,2, sda2 (unless nvme0n1p2), so all the search lines are just redundant.
You can use UUID, which may be better, if drives ever change order. Mine often do change when I plug in a flash drive.
Never used systemd entry, but that should work.

---

### Post by coley9225 on 2022-06-18
Thanks oldfred. I put your shortened version into my custom_40 file and saved the file. I'm ready to run sudo update-grub, and will reboot a little later and try it out. I'll post back later with results.

---

### Post by coley9225 on 2022-06-18
Thank you to all who helped. I now have the menu entry that I wanted in grub, and it works. I kept getting error that I had to load kernel first. I booted to graphical and added the kernel number(5.13.0-51-generic) like it is in the default entry. Still wouldn't boot to cli. I had to copy the entire menuentry as is, then edit the lines to what I posted earlier, and booted into a cli setup. I start a VM and updated, and then rebooted my computer, and was able to boot into standard desktop again. So, overall, a success. I'll mark as solved.
Thanks again for the help.

---

### Post by oldfred on 2022-06-18
So the simple one did not work?
Does your /boot have the links to kernel files?
ll # part of output from /boot in my system. 
lrwxrwxrwx  1 root root        28 Jun 15 08:57 initrd.img -> initrd.img-5.15.0-39-generic
lrwxrwxrwx  1 root root        25 Jun 15 08:57 vmlinuz -> vmlinuz-5.15.0-39-generic

---

### Post by coley9225 on 2022-06-18
Yes, those are linked in my /boot.

```

initrd.img -> initrd.img-5.13.0-51-generic
vmlinuz -> vmlinuz-5.13.0-51-generic


```

Either way, thanks to help offered, I've been able to achieve the original goal. Thankss

---

