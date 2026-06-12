---
title: "This computer has only 0 bytes disk space remaining"
date: 2016-11-30
forum: General Help
---

### Post by giridhar.07 on 2016-11-30
I run Ubuntu 16.04.1 LTS on my laptop along with Win10. Today i installed an application called yEd. After the installation was complete, my laptop became very slow. I had to hard boot it. Now i get a popup that reads "This computer has only 0 bytes disk space remaining". Beyond this popup i only see the desktop icons. the launcher bar is missing. Terminal doesnt come up.

Without reinstalling Ubuntu is there a way to fix this. I have few important files that I dont want to lose.

---

### Post by DuckHook on 2016-11-30
Perhaps your latest app install filled up your Ubuntu partition, or it might mean anything from a failing HDD to a rogue process generating tons of files to you not giving the original partition enough room when you made it.

Have you tried booting from a LiveUSB? You may have to turn off fastboot and secure boot in the BIOS first. I don't use Win10 so am very rusty on procedures needed for safely booting from LiveUSB on dual-boot Windows systems. Make sure that you don't try "fixing" anything from the LiveUSB for now, because you don't want to make things worse (like nuking your Win10 partition, for example). The intent would be to mount your filled-up Ubuntu partition, backup the important files (to yet another external drive to be safe), then diagnose the problem, then fix by some combination of disk repair, deleting files, or growing the partition.

From now on, you should have a backup process as part of your general computing habits. Since you are dual booting with Windows, back up all critical info on that partition too. Does Windows allow you to make full recovery disks? If so, do that too. The biggest danger here is a failing HDD which sometimes also generates the symptoms you describe. After your data is safe, you can plan your next steps.

---

### Post by giridhar.07 on 2016-11-30
Thanks DuckHook, I am able to boot on Windows & using a LiveUSB. On Windows i looked at the harddrive utilization. Swap partition (ext4) has 0 free space. Is there a way to in increase its size.

---

### Post by DuckHook on 2016-11-30
A filled swap will not, by itself, generate the symptoms you describe. Moreover, I don't think a Windows partitioning app will give you proper info about your Linux partitions. Therefore, within a LiveUSB session, bring up a terminal and do:```
df -h
``````
sudo parted -l
``````
sudo blkid
```…and post all results back to this thread. This will give us some useful info on your Linux partitions. While you are at it, you may as well do:```
sudo lshw -sanitize
```…so we have all your HW info to work with. The output will be large, so please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by kingneutron on 2016-12-01
--If you can still boot into Linux, I would also recommend posting results of:

```
sudo du --max-depth=1 -h -c -x /
```# count up disk space being used from root, skip other mounted filesystems (this assumes you don't have separate /usr, /var, etc -- if you do, omit the -x )

--If running from the liveusb, it's a little harder. You can use ```
fdisk -l
``` and ```
blkid
``` to find partitions and try mounting them readonly, cd to the mount point and run the above command omitting the "/" (root filesystem) part. Will post more details if you need them.

---

### Post by giridhar.07 on 2016-12-02
Thanks again DuckHook for your help. I used a LiveUSB to boot my laptop and ran the commands you suggested. Please find the responses below.

**Code**: ```
df -h
```
**Output:**
```
Filesystem      Size  Used Avail Use% Mounted on
aufs            1.9G   24M  1.9G   2% /
tmpfs           775M  9.1M  766M   2% /run
/dev/sda1        15G  1.1G   14G   8% /lib/live/mount/medium
/dev/loop0      1.1G  1.1G     0 100% /lib/live/mount/rootfs/filesystem.squashfs
tmpfs           1.9G   24M  1.9G   2% /lib/live/mount/overlay
devtmpfs         10M     0   10M   0% /dev
tmpfs           1.9G   76K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G   12K  1.9G   1% /tmp
tmpfs           388M   24K  388M   1% /run/user/1000

```
**Code:** ```
sudo parted -l
```
**Output:**
```
Model: ATA ST500LT012-1DG14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs
 2      106MB   117GB  117GB   primary   ntfs            boot
 4      117GB   241GB  124GB   extended                  lba
 5      117GB   184GB  67.0GB  logical   ntfs
 6      184GB   237GB  52.6GB  logical   ext4
 7      237GB   241GB  4196MB  logical   linux-swap(v1)
 3      241GB   500GB  259GB   primary   ntfs

