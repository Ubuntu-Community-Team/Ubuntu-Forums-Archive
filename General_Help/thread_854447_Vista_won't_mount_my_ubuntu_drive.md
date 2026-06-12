---
title: "Vista won't mount my ubuntu drive"
date: 2008-07-09
forum: General Help
---

### Post by VitaminH on 2008-07-09
Hello there,

I'm currently running a dual boot machine with 2 hard drives installed, my 500GB one with Ubuntu, and an older 150 I had in a now defunct machine that I put in and installed Vista on.  The Vista drive mounts in Ubuntu with no issues whatsoever (as does my external firewire/usb 2.0) drive that i formatted FAT32 that Vista also won't touch...), however neither drive will mount in vista.  The problem with the external seems to be the formatting, I formatted FAT32 on my MacBook Pro from OS X and I've read on the Vista forums that Vista doesn't always like that.  

However, I can find no reason why it doesn't want to mount the internal ubuntu drive.  The drive shows up in both the Device Manager and the Disk Manager, but it is not assigned a Drive letter, and the option to do so is grayed out, with the only available option being "Delete..."  Which I'm obviously not going to do.  Has anyone else had issues with this or am i Just overlooking something extremely simple.  Thanks in advance.

---

### Post by inteluser on 2008-07-09
What file system is the ubuntu drive using?  Vista does not have native support for most linux filesystems (like ext*, reiserfs, xfs, etc.).

There are a number of third party programs you can download to add support to linux file systems to windows, although I haven't tried any of them.

---

### Post by YaroMan86 on 2008-07-09
Windows, unlike Linux, only supports its own file systems natively. It can maybe see an "unknown" partition in its editor, but it assumes its unallocated.

There's a handy dandy tool called the ext2 IFS Driver for Windows which supports ext2/ext3 very well and allows Windows to access those types of partitions as if they were regular windows partitions.

You can get it [here.]("http://www.fs-driver.org/")

Remember that Windows likes to think its the only ticket in town and will frequently ignore anything non-Windows when installed. Overwriting a Linux MBR in favor of Windows, acting like Linux partitions are merely unallocated space, etc.

---

### Post by VitaminH on 2008-07-09
> **inteluser said:**
> What file system is the ubuntu drive using?  Vista does not have native support for most linux filesystems (like ext*, reiserfs, xfs, etc.).

There are a number of third party programs you can download to add support to linux file systems to windows, although I haven't tried any of them.

Ahhhh suddenly it makes sense.  I'm sure Ubuntu is ext3 (which is the default I believe?)  I had in my head the default was FAT32 for some dumb reason.  Well don't I feel silly!  I found a HOWTO for mounting EXT3 on vista now knowing better what to search for right [here.]("http://ubuntuforums.org/archive/index.oho/t-358241.html") I'll give this a shot.  Thanks!

Edit:  Whoops someone else posted the link for me already!  Thanks to everyone.

---

