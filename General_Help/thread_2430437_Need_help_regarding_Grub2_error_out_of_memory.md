---
title: "Need help regarding Grub2 error: out of memory"
date: 2019-11-01
forum: General Help
---

### Post by damndaniel on 2019-11-01
Hello everyone!
I am new to this forum and quite new to linux itself. I was running Ubuntu 18.4.3 LTS alongside windows 10 and Mac OS Mojave with grub2 EFI as default bootloader and the experience was quite nice. Then, I decided to try out the new 19.10 release. So, I backed up the grub config files and installed 19.10. After setting things up, I finally copied over the grub config files (basically, just /boot/grub/themes, /etc/grub.d/40_custom and 00_header files) and ran update-grub. After doing all this, when I tried to boot into the ISOs in the menuentry using loopback (TAILS and systemrescuecd), I always get the "error: out of memory" message during boot. Unlike several cases which I came across while searching for a solution, I am not taken to grub rescue shell. Instead, the system kicks me back to grub menu screen. They were both working fine on 18.4.3 though. Also, this doesn't happen with operating systems that are already extracted or installed the normal way (eg., Bliss OS). I checked to see which version of grub was installed in synaptic manager and saw both grub-pc and grub EFI listed as installed. Is this normal? I tried to troubleshoot the issue myself but with my limited knowledge, I wasn't getting anywhere :sad: I am perplexed at the moment. Is this a bug associated with 19.10 or am I doing something wrong? Any kind of help is appreciated. Thanks.
My 40_custom file:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Kali Linux - Live"{
    insmod linux
       set isofile="/Boot/Distros/kali-linux-64.iso"
       set bootoptions="findiso=$isofile boot=live username=root hostname=kali"
       loopback loop (hd1,gpt4)$isofile
      linux (loop)/live/vmlinuz $bootoptions
       initrd (loop)/live/initrd.img
}

menuentry "Tails"{
    insmod linux
        set isofile="/Boot/Distros/tails-amd64.iso"
        search --no-floppy -f --set=root $isofile
        loopback loop (hd1,gpt4)$isofile
        linux (loop)/live/vmlinuz boot=live iso-scan/filename=${isofile} findiso=${isofile} apparmor=1 nopersistence noprompt timezone=Etc/UTC block.events_dfl_poll_msecs=1000 splash noautologin module=Tails slab_nomerge slub_debug=FZP mce=0 vsyscall=none page_poison=1 union=aufs  quiet
        initrd (loop)/live/initrd.img
}

menuentry "Bliss OS" {
    insmod part_gpt
    set root='(hd1,gpt6)'
    linux /AndroidOS/kernel root=/dev/ram0 androidboot.selinux=permissive buildvariant=userdebug SRC=/AndroidOS
     initrd /AndroidOS/initrd.img
}

menuentry "SystemRescueCd" {
        load_video
        insmod gzio
        insmod part_gpt
        insmod part_msdos
        insmod ext2
        search --no-floppy --label boot --set=root
        loopback loop (hd1,gpt4)/Boot/Tools/systemrescuecd-6-0-3.iso
        echo   'Loading kernel ...'
        linux  (loop)/sysresccd/boot/x86_64/vmlinuz img_label=boot img_loop=(hd1,gpt4)/Boot/Tools/systemrescuecd-6-0-3.iso archisobasedir=sysresccd copytoram setkmap=us
        echo   'Loading initramfs ...'
        initrd (loop)/sysresccd/boot/x86_64/sysresccd.img
}


```

---

### Post by oldfred on 2019-11-01
Grub2 with 19.10 and later has changed from 2.02 to 2.04.
[https://launchpad.net/ubuntu/+source/grub2](https://launchpad.net/ubuntu/+source/grub2)

So putting 00_header files back may be the issue. Some change in the script.
I would expect 40_custom & themes to work, but have not tested myself.

---

### Post by damndaniel on 2019-11-01
Thanks for the input oldfred, but unfortunately, that didn't solve the problem. I tried replacing the 00_header file with the one from the latest grub 2.04 binary but it didn't help. The issue persists. Heck, I even tried reinstalling the system to no effect. I think I should also mention about the recent issue I've been facing with the boot process getting stuck at the oem logo (the bios post screen, before getting the grub menu). Could that be affecting the grub booting process by any chance? I tried resetting the bios, but I don't think it improved anything. Right now, my only options are to downgrade grub or to switch back to 18 LTS release. Or, is there any other way around this scenario?

---

### Post by oldfred on 2019-11-01
If getting stuck at UEFI/BIOS that is a separate issue.

But have seen others with grub issues.
I always keep the latest LTS version as my main working install.
My newer test installs boot with that grub currently, or I use a configfile to load the grub menu from a newer test install. but have not regularly booted them.

If you do not need the very newest 9 month version of Ubuntu because you have very new hardware, better to stay with latest LTS version.

---

### Post by damndaniel on 2019-11-02
Those are some wise words, oldfred. I'll keep it in mind for the next time I decide to try out a new release. For the time being, I have decided to go back to 18 LTS which has solved the problem; which makes grub 2.04 the clear culprit. Just a little bit of clarification needed regarding booting into older grub config file. Does this simply involve chainloading the LTS grub config through a 40_custom edit or are there any additional steps involved. BTW, this thread can be marked as solved. Thanks for the help!

---

### Post by oldfred on 2019-11-03
Grub will automatically find another install & add boot entry. Issue is that when that install updates, you have to also update main working install.

If you use configfile to boot into other install's grub, then you do not have to make changes.
With Ubuntu, it also creates links to the most current kernel & you can create boot entries to boot the links. So those do not have to change.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile & use of labels of partition to boot.
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by damndaniel on 2019-11-03
Thank you. I'll check out those links. It's a relief because I do use a separate config file to boot into other grub(s). I am still trying to understand the basics when it comes to linux systems. So, thanks for your patience and help towards this newbie. May you have a fine day!

---

### Post by oldfred on 2019-11-04
Opened bug report.
If you like add to it as the more that report, the more likely someone will look at it.

2.04 Out of memory error
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311)

Installed 2.04 to flash drive and got out of memory error on loopmount.
Installed 2.02 to same flash drive and same boot stanza booted without issue.

---

