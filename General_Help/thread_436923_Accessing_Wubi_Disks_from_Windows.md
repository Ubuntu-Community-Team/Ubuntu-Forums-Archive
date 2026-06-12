---
title: "Accessing Wubi Disks from Windows"
date: 2007-05-08
forum: General Help
---

### Post by jettplane on 2007-05-08
I thought I'd post a how to on accessing Wubi disks from the Windows installation.

First, install Ext2 Files System Driver, an open source Ext2 driver by Matt Wu at [http://www.ext2fsd.com](http://www.ext2fsd.com). You need this to let Windows be able to read Ext2 file systems. 

Next, install FileDisk, a virtual disk driver under GNU license.  The home page of FileDisk is [http://www.acc.umu.se/~;](http://www.acc.umu.se/~;) the download link is [http://www.acc.umu.se/~bosse/filedisk.zip](http://www.acc.umu.se/~bosse/filedisk.zip).  Instructions for use of FileDisk are in the archive-it is just a system file that adds a command line program called filedisk.

Create a batch file to mount your disks.  Here is what mine looks like in lindisks.bat:

filedisk /mount 0 c:\wubi\disks\system.virtual.disk l:
filedisk /mount 1 c:\wubi\disks\home.virtual.disk y:
filedisk /mount 2 c:\wubi\disks\swap.virtual.disk x:

You can add the .bat file to your start up if you want access when ever you start up.  You should now be able to use these drive mappings to look at any of your linux files.  I have not had any problems reading files so far, but some files do not copy back and forth between Windows and the disks.  You get an error message when this happens.  The files you are most likely to use, such as documents, work very well.

---

### Post by tuxcantfly on 2007-05-08
or you could simply use explore2fs...

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

just select "open file" when prompted, and drag-and-drop your files over

note that explore2fs is read-only, though, so you'll want to use the above method if you need read-write

---

### Post by tuxcantfly on 2007-05-08
or, you might also want to check out virtual volumes, supposedly has read-write support for disk images, though I haven't ever tried it...

[http://www.chrysocome.net/virtualvolumes](http://www.chrysocome.net/virtualvolumes)

---

### Post by itsjareds on 2008-07-11
FileDisk link is broken; here is the new link: [Download FileDisk]("http://www.acc.umu.se/~bosse/filedisk-14.zip")

---

### Post by naelphin on 2008-07-15
Thanks for the link to the explore2fs-1.08beta9 it helps and does't require installing a driver.

Thanks again.

---

### Post by nwubie on 2008-07-16
Thanks a lot for that jettplane ! I just messed with some setting that wouldn't allow Ubuntu to boot even in recovery mode and your solution allowed me to restore the backup files.

And thanks to itsjareds for the updated link to Filedisk.

I used Stephan Schreiber's [Ext2 Installable File System For Windows](http://www.fs-driver.org/) instead of Matt Wu's driver.

[Virtual Volumes (version 0.5)](http://www.chrysocome.net/virtualvolumes) didn't work. It installed properly but I got an error when running the program and it wouldn't let me browse for an image file.

[explore2fs](http://www.chrysocome.net/explore2fs) works great if you only want to get some file out of the wubi installation. I like it that it's a standalone .exe file : no installation and no leftovers.

---

### Post by SheridanZhoy on 2009-08-05
I haven't been able to access my Wubi files from either ext2 IFS or explore 2fs...
I'm not sure what file I'm looking for under C:\ubuntu\disks . The files there are root.disk and swap.disk. There are also two folders called "boot" and "shared".

Explore 2fs says it's looking for a .ext2 or a .img file and ext2 IFS doesn't let you point it to a file, as far as I can tell, so I don't know what to do.

---

### Post by itsjareds on 2009-09-16
Root.disk should be what you're looking for (though I can't say for sure.. I'm not using Wubi).

---

### Post by Agg23 on 2009-10-14
It is root.disk that you need, but on my computer explore2fs won't work. :mad:

---

### Post by JasonSilver on 2010-07-02
> **Agg23 said:**
> It is root.disk that you need, but on my computer explore2fs won't work. :mad:
Same here-- anyone explain why it wouldn't work for me?

---

### Post by JasonSilver on 2010-07-02
OK, for people who can't get anything else to work, there are instructions on the Wubi Guide which worked for me:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> How can I access my Wubi install and repair my install if it won't boot?
Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:


sudo mkdir /win
sudo mount /dev/sda1 /win
Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein


sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

To check the filesystem you can use:


sudo fsck /win/ubuntu/disks/root.disk

---

### Post by jucedogi on 2012-02-11
> **JasonSilver said:**
> Same here-- anyone explain why it wouldn't work for me?

Been a while since anyone wrote here but I'll post this info here so that anyone else looking for this knows how to access their info.

Basically the program on the links posted previously does not seem to have ext4 support.

The following does :: [http://sourceforge.net/projects/ext2read/files/](http://sourceforge.net/projects/ext2read/files/)

Worked great for me with a wubi install of Ubuntu 11.10

Homepage is :: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

Hope this helps someone ¬¬

---

