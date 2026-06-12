---
title: "How can I recovery data? Or how can I fix file system without deleting of data?"
date: 2015-03-10
forum: General Help
---

### Post by ferz2 on 2015-03-10
I have done


**fsck.ext4 -f /dev/sda5**

but questions were too much and I close one several times. After that I used several times e2fsck. But it was very slowly and I stopped one several times too. I've found the solve but maybe I hurt file system early. 
[B]e2fsck -f -b 32768 -y /dev/sda5[URL="http://ubuntuforums.org/archive/index.php/t-1245536.html"]

http://ubuntuforums.org/archive/index.php/t-1245536.html[/URL][/B]

I've tried several superblocks but I always got errors.
> 
Couldn't fix parent of inode 1949757: Ext2 inode is not a directory

Unconnected directory inode 1949759 (???) Connect to /lost+found? yes

Couldn't fix parent of inode 1949759: Ext2 inode is not a directory

Unconnected directory inode 1949760 (???) Connect to /lost+found? yes

Couldn't fix parent of inode 1949760: Ext2 inode is not a directory

Pass 3A: Optimizing directories Signal (11) SIGSEGV si_code=SI_KERNEL fault addr=(nil) e2fsck[0x425530]

/lib/x86_64-linux-gnu/libc.so.6(+0x364c0)[0x7f41a04104c0] e2fsck[0x4223ef]

/lib/x86_64-linux-gnu/libc.so.6(+0x39eb2)[0x7f41a0413eb2]

/lib/x86_64-linux-gnu/libc.so.6(+0x3aa75)[0x7f41a0414a75]

e2fsck(e2fsck_rehash_dir+0x261)[0x4228d1]

e2fsck(e2fsck_rehash_directories+0xe6)[0xd4234a6]

e2fsck(e2fsck_pass3+0x775)[0x419085] e2fsck(e2fsck_run+0x4f)[0x40d2df]

e2fsck(main+0xbf0)[0x4097f0]

/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f41a03fb76d]

e2fsck[0x40af75]

I think it's a software error because I met similar case on forum. I wrote down too much data on the partition. There are the photos from gparted  [IMG]http://s6.postimg.org/p77c0iqsh/f7f2f912c8bf6c8cd25f9d6a4c68af74.png[/IMG]
[IMG]http://s17.postimg.org/ehwutsnu7/83bfd2f70a83cab704473410aee9081e.jpg[/IMG]

I took photos until using of e2fsck. now the partition don't mount.
Some info from discs utility. Reallocatewhen sector count Falling. Count of remapped sectors. when the hard drive finds a read/write/verification error it marks the sector as 'reallocated' and transfers data to a special reserved area (spare area).I have to restore the data, is there any way?

Current pending sector count warning Number of sectors waiting to be remapped/ if the sector waiting to be remapped is subsequently written or read successfully this value is decreased and the sector is not remapped read errors on the sector will not remap the sector it will only be remapped on a failed write attempt

 Do you have any idea how to recovery data or fix partition?

---

### Post by tgalati4 on 2015-03-10
When you have a failing disk, like increasing number of bad sectors, those sectors get automatically written to "reserve" sectors.  This works OK until you run out of reserve sectors.  I would read about [data recovery]("https://help.ubuntu.com/community/DataRecovery") and use *testdisk* and then *photorec* (which is part of testdisk).

---

### Post by ferz2 on 2015-03-11
no, it don't work. wrote "maybe, the disk is damage"

---

### Post by tgalati4 on 2015-03-12
Which command failed?  *testdisk* or *photorec*?  It's possible that your disk has failed in a way that will not allow any tool to read it.  It happens.

---

