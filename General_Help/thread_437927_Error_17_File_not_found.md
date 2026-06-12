---
title: "Error 17: File not found"
date: 2007-05-09
forum: General Help
---

### Post by digeratiX on 2007-05-09
Booting "Ubuntu"
find --set-root /wubi/boot/grub/menu.lst
Error 17: File not found
Press any key to continue...

Whats the fix for this?

Downloaded the wubi installer, the only one available on the site, beta, installed, rebooted, was exited, then disappointed.

---

### Post by ago on 2007-05-09
[https://wiki.ubuntu.com/WubiGuide#head-7e1711f45843d41aff1ec27f06cdf8aca70cb88c](https://wiki.ubuntu.com/WubiGuide#head-7e1711f45843d41aff1ec27f06cdf8aca70cb88c)

---

### Post by digeratiX on 2007-05-09
Well this is what I got.

C:\>contig -s -a c:\wubi

Contig v1.54 - Makes files contiguous
Copyright (C) 1998-2007 Mark Russinovich
Sysinternals - [www.sysinternals.com](www.sysinternals.com)

c:\wubi\boot is defragmented
c:\wubi\disks is defragmented
c:\wubi\docs is defragmented
c:\wubi\install is defragmented
c:\wubi\license.txt is defragmented
c:\wubi\tools is defragmented
c:\wubi\Uninstall.exe is defragmented
c:\wubi\WUBI-README.txt is defragmented
c:\wubi\boot\grub is defragmented
c:\wubi\boot\initrd is in 27 fragments
c:\wubi\boot\linux is in 9 fragments
c:\wubi\boot\winboot is defragmented
c:\wubi\boot\grub\bzr_log.xLZJ4z~ is defragmented
c:\wubi\boot\grub\menu.lst is defragmented
c:\wubi\boot\winboot\grldr is in 2 fragments
c:\wubi\boot\winboot\grub.exe is in 3 fragments
c:\wubi\boot\winboot\menu.lst is defragmented
c:\wubi\disks\home.virtual.disk is in 112 fragments
c:\wubi\disks\swap.virtual.disk is in 36 fragments
c:\wubi\disks\system.virtual.disk is in 59 fragments
c:\wubi\install\install.virtual.disk is in 2 fragments
c:\wubi\install\preseed.cfg is in 3 fragments
c:\wubi\install\preseed.cfg.template is defragmented
c:\wubi\install\ubuntu-7.04-alternate-i386.iso is in 4270 fragments

Summary:
     Number of files processed   : 24
     Average fragmentation       : 189.042 frags/file

C:\>contig -s c:\wubi

Contig v1.54 - Makes files contiguous
Copyright (C) 1998-2007 Mark Russinovich
Sysinternals - [www.sysinternals.com](www.sysinternals.com)

Processing c:\wubi\disks\system.virtual.disk...c:\wubi\disks\system.virtual.disk is as contiguous as possible
.

Summary:
     Number of files processed   : 24
     Number of files defragmented: 9
     Average fragmentation before: 189.042 frags/file
     Average fragmentation after : 4.5 frags/file


I cant get it to defrag anymore, still get error 17 and no I dont use compression, may the iso gets messed up durring download, where is the iso link so I can download just that and try again.

---

### Post by ago on 2007-05-09
The 3 files that cannot be fragmented are:

c:\wubi\boot\initrd is in 27 fragments
c:\wubi\boot\linux is in 9 fragments
c:\wubi\boot\grub\menu.lst is defragmented

---

### Post by digeratiX on 2007-05-09
ok so you are saying as is reads here
[https://wiki.ubuntu.com/WubiGuide#head-7e1711f45843d41aff1ec27f06cdf8aca70cb88c](https://wiki.ubuntu.com/WubiGuide#head-7e1711f45843d41aff1ec27f06cdf8aca70cb88c)
"Defragment your drive. Make sure that wubi/boot/linux and wubi/boot/initrd are not fragmented."



But you are missing the point.
I guess I should have pasted the AFTER RESULTS

C:\>contig -s -a c:\wubi

Contig v1.54 - Makes files contiguous
Copyright (C) 1998-2007 Mark Russinovich
Sysinternals - [www.sysinternals.com](www.sysinternals.com)

c:\wubi\boot is defragmented
c:\wubi\disks is defragmented
c:\wubi\docs is defragmented
c:\wubi\install is defragmented
c:\wubi\license.txt is defragmented
c:\wubi\tools is defragmented
c:\wubi\Uninstall.exe is defragmented
c:\wubi\WUBI-README.txt is defragmented
c:\wubi\boot\grub is defragmented
c:\wubi\boot\initrd is defragmented
c:\wubi\boot\linux is defragmented
c:\wubi\boot\winboot is defragmented
c:\wubi\boot\grub\bzr_log.xLZJ4z~ is defragmented
c:\wubi\boot\grub\menu.lst is defragmented
c:\wubi\boot\winboot\grldr is defragmented
c:\wubi\boot\winboot\grub.exe is defragmented
c:\wubi\boot\winboot\menu.lst is defragmented
c:\wubi\disks\home.virtual.disk is in 8 fragments
c:\wubi\disks\swap.virtual.disk is in 10 fragments
c:\wubi\disks\system.virtual.disk is in 59 fragments
c:\wubi\install\install.virtual.disk is defragmented
c:\wubi\install\preseed.cfg is defragmented
c:\wubi\install\preseed.cfg.template is defragmented
c:\wubi\install\ubuntu-7.04-alternate-i386.iso is in 11 fragments

Summary:
     Number of files processed   : 24
     Average fragmentation       : 4.5 frags/file

C:\>contig -s c:\wubi

Contig v1.54 - Makes files contiguous
Copyright (C) 1998-2007 Mark Russinovich
Sysinternals - [www.sysinternals.com](www.sysinternals.com)

Processing c:\wubi\disks\home.virtual.disk...c:\wubi\disks\home.virtual.disk is as contiguous as possible.
Processing c:\wubi\disks\swap.virtual.disk...c:\wubi\disks\swap.virtual.disk is as contiguous as possible.
Processing c:\wubi\disks\system.virtual.disk...c:\wubi\disks\system.virtual.disk is as contiguous as possible
.
Processing c:\wubi\install\ubuntu-7.04-alternate-i386.iso...c:\wubi\install\ubuntu-7.04-alternate-i386.iso is
 as contiguous as possible.

Summary:
     Number of files processed   : 24
     Number of files defragmented: 0
     All files were either already defragmented or unable to be defragmented.


c:\wubi\boot\initrd is defragmented
c:\wubi\boot\linux is defragmented

So whats my course of action?

---

### Post by ago on 2007-05-09
[http://ubuntuforums.org/showthread.php?t=438037](http://ubuntuforums.org/showthread.php?t=438037)

---

### Post by digeratiX on 2007-05-10
Tried that and nothing worked, even more errors.

Looks like it needs a lot more work.

I will say this though, the UNINSTALL works perfectly... thank goodness.

---

### Post by miksr on 2007-05-10
Hi!

I've got the same Error 17 as other guys, so I went to GRUB's command prompt (pressing 'c' while in GRUB's menu) and tried to manually do find. I've typed "find /" and did hit <tab> to get Grubs auto-complete to show me list of available folders. wubi was one of options. But then, when I've had "find /wubi/" and did hit <tab> and it immediately completed to /wubi/boot and was not offering other folders. And when I've continued with "find /wubi/boot/" and <tab> it was coming back with file not found error or something among those lines.
So, what I make out of this is that GRUB somehow don't see all the folders. Maybe it has something to do with number of folders or something. Any ideas?

Regards, miks

---

### Post by ago on 2007-05-10
> **miksr said:**
> 
So, what I make out of this is that GRUB somehow don't see all the folders. Maybe it has something to do with number of folders or something. Any ideas?

Yep that is the issues we are facing. We are aware of that but short of ideas at the moment. On top of that the situation is not easily reproducible (Ecology has that too, but my laptop works perfectly fine).

Double check that the wubi folder is defragmented and uncompressed. To defragment use:

contig -v -s c:\wubi

If the error persist, then you will have to wait I am afraid.

---

### Post by tinybit on 2007-05-11
> find --set-root /wubi/boot/grub/menu.lst
> Error 17: File not found
> Press any key to continue...

It might show a bug in the NTFS filesystem driver(fsys_ntfs.c) for GRUB4DOS.

---

### Post by miksr on 2007-05-11
> **ago said:**
> 

If the error persist, then you will have to wait I am afraid.

Or the another solution would be to use only one level of folder hierarchy for wubi (e.g. wubi_install, wubi_boot, etc. instead of curret wubi/install and wubi/boot/grub

---

### Post by ago on 2007-05-11
> **miksr said:**
> Or the another solution would be to use only one level of folder hierarchy for wubi (e.g. wubi_install, wubi_boot, etc. instead of curret wubi/install and wubi/boot/grub

Yes, while we wait for a fix to the ntfs driver used by grub, we will move all content of the /wubi/boot folder up one level (inside c:\wubi), other folders are not relevant.  A build will be available tonight/tomorrow. Hopefully that will be enough.

---