```**Code: **```
sudo blkid
```
[B]Output: 
[/B]```
/dev/sdb1: LABEL="UUI" UUID="1AF1-151D" TYPE="vfat" PARTUUID="c3072e18-01"
/dev/sda1: LABEL="System Reserved" UUID="42721C94721C8F33" TYPE="ntfs" PARTUUID="9d08764c-01"
/dev/sda2: UUID="3E1281DD12819A93" TYPE="ntfs" PARTUUID="9d08764c-02"
/dev/sda3: UUID="62EC7B82EC7B4F73" TYPE="ntfs" PARTUUID="9d08764c-03"
/dev/sda5: UUID="109F0C48109F0C48" TYPE="ntfs" PARTUUID="9d08764c-05"
/dev/sda6: UUID="67a950ce-70a0-406c-9ac4-a303c987e27f" TYPE="ext4" PARTUUID="9d08764c-06"
/dev/sda7: UUID="451f7f12-f90b-454e-a33d-53e940a17863" TYPE="swap" PARTUUID="9d08764c-07"
/dev/loop0: TYPE="squashfs"
```

---

### Post by giridhar.07 on 2016-12-02
Thanks kingneutron. I am able to boot using LiveUSB or Windows (dual boot). I ran your suggested commands but didn't get any valid output. I'm posting the outputs below for your reference.

```
amnesia@amnesia:~$ fdisk -l
bash: fdisk: command not found
amnesia@amnesia:~$ blkid
bash: blkid: command not found
```

---

### Post by DuckHook on 2016-12-03
I take it that /dev/sda6 is your Linux partition? If so, using LiveUSB, do the following, and post back all output:
```
mount /dev/sda6 /mnt
```
```
cd /mnt
```
```
df -h
```
```
sudo du -h --max-depth=1 | sort -hr
```This time, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Do not boot into Windows to try these commands, even if you have bash installed in Windows. Windows does not have the tools needed to work with ext4 partitions and is useless in anything other than Windows.

Please describe in detail the process you went through when you first set up dual boot.

---

### Post by giridhar.07 on 2016-12-04
Please find the output below.

**Code**
```
mount /dev/sda6 /mnt
```
[B]Output
[/B]```
special device /dev/sda6 does not exist
```

**Code**
```
cd /mnt
```
[B]Output
[/B]```
amnesia@amnesia:/mnt$
```

**Code**
```
df -h
```
**Output**
```
Filesystem      Size  Used Avail Use% Mounted on
aufs            1.9G   24M  1.9G   2% /
tmpfs           775M  9.1M  766M   2% /run
/dev/sda1        15G  1.1G   14G   8% /lib/live/mount/medium
/dev/loop0      1.1G  1.1G     0 100% /lib/live/mount/rootfs/filesystem.squashfs
tmpfs           1.9G   24M  1.9G   2% /lib/live/mount/overlay
devtmpfs         10M     0   10M   0% /dev
tmpfs           1.9G   76K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G   12K  1.9G   1% /tmp
tmpfs           388M   24K  388M   1% /run/user/1000
```

**Code**
```
sudo du -h --max-depth=1 | sort -hr
```
**Output**
```
 0    
