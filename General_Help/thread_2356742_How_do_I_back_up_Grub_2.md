---
title: "How do I back up Grub 2?"
date: 2017-03-26
forum: General Help
---

### Post by steve169 on 2017-03-26
I run Windows 7 and Ubuntu 16.04.02 on the same hard disk. A third partition holds all my data files.

I back up the Windows and data partitions (formatted NTFS) with Norton Ghost 15. Works fine.

I back up the Ubuntu partitions (formatted ext4 and linux swap) with Clonezilla.

**When I restore the Ubuntu partition using Clonzilla, I run into boot problems.**

I get the usual Grub dual-boot selection menu, and if I choose Windows, it boots fine and works.

But if I select Ubuntu, I get the Ubuntu boot-up screen with the little dots marking the time, and it grinds on until it times out.

Obviously, Clonzilla has screwed up Grub 2. Using update-grub2 or Boot Repair doesn't fix the problem. I have to reinstall Ubuntu from scratch.*

[B]Seems to me if I back up Grub 2 separately, I could restore those files as a final step.[INDENT]
Is this feasibile?


[/INDENT]
[/B][INDENT][B]If it is, what Grub 2 files should I copy and restore?

Is it necessary to back up the Linux swap partition?
[/B][/INDENT]

_____________________________


* I've been advised to back up only my data files and in case of a crash simply reinstall Ubuntu. But I do so much customizing of Ubuntu that restoring it from scratch takes hours.

---

### Post by oldfred on 2017-03-26
If you can boot to grub menu, then it sounds like grub is working ok, but you have other issues.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Normally you do not need to backup grub, just reinstall its boot loader to MBR, to let you boot. And yours already boots.
Some may need a full Uninstall/reinstall of grub, but if you can boot to grub menu then that may be overkill and not solve issue.

---

### Post by Cavsfan on 2017-03-26
Or you could customize grub2. It's easy on dual boot or multi-boot systems.

I currently have Windows 10, Arch Linux, Xenial Xerus 16.04 and Zesty Zapus 17.04 on my system.

All you would need to do for starters is this:
Find out which partition your systems are on and plug them into a text file called **/etc/grub.d/06_custom** like this:

```
#!/bin/sh
echo 1>&2 "Adding Xubuntu Xenial Xerus 16.04 LTS and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Xubuntu Xenial Xerus 16.04 LTS" {
    set root=([COLOR=#ff0000]hd0,4[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=#ff0000]sda4[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Xubuntu Xenial Xerus 16.04 LTS (Recovery Mode)" {
    set root=([COLOR=#ff0000]hd0,4[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=#ff0000]sda4[/COLOR] ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='([COLOR=#ff0000]hd0,1[/COLOR])'
    search --no-floppy --fs-uuid --set [COLOR=#ff0000]1CFC7A8DFC7A60C6[/COLOR]
    chainloader +1
}
```

Just change the hd0,4 sda4 and hd0,1 to match your partitions. Plus the UUID in the Windows 7 part.
You can enter **sudo blkid** in terminal to get both the partitions and the UUID of Windows 7.

Then make it executable **sudo chmod +x /etc/grub.d/06_custom** and **sudo update-grub**.

Reboot and you should be able to boot into both windows and Ubuntu.

If you like it, you can add a wallpaper of your choice for a background and change the font size and colors.
There is a Wiki in the 1st post of the green link in my signature that tells you all about it.

Last if all works as you expect, you'd make **/etc/grub.d/20_memtest86+**, **/etc/grub.d/10_linux** and **/etc/grub.d/30_os-prober** unexecutable and update-grub again.
Then you would only have your custom entries. When an update to grub occurs it takes a long time to happen on my system. This method takes about 1 second.
No need to ever do anything unless you add a system, remove a system or change the partition a system is on.

This is the last picture I've taken of my grub screen. That is on Arch and you can only have 2 colored fonts - the normal menu entries and the highlighted menu entry.
But, on Ubuntu you can also choose a color for the text above and below the box with the menu entries.

[[IMG]http://www.zimagez.com/miniature/20170222163033.jpg[/IMG]]("http://www.zimagez.com/zimage/20170222163033.php")

It's up to you. 
Cheers

---

### Post by steve169 on 2017-03-27
Dear oldfred,

I ran Boot Repair and created this report:
[INDENT][B][http://paste2.org/2cYHWCM4](http://paste2.org/2cYHWCM4)
[/B][/INDENT]

As part of the process, Boot Repair installed a fresh version of GRUB, put it didn't cure the problem.

---

### Post by oldfred on 2017-03-27
Grub looks correct and now you have it installed to the MBR of every drive. That is the default reinstall when using Boot-Repair. I suggest for those with multiple drives to only use Boot-Repair's advanced mode and choose an operating system and drive for boot loader install.

The flexnet warning is from some Windows software that has DRM restricted software using Flexnet. It used to be both flexnet & grub wrote into same sectors just after MBR and caused major issues. Grub now has a work around, and tries to avoid the sector(s) used by flexnet.

You may need boot parameters. But with Intel video that usually is not for video, but you may need other boot parameters.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) 
    
I would think this should have been fixed in newer Ubuntu.
 Xeon Skylake Users May Run Into Display Problems With Current Distributions Dec 2015
[http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset](http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset)

---

### Post by steve169 on 2017-03-27
Dear oldfred,

Following your directions, I changed "quiet splash" into "nomodeset."

After restarting and choosing Ubuntu from the boot selections, I received this error message:
[INDENT][B]
[      1.579345] usb 2-1.5: device
descriptor read/all, error -32
/dev/sda5: clean, 311181/3612672 files, 2606740/14441472 blocks[/B]
[/INDENT]
 
 (FYI: sda5 contains the Ubuntu operating system.)

Afterwards, the same unsuccessful boot-up occurs: The little orange dots blink until the process times out.

[B]I have no idea what this error message means or whether it affects what we're doing. Should I ignore it?

Also, need I delete the MBRs on the other partitions and hard disks? If so, how do I find them?
[/B]

---

### Post by oldfred on 2017-03-27
We almost never delete boot loaders in an MBR. Just if or when needed install a correct boot loader. 
The only way to delete is to use dd which has the nickname of data destroyer and can be dangerous, but is powerful.

It seems like it wants to run fsck on every boot?

Try of full fsck:
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

---

### Post by steve169 on 2017-03-28
Dear oldfred,

Yet *another* error.

I simply tried to run **update-grub** and got this message:[INDENT][B]
/usr/sbin/grub-probe: error: failed to get canonical path of `aufs'.

[/B][/INDENT]
What do I do about this?

PS: Many thanks for your time and effort. Please let me know when I start wearing out my welcome.

---

### Post by oldfred on 2017-03-28
That sound like the error you get trying to run sudo update-grub from live installer? Of course live installer cannot be updated. 
You have to be booted or mount your install for that to work. Boot-Repair auto mounts or offers the full chroot to update or totally re-install grub.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by steve169 on 2017-03-31
Dear Oldfred,

I finally threw in the towel and took the coward's way out: I reinstalled Ubuntu using the ext3 format.

This allows me to use my old standby, Norton Ghost 15, to back up everything. I have used Ghost for many years, and I trust it.

So far, Ubuntu seems to be working fine.

Many, *many, **MANY*** thanks for all the time and effort you and others spent on my problem.

---

