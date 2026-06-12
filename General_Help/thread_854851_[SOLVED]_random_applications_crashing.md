---
title: "[SOLVED] random applications crashing"
date: 2008-07-09
forum: General Help
---

### Post by LashSilence83 on 2008-07-09
I'm having issues with firefox crashing quite a bit and also other things will crash as well such as nautilus or azureus. Even when they don't crash sometimes I will have a couple firefox and nautilus windows open and everything will randomly grey out and often various programs will crash or cause the entire system to lock up, forcing me to ctrl+alt+F1. I also noticed that after I installed Fedora on a separate partition a few days ago and had grub problems that were fixed (sort of) by the super grub disk, I still can't boot fedora and when ubuntu is booting up, it fails the file system check. I'm not too sure if these issues correlate but I figure any extra info helps diagnose the problem. 

I'm using ubuntu 7.10 

thanks in advance. :)

---

### Post by cariboo on 2008-07-09
You should let fsck repair your hard drive first before doing anything else. It would be best if you did this from a liveCD and make sure your partition is not mounted. Use:

```
sudo fsck -a /dev/hdx
```

Where /dev/hdx is the drive that has a problem.

Jim

---

### Post by LashSilence83 on 2008-07-10
This is what I got from the check: 

ubuntu@ubuntu:~$ sudo fsck -a /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
/dev/sdb1: clean, 230444/37847040 files, 4014800/75674174 blocks


strange...:-|

---

### Post by LashSilence83 on 2008-07-10
Wait, was that supposed to clean it up or just run a check on it? I just like to understand what these commands mean for future reference. 

Alright, I just rebooted and got the same message about the file system check failing. It then tells me that I should fix it manually. How exactly do I go about doing that?

---

