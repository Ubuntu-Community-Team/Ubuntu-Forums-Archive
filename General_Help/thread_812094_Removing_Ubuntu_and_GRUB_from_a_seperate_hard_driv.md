---
title: "Removing Ubuntu and GRUB from a seperate hard drive"
date: 2008-05-29
forum: General Help
---

### Post by cuulcars on 2008-05-29
How do you remove Ubuntu and GRUB? I've read a few help topics, but they all specify directions on how to remove it by deleting partitions. I have a master drive that contains windows, and a slave drive that contains Linux as well as GRUB. Obviously, it boots from the slave drive. I considered just formatting the slave drive, but then I probably wouldn't be able to boot Windows, due to GRUB not existing anymore. So, how would I go about removing Linux and GRUB and make it boot Windows again? Note that I don't have the Windows Installation/Recovery disk anymore. I don't know if I could go to Microsoft and request for one, but I thought it probably cost me and arm and a leg so I was wondering if there were any alternatives.

---

### Post by wdaniels on 2008-05-29
I haven't used Windows for a while, but you always used to be able to just do "fdisk /mbr" from DOS to restore the master boot record. Otherwise, you could always just install grub on the master drive and use it only for booting Windows ([you don't necessarily need Linux to use grub]("https://sourceforge.net/projects/grub4dos"), and there are plenty of other bootloaders around that can boot Windows if you prefer).

---

### Post by logos34 on 2008-05-29
So, hightailing it back to Windoze?  Enjoy your masochism:)

just kidding

> **wdaniels said:**
> you always used to be able to just do "fdisk /mbr" from DOS to restore the master boot record.

That's one way.  Try the windows 98 SE OEM floppy [here]("http://www.bootdisk.com/bootdisk.htm").

Or get the **Super Grub Disk**.

oh, and this will erase grub from the mbr of the slave drive:

[B]dd if=/dev/zero of=/dev/hdb bs=446 count=1
[/B]
(or /dev/hdd)

Use gparted on the live cd to delete partitions/format the drive

---

### Post by meierfra. on 2008-05-29
```
oh, and this will erase grub from the mbr of the slave drive:

dd if=/dev/zero of=/dev/hdb bs=446 count=1

(or /dev/hdd)
```

Two comments:

1) There are only very rare circumstances where this command will achieve anything. You need to replace Grub by a different boot loader, which in the process will automatically erase Grub. There is no reason to  manually erase Grub.

2)  "dd" can be very  dangerous. For example if you accidentally leave out the "count=1" the above command, it  will erase your whole hard drive.

logos34, I'm really surprised that you  presented this command without any further comment.

---

### Post by ibuclaw on 2008-05-29
There is a safer way to do it.
```

sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```
This technique is mainly used for making USB-sticks bootable, but it works very well on normal harddrives too! [(I found out that the hard-way)]("http://ubuntuforums.org/showthread.php?t=799895")

This basically overwrites GRUB with an MBR that just boots off the harddrive it's currently on. No menu, no questions asked!

Great if your Windows install is on the same disk as the Primary hard-drive.
Not so good if it isn't (But you can switch the settings in BIOS to fix this).

Regards
Iain

---

### Post by logos34 on 2008-05-29
> **meierfra. said:**
> [CODE]1) There are only very rare circumstances where this command will achieve anything. You need to replace Grub by a different boot loader, which in the process will automatically erase Grub. There is no reason to  manually erase Grub.

2)  "dd" can be very  dangerous. For example if you accidentally leave out the "count=1" the above command, it  will erase your whole hard drive.

logos34, I'm really surprised that you  presented this command without any further comment.

I guess I've got too many threads swirling around in my head...I added that as an afterthought, but after rereading cuulcars original post it's clear grub is only on the mbr of the master (windows) drive.  I started thinking it was on the slave mbr (?). Jeez, short-term memory loss wasn't supposed to kick in until my geezer years...

But let's say it was on the mbr of a slave disk that's going to be wiped and maybe turned into a (non-bootable) data drive: I don't see any particular reason why not to erase the mbr too...There's a grub 'uninstall' option in SGD for precisely that.  The dd command is not the only one you can accidentally truncate and end up in real trouble.

But I probably should at least have added a 'be careful' as I usually do when I recommmend Testdisk--a really great tool that is also a little scary because if you get sloppy and write the wrong changes to disk that's it, boom, gone, as I found out once.

---

