---
title: "EXT4 64bit option, Large file system question."
date: 2013-05-23
forum: General Help
---

### Post by zircon009 on 2013-05-23
I would like to migrate my existing XFS filing systems over to EXT4.  I have been using XFS for roughly the last four to five years, on my personal filing system.  I have read lots of post regarding ext4 and 16TB limit imposed by using 32bit inodes. While 64bit option in the format command will fix the issue. I'm a little concerned its not production ready. The posts I have been seeing, while a year or two old, do not gleam confidence. I have 50TB of usable space, spread over three map points.(two 20TB array and one 10TB array). There is almost 100% certainty these will be expanded in the future, and already exceed the old e2fsprog 16TB limit. I just stuck in the 10TB array to facilitate the data moving shuffle. The 32bit integer struck me a few years back with the mdadm 0.90 array metadata version, and I would like to not be boxed in.  I screwed up one of the formats on the last 20TB, and need to recreate it regardless.  It has 25K ag count, and this causes issues mounting if its dirty or file check it.  I have enough free space to pivot, but is ext4 safe on large filesystems?  The primary reason I would like to go with EXT4 is for the option to shrink the file system. 

Thanks.

---

### Post by dino99 on 2013-05-23
what you have read is about ext3 limits; ext4 is way huge and is the most used and quite stable now
[https://ext4.wiki.kernel.org/index.php/Ext4_Howto](https://ext4.wiki.kernel.org/index.php/Ext4_Howto)

---

### Post by prodigy_ on 2013-05-23
With those amounts of storage (and, presumably, data) you might want to look into ZFS instead. Especially if you need to protect your data against silent corruption.

---

### Post by HiImTye on 2013-05-23
I wouldn't use zfs on linux yet, if you want to use it, OpenBSD is your only real choice right now. also, you will want to do some reading on zfs first, so you don't use features like dedupe

ext4 is very usable now, but you should still always back up your data

---

### Post by zircon009 on 2013-05-23
The limitations that I have been reading about, is limited to E2FSPROG  toolset, not the kernel ext4. This toolset is used to create and maintain EXT4, and other  filesystems. Up until version 1.42, it was a 32 bit applications, and  could not create or expand a drive larger than 16TB, even on EXT4 file  type.  Nov 29, 2011, version 1.42.0 was released, and the code based was  fully 64bit compliant, which fixed this max file system size limit.   Now, this has only been around for just under two years, which is not  the most mature code base from my experience.  Most people do not have  16TB drives, and this is not a issue. I would not be concerned with a  less than 16TB EXT4 file system, as that has been proven reliable for years.   I do admit that I'm a little more concerned with a over 16TB file  systems on EXT4, and it possibly having issues with it.  [http://e2fsprogs.sourceforge.net/e2fsprogs-release.html#1.42](http://e2fsprogs.sourceforge.net/e2fsprogs-release.html#1.42)   The current release of e2fsprog is 1.42.7.

Here is a snippet from a e2fsprog release log that sums up my concern:
E2fsprogs 1.42.4 (June 12, 2012) [http://e2fsprogs.sourceforge.net/e2fsprogs-release.html#1.42.4](http://e2fsprogs.sourceforge.net/e2fsprogs-release.html#1.42.4)
Fixed more 64-bit block number bugs (which could end up corrupting file systems!) in e2fsck, debugfs, and libext2fs.

Also, I did figure out the problem with the problematic XFS file  system.  I just used the defaults when creating, and since the drive is  a lvm logical volume, the default settings for XFS are junk. I should of  read the XFS.org faq more closely.  If I had used the md0 device  directly, it would of picked the default settings correctly. 

Thanks  for the zfs suggestion, but I'm fine with mdadm raid with lvm running  on top of it.  It works fine for my simple cifs/nfs file server and does  all that I ask of it. 

Thanks.

---

