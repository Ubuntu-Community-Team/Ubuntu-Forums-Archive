---
title: "Ubuntu sharing files with Windows"
date: 2017-05-24
forum: General Help
---

### Post by xpeaceservant on 2017-05-24
[LIST=1]
[*]So I noticed from a older install, and the install I did the other day that I can see my Windows file folders when running Ubuntu.  If there is a 'partition', separation between the operating systems, how is it then that I can see the other stuff?
[*]Is Ubuntu using anything from Windows to operate, or is it 100% independent?  I would think independent is the answer because it could run entirely with an over-write of Windows.
[/LIST]

---

### Post by TheFu on 2017-05-24
There is a FUSE file system driver called ntfs-3g which allows Unix systems to directly access many NTFS storage types.

Yes, you can completely wipe Windows. Is that bad?
Windows can completely wipe Linux too.

---

### Post by Bucky Ball on 2017-05-24
Ubuntu is running 100% independently of Windows. Wouldn't matter if it was there or not. You can see the files, but not a great idea to use the Win OS partition in day to day operations as part of your routine. One false move and you could render your Win unbootable or very broken. 

As above from TheFu. An NTFS filesystem partition is an NTFS filesystem partition as far as Ubuntu is concerned. It will show you what's there regardless what's on it. Very common for users to set up an NTFS 'share' partition (not the Win OS partition!) for data to be shared between Ubuntu and Win as both can read/write to NTFS but Win can't use EXT4.

---

