---
title: "Anyway to recover my files after I accidentally installed on the wrong partition?"
date: 2014-12-25
forum: General Help
---

### Post by jgcsd on 2014-12-25
I accidentally installed on the wrong partition, and now a Linux install I wanted to keep is gone.

I did some searching yesterday and found a few programs that might help. One of them seemed to find a bunch of files, but most were .ecrypt files, since I had an encrypted home. Is there any hope at all I can get at least a few of my important files back from this mess?

---

### Post by hal8000b on 2014-12-26
This is probably the worst case scenario you have. Accidentally deleting a partition is easy to recover providing you have start and end sectors of the partion; however overwriting
with another filesystem will make recovery much more difficult and some files may not be recoverable at all.

Can you provide more information:
Start and end sector (of original partition )
Size and partition number e.g.  sda5   20G
Size of new partition.

File system that you overwrote the old filesystem with.

Recovery tools on linux are testdisk, scalpel and photorec.
Have a look at this page, particularly section 5 and 6:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Tutorial on scalpel:

[http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel](http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel)

[http://www.howtoforge.com/recover-deleted-files-with-scalpel](http://www.howtoforge.com/recover-deleted-files-with-scalpel)

Page on testdisk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you do manage to recover any files these will still be encrypted so you still need
to know your original passphrase.
Good luck.

---

