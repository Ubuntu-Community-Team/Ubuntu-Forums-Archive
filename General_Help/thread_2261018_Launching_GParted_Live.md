---
title: "Launching GParted Live"
date: 2015-01-15
forum: General Help
---

### Post by gordon99 on 2015-01-15
My laptop dual boots Xubuntu and Windows 7. I have been trying, without success, to get GParted Live to install from a USB flash drive. Having given up on that approach I have just tried to install the GParted Live by adding it into the start menu. However, when I switch on and select GParted Live, which is at the bottom of the start menu, all I see is a black screen with a stationary cursor at top left.
I had amended the 'grub.d/40_custom' file in accordance with a guide I have read. I then put the command 'sudo grub-mkconfig -o /boot/grub/grub.cfg' into terminal which was accepted. Can anyone with knowledge of this procedure explain what has gone wrong for me? I have added a copy of the amended 'grub.d/40_custom' file in case it is in making the amendment that I have erred. 

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'GParted Live' {
set isofile='/home/gordon/Documents/gparted-live-0.20.0-2-i486.iso'
loopback loop (hd0,5) $isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}
```

---

### Post by yancek on 2015-01-15
I thought I had an entry for this for GParted but I guess not.  Two possibilities, the first is you might try moving the gparted iso file to the root of the filesystem rather than in your Documents directory.  I've had problems booting iso files directly if they were not in the root although I'm not sure this is the problem.  Another possibility, you might extract the files from the iso and take a look at the syslinux.cfg or isolinux.cfg menu entry.  I have an entry for an extracted gparted which I copied to a gparted directory in the root of my filesystem which does boot.

> menuentry " GParted" {
search --set -f /gparted/live/vmlinuz
  linux /gparted/live/vmlinuz boot=live config union-aufs nowswap noprompt ip=frommedia live-media-path=/gparted/live bootfrom=/dev/sdb1 toram=filesystem.squashfs
  initrd /gparted/live/initrd.img
}   

The entry above has a lot more parameters which I don't think you need unless you try to extract and boot it so I wouldn't worry about that.  One thing I notice though is that your "union=aufs" has the equal sign while mine has a dash:  union-aufs.  Checking the syslinux.cfg or isolinux.cfg would verify if your parameters are correct.  Don't see anything else obvious.

---

### Post by C.S.Cameron on 2015-01-16
This is how MultiBootUsb does the Grub2 menuentry:

```
menuentry "GParted" {
        loopback loop /boot/iso/gparted-live-0.5.2-1.iso
        linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=/boot/iso/gparted-live-0.5.2-1.iso
        initrd (loop)/live/initrd.img
    }
```


This assumes that the gparted iso is in /boot/iso/ on the first partition

---

### Post by gordon99 on 2015-01-18
Thank you yancek and C.S.Cameron for your replies to my enquiry which I also posted on Linux Questions. For the record I succeeded in getting GParted Live onto the hard drive by adding the following to the 'grub.d/40_custom' file and saving same.
 
menuentry "GParted Live" {set isofile="/home/gordon/Downloads/gparted-live-0.20.0-2-i486.iso"
loopback loop $isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

You will see I had left the 'GParted iso.' in my Downloads file. Hence the line 'set isofile= xxxxxxxx' 
To update the grub configuration I used 'Sudo update-grub2'.
Hope this helps others who are using Xubuntu 14.04.

---

