---
title: "Adding a new distro to Ubuntus GRUB menu"
date: 2008-04-15
forum: General Help
---

### Post by insubstantial on 2008-04-15
Hi everyone, so i installed Ubuntu, and then Fedora after it, now the research i did says not to install the bootlooader of the second distro or it'll use its own as the defaul loader (correct me if im wrong)...........so i'n order for me to see Fedora in Ubuntus GRUB menu, i'll have to edit the GRUB menu and point it where Fedora is installed....thats where my problem comes in, I don't know the location of it, is there a way i can look for it ?

---

### Post by bodhi.zazen on 2008-04-15
LOL

Well grub identifies partitions differently then linux, see this link :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

To list your partitions : ```
sudo fdisk -l
```

Not the question, how did you install Fedora ? If you used the defaults it created a LVM partition (for root) any a /boot partition. In that case I advise you install grub to your ubuntu partition and chaniload from the fedora /boot partition.

See this link :   [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by insubstantial on 2008-04-15
Thanks, however i'm still slightly confused, heres what i got for the partition info.

```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22dd22dd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd87bff1c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         729     5855661   83  Linux
/dev/hdb2             730         972     1951897+   5  Extended
/dev/hdb3   *         973        1737     6144862+  83  Linux
/dev/hdb4            1738        1992     2048287+  82  Linux swap / Solaris
/dev/hdb5             730         972     1951866   82  Linux swap / Solaris

```

---

### Post by bodhi.zazen on 2008-04-16
Well, from what you listed I do not see a /boot partition.

But we need to know which partition is Ubuntu and which is Fedora.

---

### Post by insubstantial on 2008-04-16
Ubuntu would be on /dev/hdb1
Fadora on /dev/hdb3

you said you don't see a boot partition, when i installed i only used */* assuming /boot and the rest would be installed there, was that incorrect to do?

One more question, is it possible to install Ubuntu to a computer from an external harddrive ? see i have the installtion iso's on an external harddrive, now i was wondering if i booted up a system with a live cd, can i then navigate to the external drive, and mount the installation iso from there ? would that work ?

---

### Post by bodhi.zazen on 2008-04-18
Well, the problem is Fedora does not automatically add other distros to the grub menu.

You can either manually add the Ubuntu stanzas or use chainloader. 

To manually add Ubuntu to Fedora, boot Fedora and mount the Ubutnu partition at /media/ubuntu:

```
su - 
```
To become root in Fedora

Then ```
mkdir /media/ubuntu
mount /dev/hdb1 /media/ubuntu
```

Now, I do not know if Fedora will let you launch graphical applications as root, or you may need to log in as root to do so ???

At any rate, using any editor, as root, add the Ubuntu stnazas from /media/ubuntu/boot/grub/menu.lst to /boot/grub/menu.lst (Fedora menu).

If you know how you can use nano (with two root termainals) and copy -> paste ...

If you do this you will need to manually update the kernel and initrd lines in the Ubuntu stanza each time you upgrade your Ubuntu kernel.

===========

Alternate is to use chainloader. This is a little easeir as it automates the whole process. Boot a live CD, use grub to install grub to your ubuntu partition.

The in fedora add

Title Ubuntu
root (hd1,0)
chainloader +1

See this link for details :  [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

===========

I think you are asking how to install Ubuntu from an iso rather then booting a burned CD ?

first you can mount an external hard drive from the live CD

second you can install from an iso :

Install : [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

	[indent]There is a section on no CD ...[/indent]

Install without a CD:

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

[http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive](http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive)

[http://ubuntuforums.org/showthread.php?&t=316093](http://ubuntuforums.org/showthread.php?&t=316093)

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

---

