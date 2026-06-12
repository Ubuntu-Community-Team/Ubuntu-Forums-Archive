---
title: "Partition gone read only"
date: 2018-12-17
forum: General Help
---

### Post by makem2 on 2018-12-17
I was experimenting with a WinToUSB install of windows 10 on a usb flash drive and when I returned to xubuntu I found a partition had 'gone' read only.

```

makem@ssdTOSH:/media$ ls -la
total 532
drwxr-xr-x   7 root root   4096 Aug  4 20:21 .
drwxr-xr-x  24 root root   4096 Dec 12 23:23 ..
drwxr-xr-x   2 root root   4096 Jun 16  2018 data
lrwxrwxrwx   1 root root     45 Aug  4 16:39 .directory -> /etc/kubuntu-default-settings/directory-media
lrwxrwxrwx   1 root root     42 Aug  4 16:39 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxr-x---+  2 root root   4096 Dec 17 21:57 makem
drwxrwxrwt   3 root root     60 Dec 17 22:50 ramdisk
drwxrwxrwx   3 root root   4096 Aug  5 13:56 testing
drwxrwxrwx   1 root root 524288 Dec 16 23:57 WinData
makem@ssdTOSH:/media$ cd WinData
makem@ssdTOSH:/media/WinData$ ls -la
total 1306200
drwxrwxrwx 1 root root    524288 Dec 16 23:57  .
drwxr-xr-x 7 root root      4096 Aug  4 20:21  ..
drwxrwxrwx 1 root root      4096 Jun 16  2018  Data
drwxrwxrwx 1 root root     20480 Dec 11 21:55  downloads
-rwxrwxrwx 1 root root 164053002 Dec  6 00:33 'How Particle Accelerators Are Used to Cure Cancer - with Simon Jolly.mp4'
-rwxrwxrwx 1 root root 162512661 Nov 26 01:00 'Hyperloop and the Future of Transport Technology - with Anita Sengupta.mp4'
drwxrwxrwx 1 root root         0 Oct 29  2016  MSOCache
-rwxrwxrwx 1 root root 303044487 Nov 29 15:32 'Q&A - Synthetic Intelligence - with Zdenka Kuncic.mp4'
-rwxrwxrwx 1 root root 289230431 Aug 20  2016 'Q&A - The Aliens Are Coming! with Ben Miller.mp4'
drwxrwxrwx 1 root root         0 Jul 14 10:35 '$RECYCLE.BIN'
-rwxrwxrwx 1 root root 184037990 Nov 29 11:17 'Synthetic Intelligence - with Zdenka Kuncic.mp4'
drwxrwxrwx 1 root root      4096 Jun 16  2018 'System Volume Information'
drwxrwxrwx 1 root root         0 Oct 27  2015  .Trash-1000
-rwxrwxrwx 1 root root 234096359 Nov  8 00:10 'What Makes Us Human - with Adam Rutherford.mp4'
drwxrwxrwx 1 root root      4096 Sep 14 17:22  windows
makem@ssdTOSH:/media/WinData$ mkdir test
mkdir: cannot create directory &#8216;test&#8217;: Read-only file system
makem@ssdTOSH:/media/WinData$

```

The partition is mounted:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=7f90b906-206f-4806-b66d-a83db8f7f3d0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=CCBC-12A0  /boot/efi       vfat    umask=0077      0       0
# /home was on /dev/sda3 during installation
UUID=d78428d2-66ad-474b-a7bc-8144945dd6a1 /home           ext4    defaults        0       0
# swap was on /dev/sda4 during installation
#UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5 none            swap    sw              0       0
UUID=0178c9df-c13e-434d-bb57-b6c19095f4aa none  swap    0       0
none /media/ramdisk tmpfs nodev,nosuid,noexec,nodiratime,size=1024M 0 0
#WinData
UUID=D232DC8B32DC75C7   /media/WinData  ntfs defaults   0       0
#testing
UUID=aa855949-81f9-4362-b314-29d55969ea63 /media/testing ext4 defaults  0       0

```

I have attempted to unmount and force a remount but cannot get the method correct and it fails.

Any guidance how to recover this correct permissions would be appreciated.

EDIT:

```

makem@ssdTOSH:~$ grep sdb6 /proc/mounts
/dev/sdb6 /media/WinData fuseblk ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
makem@ssdTOSH:~$

```

---

### Post by oldfred on 2018-12-17
Windows updates often turn fast startup back on.
And that sets hibernation flag which makes NTFS read only. It applies to all NTFS partitions Windows sees.
Check Windows settings.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

Abnormal shutdown also can corrupt file system. But if NTFS, you can only run chkdsk from Windows or a Windows repair disk with its repair console.
       Windows 10 chkdsk
[https://www.tenforums.com/tutorials/40734-drive-error-checking-windows-10-a.html](https://www.tenforums.com/tutorials/40734-drive-error-checking-windows-10-a.html)

---

### Post by CatKiller on 2018-12-17
It's a *long* time since I had access to an NTFS partition, but I recall that the kernel's ntfs isn't able to write. For read-write access you needed to use the userspace ntfs-3g.

Edit: oldfred has more recent information.

---

### Post by makem2 on 2018-12-17
Cheers OldFred, Windows did keep me waiting while prepared to do something prior to my returning to linux. Btw, this is a dual booted machine.

I will check the partition in windows and see the fastboot condition.

---

### Post by makem2 on 2018-12-17
> **CatKiller said:**
> It's a *long* time since I had access to an NTFS partition, but I recall that the kernel's ntfs isn't able to write. For read-write access you needed to use the userspace ntfs-3g.

Edit: oldfred has more recent information.

I have been using this partition for read/write for over a year and only a few minutes prior to this problem.

---

### Post by makem2 on 2018-12-17
The fastboot option was missing from windows power options so I used regedit:

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Power


HiberbootEnabled DWORD


0 = Turn off fast startup
1 = Turn on fast startup

I found fastboot was 'on' and set it to 'off'

I attempted to chkdsk the WinData partition which in fact is the 1TB HD in the laptop. Xubuntu is on an SSD on its own. I usually right click on the partition to access chkdsk but this time the system hung with the windows round and round circle.

I used command prompt to chkdsk D:/ and foundthat at stage 4 (cluster checking) it hung quite early in the check and just gave up.

I returned to linux and found I now had read/write access to /media/WinData.

I am now stuck as to what to do about the HD. Any help in that direction? I always backup everything so could start from scratch but that is such a time consuming exercise.

To clarify what I have in mind for the future in case it may affect advice:

I hardly ever using windows and in fact only need the use of internet explorer. I have a working windows virtual drive on the SSD but the banking internet explorer page I need to use uses a LCD dongle for security purposes and the USB of the virtual drive does not recognise it.

I want to swap my laptop for a 2 in 1 tablet at some stage and if possible use windows from a USBC flash drive or, if I have to, dual boot windows again.

I mention these thoughts in case it is suggested the existing HD is not repairable, on the way out and not to be trusted.

EDIT: I have used all of the methods mentioned by OldFred in:

[https://www.tenforums.com/tutorials/...dows-10-a.html]("https://www.tenforums.com/tutorials/40734-drive-error-checking-windows-10-a.html")

They all return no errors. However, I still cannot right click on the D: partition to access properties. In addition, Firefox keeps crash I think because my profile is in D:

Returning to windows a few minutes later I find I can now access D: correctly. I have no idea how this happened but my problem is solved and I will mark the thread as such.

---