```

**Question**
>  Please describe in detail the process you went through when you first set up dual boot.
[B]Response
[/B]> I installed it using LiveUSB. I didn't use any advanced/customized installation procedure. I just clicked NEXT...NEXT.. and completed my installation.
My apologies if I am not being comprehensive. I am a beginner to Linux.

---

### Post by DuckHook on 2016-12-05
giridhar.07, we seem to be spinning our wheels here. Perhaps my fault for not explaining what we are actually trying to do.

We are trying to mount your problem partition within your LiveUSB session, change into the newly created mount, and then run the commands that should tell us what and where the problems are. But if the problem partition fails to mount as the first step in this process, then it makes no sense to continue with the remaining steps, since they will tell us nothing. This is what happened in your last series of steps. When your mount attempt returned:```
special device /dev/sda6 does not exist
```…all further steps were rendered pointless. To solve this problem, it is important for you to understand what each step is designed to achieve rather than just blindly following instructions like a recipe.

Let's try again.

[LIST=1]
[*]Fire up a LiveUSB of Ubuntu.
[*]Within this LiveUSB, you must first find out which device designations have been assiged to your various partitions. You do this with:```
sudo blkid
```
[*]You will recall that you had produced this output in post #6 already, and I was relying on that output the second time around. Well, it seems that the LiveUSB session may have changed the device designation the second time around or some other hiccup occurred, so this time, first do:```
sudo blkid
```…again and note the line that contains the ext4 partition. It will look like the following:```
**/dev/sda6**: UUID="67a950ce-70a0-406c-9ac4-a303c987e27f" TYPE="**ext4**" PARTUUID="9d08764c-06"
```…This is your Linux partition. Note the device designation, in this example: */dev/sda6*
[*]Now, mount that device into your */mnt* directory with:```
mount /dev/sda# /mnt
```…replacing the # with the actual number of the device that the previous step revealed to you. The result must positively state that the mount was successful. Otherwise, the following steps are a waste of time. If the mount is *un*successful, stop what you are doing and just report results back to this thread.
[*]If mount is successful, change into the mounted directory (/mnt) with the following command:```
cd /mnt
```
[*]You should now be able to see how full that directory is using the following command:```
df -h
```
[*]Moreover, you can list and sort which files and directories are using up your disk space with the following command:```
sudo du -h --max-depth=1 | sort -hr
```
[/LIST]
Hopefully, this annotated series of steps will save you further misdirected effort and will return some meaningful info.

---

### Post by giridhar.07 on 2016-12-06
Thank you very much for explaining the steps. I now understand how we are trying to solve the puzzle.

Please find the output below.

**Code**
```
sudo blkid
```
[B]Output
[/B]```
/dev/sdb1: LABEL="UUI" UUID="1AF1-151D" TYPE="vfat" PARTUUID="c3072e18-01"
/dev/sda1: LABEL="System Reserved" UUID="42721C94721C8F33" TYPE="ntfs" PARTUUID="9d08764c-01"
/dev/sda2: UUID="3E1281DD12819A93" TYPE="ntfs" PARTUUID="9d08764c-02"
/dev/sda3: UUID="62EC7B82EC7B4F73" TYPE="ntfs" PARTUUID="9d08764c-03"
/dev/sda5: UUID="109F0C48109F0C48" TYPE="ntfs" PARTUUID="9d08764c-05"
**/dev/sda6: UUID="67a950ce-70a0-406c-9ac4-a303c987e27f" TYPE="ext4" PARTUUID="9d08764c-06"**
/dev/sda7: UUID="451f7f12-f90b-454e-a33d-53e940a17863" TYPE="swap" PARTUUID="9d08764c-07"
/dev/loop0: TYPE="squashfs"
```

**Code**
```
sudo mount /dev/sda6 /mnt
```
[B]Output
[/B]> Drive was successfully mounted

**Code**
```
cd /mnt
```
[B]Output
[/B]```
amnesia@amnesia:/mnt$
```

**Code**
```
df -h
```
[B]Output
[/B]```
Filesystem      Size  Used Avail Use% Mounted on
aufs            1.9G   24M  1.9G   2% /
tmpfs           775M  9.1M  766M   2% /run
/dev/sdb1        15G  1.1G   14G   8% /lib/live/mount/medium
/dev/loop0      1.1G  1.1G     0 100% /lib/live/mount/rootfs/filesystem.squashfs
tmpfs           1.9G   24M  1.9G   2% /lib/live/mount/overlay
devtmpfs         10M     0   10M   0% /dev
tmpfs           1.9G   76K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G   24K  1.9G   1% /tmp
tmpfs           388M   24K  388M   1% /run/user/1000
/dev/sda6        49G   46G     0 100% /mnt
```

**Code**
```
sudo du -h --max-depth=1 | sort -hr
```
[B]Output
[/B]```
184M    ./opt
4.0K    ./cdrom
4.0K    ./proc
16K    ./lost+found
88K    ./run
8.0K    ./media
34G    ./home
1.2G    ./var
530M    ./boot
12K    ./dev
2.9G    ./lib
3.9M    ./lib32
48K    ./tmp
4.0K    ./srv
4.0K    ./snap
19M    ./etc
13M    ./bin
7.4G    ./usr
348K    ./root
4.0K    ./lib64
4.0K    ./sys
4.0K    ./mnt
13M    ./sbin
46G    .

