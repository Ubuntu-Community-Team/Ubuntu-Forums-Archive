---
title: "HDD Issues and Cannot Download Boot-Repair to Restore Bootability"
date: 2015-06-27
forum: General Help
---

### Post by oldefoxx on 2015-06-27
I have a My\ Passport external 1T drive that was formatted NTFS.  I could not find any Linux tool that would deal with this at all.  I attached it to my wife's laptop with Win7  and used chkdsk.exe on it from the run/cmd line.  Windows no longer supportsdfoing this from the GUI.  Chkdsk.exe took hours, and finally reported there were not enough clusters left for it to do it;s job.  But it did give me access to my folders and files.  So I reformatted my new laptop to wipe out Windows 8.1, which I found worthless, far less capable than Win7, and had Ubuntu install in it's place.  Made a bad mistake there, as I let the installer coerce me into using LV as my format type.  Now I have all that to do over as well.  But first to get the data off the usb dfive so that I can reformat it.  That took hours, but finally got done.

Tried to use gparted to reformat the usb drive.  It failed miserably.  Said it did it, but drive had a bad superblock now, and none of the Linux tools available would do anything to fix it.  Made the drive look worthless, and yet I knew better.  As a last recourse, I decided to use the LiveCD and try to just install Ubuntu 14.04 to it.  That worked.  Whatever the LiveCD uses for a disk formatter, it is the best thing going.  Except for that damn LV option.  I will know better than ever do that again.

Trouble is, the install to a usb drive replaced my grub boot selection on sda1 with its own version which features the usb drive as the primary boot device.  If the usb drive is not connected, my laptop will no longer boot up.  I need boot-repair or something to let me first boot to sda1 (via the usb drivr being attached), then detatch the usb drive so that it is not included at all in the grub settings on sda1.  But that won't work with LiveCD, since it is the agency that did the whole grub thing as the last part of it's install to that very drive.  The usb drive has to be attached to complete the install, but the installer is making changes to sda1, instead of just putting it all on the udsb drive.  If the drive is attached, and my boot order is configured to put usb before hdd, let it use the grub settings stored there.  If it is not attached, or comes after the hdd in the boot order settings, let the grun on my first bootable hdd take over.  

Anyway, my problems to deal with are:  (1) the fiolder/file recovery from the NTSF drive was so crossed threaded that I have multiple restores of the same files in several folders, so I've got to single and sort that all out.  (2)  Get the results copied back to the usb drive so that I can reinstall Ubuntu on the same partition (without LV this time).  (3)   Copy the stored files on the usb drive back to the newly installed Ubuntu on my hdd partition.  That's going to take time. But I guess it will all be worth it.  Oh, and if I get snother usb drive, I will immediately reformat it to Ext4 in place of NTFS.  Aside from chkdsk.exe, MS offers nothing that brings a screwed up file system back to life.

But the thing that irks me most right now, is ***_That I can't Get Boot-Repair to Install off the Internet.  _***  Don;t ask me why, but apt-get can't find it, although I;ve checked every link on the subject and they all say the the same thing.  (1)  sudo in a deb reference, (2) sudo apt-get update, (3) sudo apt-get install of boot-repair, , and (4) execute boot-repair.  apt-get says it can't find boot-repair, and there things die.  Seems like maybe boot-repair should be made part of the family of modules residing on the LiveCD, because you can be dead in the water without it.  Without this little usb drive being attached, this laptop is about like burnt toast.

Can somebody tell me how ro get boot-repair, or what I have to do to get Grub2 to bring my boot options back to the sda1 partition?  I like boot-repair, because it did not clutter up my boot menu with a bunch of expired images.  It kept the choices down and limited to the latest installs.

---

### Post by oldefoxx on 2015-06-27
I'm still trying to come up with an alternative to roob-repair.  I followed this link on google:
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

and got this result:```
$ sudo grub-install –boot-directory=/mnt/boot /dev/sda
grub-install: error: More than one install device?
```

I tried umount and removing the usb drive, but keep getting the dsmr results.  Another dead end.

Finally, some progress.  I next went to the following link:
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

And followed these steps:
> Reinstalling GRUB 2 from a Working System
If Ubuntu is operating normally, boot into the working installation and run the following command from a terminal. 

X is the drive (letter) on which you want GRUB to write the boot information. Normally users should not include a partition number, which would produce an error message as the command would attempt to write the information to a partition. 

**_sudo grub-install /dev/sdX_**  # Example: sudo grub-install /dev/sda
This will rewrite the MBR information to point to the current installation and rewrite some GRUB 2 files (which are already working). Since it isn't done during execution of the previous command, running**_ sudo update-grub _**after the install will ensure GRUB 2's menu is up-to-date.


With this result:
```
~$ sudo grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
oldefoxx@Don-L355:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sda1
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sda3
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sdb1

```

Two downside to this:

 (1)  The usb hdd was currently plugged in, so got picked up in the process.  But it that proves to be a problem, I can deal with it later.  Main thing is to get sda1 bootable again.

(2)  It also picked up all the old imsge files I still have on my hard drive.  That can be good though, because I've had current images corrupt on me, and have gone back to earlier images to find a working one.  Beats a complete reinstall and having to reinstall all the programs and features that you put in there.  Just ought to be an easy way to limit yourself to a few old images, not a bunch.

---

