---
title: "Can I boot Super GRUB Disk from ISO ?"
date: 2013-04-14
forum: General Help
---

### Post by GameX2 on 2013-04-14
[COLOR=#FFFFFF ! important][FONT=arial]**2**[/FONT][/COLOR]Hi,


I want to try something; to speed up my Ubuntu boot time, I've turned off the GRUB menu, so that it would only display if I hold SHIFT during boot.
What's too bad is that doing this make it impossible to boot into Windows.  It's apparently incompatible with OS_Prober.

Is there a workaround ?

I've thought about something.  I know about the Super GRUB 2 Disk, which is basically a ISO that you can burn to a CD-ROM, and allow to choose GRUB entries from the CD (I use it to boot in Ubuntu when GRUB is wiped from the hard drive).
[http://www.supergrubdisk.org/super-grub2-disk/[COLOR=#FFFFFF ! important][FONT=arial]**374**[/FONT][/COLOR]]("http://www.supergrubdisk.org/super-grub2-disk/")

I also know that you can boot a few ISOs from the GRUB menu.  I've done it with GParted.  Now, what I would like to do, is be able to boot this ISO from the GRUB menu.  That way, I should be able to boot in Windows 7 using this ISO.

I've tried editing the GParted booting file from /etc/grub.d/40_custom:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

 menuentry 'Super GRUB 2 ISO' {

set isofile="/boot/iso/GRUB.iso"

set root=(hd0,5)

loopback loop (hd0,5)$isofile

linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile

initrd (loop)/live/initrd.img

}
```

But I'm getting an error "You need to load the kernel first".  The error that show up, when the iso's no found.  Can I even boot it from GRUB ?  Is it supported?  It's weird, since I'm simply booting GRUB.. from GRUB (As useless as it may seem, yes) !

How could I do this?

Thanks!

---

### Post by oldfred on 2013-04-15
This worked for me with the version I have:

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

menuentry "" {
set root= 
}

# locate memdisk
menuentry "super_grub2_disk_hybrid_2.00 " {
    insmod part_gpt
    insmod memdisk
#    set isofile="/iso/super_grub2_disk_hybrid_2.00s1-beta1.iso"
#    loopback loop (hd2,4)$isofile
#    linux (loop)/live/vmlinuz2 boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
   linux16 /usr/lib/syslinux/memdisk iso bigraw
#    linux (loop)/live/vmlinuz2 boot=live config
#    initrd (loop)/live/initrd2.img
#   initrd16 (hd2,4)/iso/super_grub_disk_hybrid-1.98s1.iso
   initrd16 (hd2,4)/iso/super_grub2_disk_hybrid_2.00s1-beta1.iso
}
```

With all the # or comments, it must have taken me a while to get it to work
I changed to just having one entry in 40_custom that boots a config file (livecdimage.cfg) in the same partition as all my ISOs. The I do not have to run sudo update-grub on every edit to my ISO files.
My files are in a gpt partitioned drive so I have to add that insmod.

---

### Post by GameX2 on 2013-04-15
Thanks!

I've just read there are also ways to hide the GRUB menu, and also display the Windows entries when pressing SHIFT, using custom scripts.  That would be more efficient.

I've tried a few times, and haven't managed to hide the GRUB menu and preserve the Windows entries.  I'm confident, pretty sure I'll manage to get it to work.
Any working method (Apologies, this question was probably asked multiple times)?

I'll try this method right now.

Thank you very much.

---

### Post by oldfred on 2013-04-15
I do not do exactly what I think you want but used to just copy my Windows XP entry into 40_custom and turn off os-prober. I still do that because I have a lot of old test installs that I have not yet deleted and let the scripts find my current install's kernels & 40_custom entries.

       From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

I did experiment with creating a Windows 7 repair flash drive directly from Ubuntu. While some said they have, I could not. So I created CD and used CD to write a FAT32 flash drive. But it has so much room, I decided to install grub into the same Windows partition and boot the repair install of Windows and then boot Linux repair ISO. A standard Windows grub entry to chain to the same partition's boot sector where my grub and Windows was in worked. The only thing I has to be real careful of was two /Boots. FAT32/Windows does not care about case, but and Windows already has a /Boot for its BCD. So I made(copied?) the grub /boot into /Boot.

---

### Post by GameX2 on 2013-04-15
> **oldfred said:**
> I do not do exactly what I think you want but used to just copy my Windows XP entry into 40_custom and turn off os-prober. I still do that because I have a lot of old test installs that I have not yet deleted and let the scripts find my current install's kernels & 40_custom entries.

       From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

I did experiment with creating a Windows 7 repair flash drive directly from Ubuntu. While some said they have, I could not. So I created CD and used CD to write a FAT32 flash drive. But it has so much room, I decided to install grub into the same Windows partition and boot the repair install of Windows and then boot Linux repair ISO. A standard Windows grub entry to chain to the same partition's boot sector where my grub and Windows was in worked. The only thing I has to be real careful of was two /Boots. FAT32/Windows does not care about case, but and Windows already has a /Boot for its BCD. So I made(copied?) the grub /boot into /Boot.

Thanks for the reply.

I want to do something common - since I use Windows 7 rarely, I want to hide GRUB and automatically boot Ubuntu.  I would like GRUB to display only when I hold the SHIFT key, and when GRUB will be displayed, I would appreciate to be able to boot into Windows 7 that way.  I've read some users wondering about how to do this, on the forums.  This require tweaking a few GRUB files - do you have any suggestion?

I originally thought about starting the GRUB ISO from the menu, since I believed that booting Windows from a hidden GRUB menu was incompatible/impossible.  I was wrong!
By the way, your method to boot the GRUB ISO is working!  Great! :)

---

### Post by oldfred on 2013-04-15
I know the offical way is the grub timeout. But some that have used 0 then can never get into the menu as there is not enough time. So 1 may be possible?

info -f grub -n 'Simple configuration'

       Discussion of timeouts issue & recordfail:
[http://ubuntuforums.org/showthread.php?t=1717700](http://ubuntuforums.org/showthread.php?t=1717700)

---

