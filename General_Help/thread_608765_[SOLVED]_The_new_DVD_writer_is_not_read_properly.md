---
title: "[SOLVED] The new DVD writer is not read properly"
date: 2007-11-10
forum: General Help
---

### Post by PmDematagoda on 2007-11-10
I just bought a new DVD writer, a Samsung Write-Master. Now I first put a CD to test it, but even after I eject the CD, the CD is still mounted in /media/cdrom1, and when I try and unmount it manually, it tells me:-
```
[mntent]: line 2 in /etc/mtab is bad
[mntent]: line 4 in /etc/mtab is bad
[mntent]: line 5 in /etc/mtab is bad
[mntent]: line 6 in /etc/mtab is bad
[mntent]: line 8 in /etc/mtab is bad; rest of file ignored
[mntent]: line 2 in /etc/mtab is bad
[mntent]: line 4 in /etc/mtab is bad
[mntent]: line 5 in /etc/mtab is bad
[mntent]: line 6 in /etc/mtab is bad
[mntent]: line 8 in /etc/mtab is bad; rest of file ignored
umount: /media/WXPVOL_EN: not found

```

I had a look at mtab and here it is:-
```
Release Date: 19 April 2007 0
Build Date: 29 September 2007 0
```

Personally I'm confused:confused:, could anyone please tell me what can be done to fix this issue?

---

### Post by JOe! on 2007-11-11
I also have been having a similar problem ever since I moved to gutsy (Kubuntu).

I haven't tried CDs, but after I insert a blank DVD the first time it pops up with the media launcher (what do you want to do with this blank media? etc.). But after I eject the disc the system will not recognize and new media inserted into the drive, I have to restart the system to have it recognize a new disc. Nor can I unmount the drive and remount it.

If I try to unmount I get:
```
umount: /dev/hdc: not mounted
```

If I try to mount the drive I get:
```
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Also, the little disc icon stays in the media tray on my kubuntu menu after the first disc is inserted and will not dissapear until a restart.

Any suggestions?

---

### Post by Ubukanuba on 2007-11-24
I am getting the same problem HELP!

---