```

---

### Post by DuckHook on 2016-12-06
Excellent! Now we are getting somewhere.

*df* shows your Linux partition to be completely full.```
Filesystem      Size  Used Avail Use% Mounted on
…
/dev/sda6        49G   46G     0 **100%** /mnt
```This is no surprise. We expected that from your initial symptoms. *du* gives further info. What's of especially relevance to you are the following directories:```
34G    ./home
1.2G    ./var
2.9G    ./lib
3.9M    ./lib32
7.4G    ./usr
```…which means that you have a lot of apps and data packed in there. I consider myself a power-user and use about half the disk space for system files that you do.

The biggest disk hog is */home*, which is expected. If you can clean out some of the data that you've got accumulated in there, then your system will likely boot. The biggest files tend to be photos, videos and music. Do you have a lot of those? If so, you can either spin them off onto an external disk, or move them to another partition. You can do either action within the LiveUSB session.

After you've freed up some space and thus allow your Linux OS to boot again, then going forward, you will obviously have to do something about your Linux partition. It's too small for your computing habits, and ignoring it will only lead to a repeat of your current woes. There are a number of strategies you can consider, but if you are interested, please start another thread with just that topic. For now, let's just solve the matter at hand and get your OS working again.

---

### Post by giridhar.07 on 2016-12-07
....and we have a WINNER!! I cleared /home directory and Ubuntu started working. 

As a beginner it wasn't easy for me to run commands on the Terminal. I searched on this forum for commands to list files & folders and how to delete them. My terminal command vocabulary has now increased a fraction since I started this thread!

I sincerely thank you for your time.

I'll start another thread on increasing Linux partition.

Could you please recommend the best approach to learn Ubuntu and get a good grasp on it (read books on Ubuntu or get pursue Ubuntu certification or something else?).
 My long term goal is to gradually migrate to Ubuntu from Windows and once confident remove Windows (or at least limit Windows usage).

---

### Post by DuckHook on 2016-12-07
"As a beginner", you did amazingly well. It was nervy to do the deleting using the command line and my hat's off to you, but it is also perfectly fine to have used the GUI tools within the LiveUSB (like Nautilus) to do your moving/deleting work. We helpers tend to give instructions using the command line, but that is because GUI tools vary between flavours, whereas CLI tools are common to all. And it's much easier giving instructions in CLI form than trying to show steps in pictures, videos and drawing arrows.

Re: Linux knowledge

The links in my sig are all useful for those starting out in Linux/Ubuntu. With the exception of *Resurrecting Old Hardware*, which is rather specialized, they are useful to all new users.

As general advice, it isn't really that important to become a command line jockey. Many users get along fine with very little knowledge of the command line, using it only to troubleshoot with the help of the community. Some sites in addition to those in my sig:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Trusty](http://ubuntuguide.org/wiki/Ubuntu:Trusty)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://linuxjourney.com](https://linuxjourney.com)

The last one is relatively new and is especially slick and easy.

Of course, if you want to get some form of Ubuntu certification for work or career purposes, then you are most welcome, but most Ubuntu users are ordinary folks who just come to love the OS and slowly gain expertise with it. It's a slow and steady process, but you would be surprised how far you can get by just patiently plodding along (that's how I learned and how I still do it). I lurk on these forums and learn from the gurus. They are welcoming, generous with their expertise and insanely knowledgeable, so it's the best free resource of all.

As already said, I urge you to post another thread in the "New to Ubuntu" subforum for advice in dealing with the size of your partition. I'll keep an eye out and jump in if time allows.

---

