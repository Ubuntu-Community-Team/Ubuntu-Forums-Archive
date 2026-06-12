---
title: "Can I do 2 seperate installs of ubuntu 14.04"
date: 2014-09-26
forum: General Help
---

### Post by Tom_Carr on 2014-09-26
I installed ubuntu 14.04, then did a thing where it is combined with xubuntu in one install.  I would like to have a new, clean, separate intall of 14.04 on the same computer, so I would have a choice of which one to use.  Can I do this?  If I just put in the install DVD will it ask me the right questions to set it up this way?

---

### Post by Bashing-om on 2014-09-26
Tom_Carr; Hello ;

The answer is Yes and yes.

Now the question is - How much control do you want to exercise ?
a) install along side, and the installer will make all the decisions for system set up.
b) you may set up the system partitioning before hand - with some small amount of thought and effort on your part.

For instance and reference; My system set up, quad booting 'buntus:
```

sysop@1404mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
sysop@1404mini:~$

sysop@1404mini:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
sysop@1404mini:~$

```

Keep in mind, this is ubuntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT]

---

### Post by Tom_Carr on 2014-09-26
Thanks for the info Bashing-om.  
I am a very simple user.  I do what I can with the GUI.  I don't venture into the system level code.  I know my limitations.
I will let the installer make the decisions for me.
My big question, which I think you answered, is if I can install the new clean version without effecting the current version.
From what you said, I assume I can just pop in the DVD, answer the installers questions, and know that my old version is safe as I install a new version.
Correct?

---

### Post by Bashing-om on 2014-09-26
Tom_Carr; Yepper.

In essence that is correct. Murphy's Law always applies, what ever can go wrong will go wrong, always advised to back up important data ( or it is not important).

I have never had a problem installing for dual booting. But there is a bug presently that you need to be aware of.
Maybe only effects UEFI systems but worth a few minutes to read and heed.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)
Where choosing the option to "install alongside" wipes the whole drive.
The workaround is to choose "something else" and set up partitions manually - just to be on the safe side.

[INDENT][INDENT]where is my rose colored glasses ?
[/INDENT][/INDENT]

---