### Post by ajgreeny on 2008-07-10
If you can boot into ubuntu (I'm not sure about that from your post) open a terminal, or even go to console (Ctrl+Alt+F1) and enter ```
sudo touch /forcefsck
```Next time you boot ubuntu it will run the full fsck check and hopefully clear problems, though the error message about running a manual check may mean that I'm talking out of my ****.

---

### Post by LashSilence83 on 2008-07-10
ok, did that, and upon reboot it began checking the file system. after it got to about 95% I got this:


checking file systems...
fsck 1.40.2
fsck.ext3: unable to resolve 'UUID=0623d84f-d052-4568-b64a=9cb5cdbab4c8'
fsck died with exit status 8

after that it told me to repair manually or hit ctrl+D to continue. It seems like every time I boot up, there is something strange going on like nautilus won't start or my screenlets are moved around in strange ways, or I try to start firefox and it crashes within a minute or two. Everything is in pretty bad shape it seems... Perhaps an upgrade to hardy or reinstall of gutsy would remedy this problem? I wouldn't mind doing that but I'd really like to learn what I did to cause this and how it can be fixed. The easy way out doesn't really satisfy me...

---

### Post by ajgreeny on 2008-07-10
If you are running a system with more than one partition (other than swap and /) do you know which partition is UUID=0623d84f-d052-4568-b64a=9cb5cdbab4c8?  Have a look with ```
sudo blkid
```if you are not sure, to see if it is the root partition or /home, perhaps.  It seems possible that you have a problem either with disk hardware or with a file system.

---

### Post by LashSilence83 on 2008-07-10
ok, here's a (most likely) stupid question. Do these UUID numbers correspond with what kernel I'm running or are they basically telling the format and disc information? so here's what I got from running that. sdb1 is where ubuntu is:

/dev/sda1: UUID="E8FC9724FC96EC56" TYPE="ntfs" 
/dev/sda5: UUID="cf0498c7-43a5-4787-96ff-ef452855a732" SEC_TYPE="ext2" TYPE="ext3" LABEL="/1" 
/dev/sda6: TYPE="swap" LABEL="SWAP-sda6" UUID="9b8617eb-9198-45ac-8671-5efbe8e2ce9e" 
/dev/sdb1: UUID="9e0f0424-36e8-43fc-93e1-3e49a15ec9aa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="d4b348aa-f28e-44ab-900b-1a9a1b08e0d3" 
/dev/sdc1: UUID="483A-2E23" TYPE="vfat" 
/dev/sda7: UUID="0dd9e92c-c948-41f6-95ab-920f36055aa4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="2c14e9d9-8057-440d-8731-06a68bddb76c" 
/dev/sdd1: UUID="5D51-966B" TYPE="vfat" LABEL="BRAIN"

---

### Post by ajgreeny on 2008-07-10
So that explains part of the problem, at least.  You don't appear to have a partition with the UUID=0623d84f-d052-4568-b64a=9cb5cdbab4c8 so there is no way that fsck can check it.  What baffles me is why the system is trying to check something that does not appear to exist, and where it is getting this UUID from.

Let's see the output of ```
sudo fdisk -l
``` in ubuntu terminal as it may be that ubuntu is trying to mount something at boot that doesn't exist as well, causing instability in your whole system.

---

### Post by LashSilence83 on 2008-07-10
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18a718a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10444    83891398+   7  HPFS/NTFS
/dev/sda2           10445       60792   404420310    5  Extended
/dev/sda5           10445       13055    20972826   83  Linux
/dev/sda6           13056       14099     8385898+  82  Linux swap / Solaris
/dev/sda7           14100       16971    23069308+  83  Linux
/dev/sda8           16972       18146     9438156   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f89649a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37684   302696698+  83  Linux
/dev/sdb2           37685       38913     9871942+   5  Extended
/dev/sdb5           37685       38913     9871911   82  Linux swap / Solaris

Disk /dev/sdc: 1040 MB, 1040187392 bytes
1 heads, 32 sectors/track, 63488 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x488961a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2       63488     1015792    b  W95 FAT32

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001    c  W95 FAT32 (LBA)

---

### Post by ajgreeny on 2008-07-11
Sorry, my mistake!  I was thinking too quickly and not detailed enough.  What I really wanted to see was the output of ```
cat /etc/fstab
```to see what ubuntu is trying to mount at boot up.  And I though I was being so helpful.  Thats what comes of trying to do too many things at the same time.
Nevermind, let's see the output from that command above to see if fstab is trying to mount the non-existent partition.

---

### Post by LashSilence83 on 2008-07-11
it's quite alright! :) I just wish I could become more familiar with all this kinda stuff. I've read multiple linux basics books and none of them have really touched at all on this kind of stuff. I suppose I just need to find something a bit more comprehensive... 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=9e0f0424-36e8-43fc-93e1-3e49a15ec9aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=E8FC9724FC96EC56 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=0623d84f-d052-4568-b64a-9cb5cdbab4c8 /media/sda5     ext3    defaults        0       2
# /dev/sdb5
UUID=d4b348aa-f28e-44ab-900b-1a9a1b08e0d3 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

---

### Post by ajgreeny on 2008-07-11
OK, this shows that sda5 is trying to be checked and mounted at boot in fstab and that is the partition that is incorrectly noted by UUID.  You can edit your fstab file after backing it up easily enough.

First backup in terminal by typing ```
sudo cp /etc/fstab /etc/fstab.backup
```
Now edit the file as root with ```
gksudo gedit /etc/fstab
```The file will open in the text editor with root priviledges, so you can mess up here if you are not careful.  In the fstab file go to the line starting:-
UUID=0623d84f-d052-4568-b64a=9cb5cdbab4c8
and delete the exact part shown in the line above, ie from UUID to 4c8 inclusive, and replace it with:-
UUID=cf0498c7-43a5-4787-96ff-ef452855a732
Save the file and now reboot to check all is well.

The swap partition that was trying to be checked and mounted should now work OK and the fsck run through without stopping and causing you anxiety.

---

### Post by LashSilence83 on 2008-07-12
Well, that worked like a charm. Thank you very much for your patience and help. I would have never figured that one out on my own.

---

### Post by ajgreeny on 2008-07-12
Glad to be able to help.  It is very nice when you get to that point where you are able to repay all the help you had in the beginning by helping out with the (few) questions you can answer.
Please mark the thread as Solved by using the **Thread Tools** at the top of the page.

---

