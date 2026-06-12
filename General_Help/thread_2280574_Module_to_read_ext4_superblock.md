---
title: "Module to read ext4 superblock"
date: 2015-05-31
forum: General Help
---

### Post by amit23 on 2015-05-31
Hi,

I'm totally a newbie to this forum. Please guide me how to write a module to read a superblock.

Regards
am

---

### Post by tgalati4 on 2015-05-31
Welcome to the forums.

Open a terminal:

```
sudo dumpe2fs /dev/sda1
sudo apt-get install hexedit
man hexedit
```

Use *hexedit* to look at specific sectors identified as superblocks in the *dump2efs* command.  Be careful.  You don't want to edit superblocks unless you know what you are doing.  System breakage is likely.

---

### Post by coffeecat on 2015-06-01
*Thread moved to **General Help**.*

---

### Post by amit23 on 2015-07-18
Sir,

My task is, to design a module which can read a suberblock.

Regards
Amit

---

### Post by coffeecat on 2015-07-18
> **amit23 said:**
> 
My task is, to design a module which can read a suberblock.


Is this a homework assignment? 

If so, please see [this]("http://ubuntuforums.org/showthread.php?t=2158945"):

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. 

---

### Post by amit23 on 2015-07-18
How to design a module which can read the superblock of existing running linux machine?
Do I need to register file system type for this or I can directly read it into a structure buffer?

Regards
Am

---

### Post by tgalati4 on 2015-07-18
I don't understand your question, but I would examine the *dump2fs* source code to determine exactly how the superblocks are found and identified.  If you can identify the superblocks, reading them is trivial.  The superblocks are part of a linux file system.  It doesn't matter if the system is running or not, the superblocks are static on the file system when it is created.

> tgalati4@Mint17 ~ $ sudo dumpe2fs /dev/sda1 | grep superblock
dumpe2fs 1.42.9 (4-Feb-2014)
  Primary superblock at 0, Group descriptors at 1-5
  Backup superblock at 32768, Group descriptors at 32769-32773
  Backup superblock at 98304, Group descriptors at 98305-98309
  Backup superblock at 163840, Group descriptors at 163841-163845
  Backup superblock at 229376, Group descriptors at 229377-229381
  Backup superblock at 294912, Group descriptors at 294913-294917
  Backup superblock at 819200, Group descriptors at 819201-819205
  Backup superblock at 884736, Group descriptors at 884737-884741
  Backup superblock at 1605632, Group descriptors at 1605633-1605637
  Backup superblock at 2654208, Group descriptors at 2654209-2654213
  Backup superblock at 4096000, Group descriptors at 4096001-4096005
  Backup superblock at 7962624, Group descriptors at 7962625-7962629
  Backup superblock at 11239424, Group descriptors at 11239425-11239429


The primary [superblock]("https://en.wikipedia.org/wiki/Ext2#ext2_data_structures") in Linux is always at Block 0.  I don't know how the backup superblocks are layed out.  If you only care about the primary superblock then just perform a read on Block 0.

What do you want to do with the data in the superblock?

---

