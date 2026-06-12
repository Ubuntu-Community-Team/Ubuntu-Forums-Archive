---
title: "When update-grub, Inode 17 keeps getting corrupted"
date: 2013-10-20
forum: General Help
---

### Post by tcf38012 on 2013-10-20
Hello,

Each time i do update-grub, my file system keeps getting remounted as read only. Then I have to reboot into my recovery disk and repair my file system.

Then I reboot back into my system, I run update-grub again, and then it gets corrupted. It does say read-only file system right after it says (found memtest+) I think it is os-prober because I have Mac OS X 10.9 GM and Windows 8.1 Pro installed with gptsync.

Dmesg:

```

[   71.221375] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   71.238075] JFS: nTxBlock = 8192, nTxLock = 65536
[   71.258184] NTFS driver 2.1.30 [Flags: R/O MODULE].
[   71.286456] QNX4 filesystem 0.2.3 registered.
[   71.305144] xor: automatically using best checksumming function:
[   71.343283]    avx       : 24393.000 MB/sec
[   71.411283] raid6: sse2x1    8970 MB/s
[   71.479281] raid6: sse2x2   11026 MB/s
[   71.547277] raid6: sse2x4   12952 MB/s
[   71.547280] raid6: using algorithm sse2x4 (12952 MB/s)
[   71.547281] raid6: using ssse3x2 recovery algorithm
[   71.575815] bio: create slab <bio-1> at 1
[   71.576402] Btrfs loaded
[   71.754605] EXT4-fs error (device sda4): ext4_ext_check_inode:464: inode #17: comm grub-mount: bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0)
[   71.754612] EXT4-fs (sda4): Remounting filesystem read-only
[   72.247746] EXT4-fs error (device sda4): ext4_ext_check_inode:464: inode #17: comm grub-mount: bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0)
[   73.591610] EXT4-fs error (device sda4): ext4_ext_check_inode:464: inode #17: comm grub-mount: bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0)

```


Thanks in advanced!

---

### Post by tcf38012 on 2013-10-20
Odd, but the only file in inode 17 is ._.Trashes

But when I try to delete it from my installation disk, it says Input/Output Error.

Update: ._.Trashes was made from the osx installation when I mounted the ubuntu installation with Pargon Ext4fs

---

### Post by tcf38012 on 2013-10-20
Solved, 

debugfs -w -R 'rm /._.Trashes' /dev/sda4


Thanks for the support lol.

---

### Post by Cavsfan on 2013-10-20
Wow that was quick. You opened and solved your own problem in just a few minutes. 

If you want to take the hassle out of grub, take a gander at the wiki in my signature. It is just a matter of placing a picture in **/boot/grub/** that is the same resolution as your screen. Then the fact that grub finds that picture it will pulls the font colors from **05_debian_theme** which just has to have 2 lines added to it. Then adding some stuff to **/etc/default/grub**.
Take a look at the last post in this thread and see if you like it. It is my grub screen after Saucy 13.10 was at final release.

[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by tcf38012 on 2013-10-20
Wow lol, u are just so ironic, because after I got that fixed I put an image on my GRUB2 background without looking at my thread.

Well, thanks anyways, I bookmarked it just incase ;)

---

