---
title: "Ubuntu not booting - GRUB"
date: 2016-11-23
forum: General Help
---

### Post by ineedhelp4 on 2016-11-23
Hi All,

I have inherited a Ubuntu machine that is used to run RADIUS.
I am _extremely_ new to Linux so will explain the problem as best I can.

The machine is no longer booting.
There were some issues with the machine a few months back; a clonezilla image was then restored to the machine in the hopes this would fix the issue.
It did not and led to the machine starting with the grub-rescue> command.

I managed to get from here to the full GRUB 2 command Shell (grub>).

I cannot however get any further.

I have been trying to follow this guide:

[https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux)

However when getting to the second line of this part:[INDENT][FONT=courier new]grub> set root=(hd0,1)
grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1
grub> initrd /boot/initrd.img-3.13.0-29-generic
grub> boot
[/FONT][/INDENT]
[FONT=courier new][FONT=arial]I get stuck as my /boot does not appear to have VMlinuz and initrd files and the folder where these are does not have a /boot folder.

To explain everything I have done/ I have managed to find so far:
The machine has the following when the ls command is used:

(RADIUS-swap_1)
(RADIUS-root)
(hd0)
(hd0,msdos5)
(hd0,msdos1)

[FONT=courier new][FONT=arial]**(RADIUS-root) **[/FONT][/FONT][/FONT][/FONT]
[LIST]
[*]Contains a /boot folder with /grub and grub modules. 
[*][FONT=courier new][FONT=arial][FONT=courier new][FONT=arial]It also contains /usr/lib/grub/i386-pc.
[/FONT][/FONT][/FONT][/FONT] 
[*][FONT=courier new][FONT=arial][FONT=courier new][FONT=arial]It is listed as a ext4 filesystem.
[/FONT][/FONT][/FONT][/FONT] 
[*][FONT=courier new][FONT=arial][FONT=courier new][FONT=arial]It does not however contain any vmlinuz or initrd.img files.
[/FONT][/FONT][/FONT][/FONT] 
[/LIST]
[FONT=courier new][FONT=arial]**[FONT=courier new][FONT=arial](hd0,1)[/FONT][/FONT]**[/FONT][/FONT]

[LIST]
[*][FONT=courier new][FONT=arial]Contains vmlinuz and initrd.img files from 3.2.0-23 up to 3.2.0-45[/FONT][/FONT] 
[*][FONT=courier new][FONT=arial]Contains a grub/ folder with grub modules under /i386-pc/[/FONT][/FONT] 
[*][FONT=courier new][FONT=arial]Does not contain a /boot folder[/FONT][/FONT] 
[*][FONT=courier new][FONT=arial]Marked as boot on G-Parted through a live CD[/FONT][/FONT] 
[*][FONT=courier new][FONT=arial]ext2 filesystem[/FONT][/FONT] 
[/LIST]
[FONT=courier new][FONT=arial] I have run boot-repair-disk from a live usb and have the following info:[/FONT][/FONT]

[LIST]
[*]sets the OS to boot by default as: mapper/RADIUS-root (Ubuntu 12.04.1 LTS) 
[*][FONT=courier new][FONT=arial]And ticks the separate/boot partition, set as sda1[/FONT][/FONT] 
[*]The program runs under the recommended repair and fails giving the following: 
[/LIST]
[INDENT][I]"apt-error detected. Please open a terminal then type the following command:

sudo chroot "/mnt/boot-sav/mapper/RADIUS-rot" apt-get -f install

Then close this window"

[/I][/INDENT]
This then fails with:[INDENT][I]dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-115-generic_3.2.0-115.157_amd64.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-115-generic': No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-115-generic /boot/vmlinuz-3.2.0-115-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-115-generic /boot/vmlinuz-3.2.0-115-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-115-generic_3.2.0-115.157_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]
[/INDENT]

A pastebin from Boot repair is as follows:

[https://paste.ubuntu.com/23521991/](https://paste.ubuntu.com/23521991/)

Apologies for the wall of text; I thought a thorough explanation would be best.
Any help with this would be greatly appreciated as I have now reached a dead end.
  Please could you be as clear as possible in answers as as previously mentioned I am new to all of this.

p.s. Sorry if this is in the wrong sub-forum, please move if so.

A million thanks.

---

### Post by oldfred on 2016-11-23
You have the advanced LVM partitioning.
Also 12.04 will expire in April 2017, so best to start planning upgrade.

And this is your problem, full /boot, very common if not maintained by removing old kernels. But fixed in 16.04 to auto remove all but two most recent kernels. From line 1002 of your report:
```
/dev/sda1               ext2       228M  228M     0 [COLOR=#ff0000]100%[/COLOR] /mnt/boot-sav/sda1
```

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

I do not know LVM, but some links.
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by ineedhelp4 on 2016-11-24
Thanks oldfred.

Will I be able to clear the /boot partition with the commands from your first link using a live cd?

---

### Post by oldfred on 2016-11-24
Once it is full, I gather it can be difficult.
And you are only supposed to use dpkg to remove anything installed with dpkg or its database gets out of sync and you can have even bigger issues.

Sometimes, I think you have to violate the rules & rm one or two old files just to have enough room. Then once normally housecleaned, best then to actually do the reinstall of that file/kernel and use dpkg to correctly houseclean it out. Not sure if that really works or not.

I normally use synaptic which is a gui app. But with a server you have to use command line.

---

