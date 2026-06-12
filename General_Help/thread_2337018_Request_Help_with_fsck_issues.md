---
title: "Request Help with fsck issues"
date: 2016-09-13
forum: General Help
---

### Post by m9ke2 on 2016-09-13
I am running Mate 16.04.  I could really use some help understanding and using fsck with this computer.

Two hard disks installed:   
I boot from an SSD: 
/dev/sda1 a fat 32 EFI system partition
/dev/sda2 an ext4 partition

Data is on a conventional spinning drive:
/devsdb1 a linux swap partition
/dev/sdb2 an ext4 partition where Home lives

System boots and runs fine.   However I was poking around in /var/log/fsck and found that  the file called checkfs and the file called checkroot both say 'Nothing logged yet'.  

This led me to wonder if the system is fsck-ing as it should.  I booted from an Ubuntu USB drive and ran [COLOR=#000000][FONT=&amp]sudo e2fsck -f /dev/sd*

The fscks seemed to run, but seemed to complete quicker than they should have to scan my boot drive 250 GB and my data drive of 2TB.  Afterwards I went back to [/FONT][/COLOR]/var/log/fsck and found that both the file called checkfs and the file called checkroot both STILL say 'Nothing logged yet'.  

I am not confident that i actually ran fscks when I thought I did, due to the speed with which they seemed to complete, and due to the logs still saying nothing to log after the fsck supposedly ran.

I have searched this forum and googled on the net, but much of what is out there pertains to earlier pre-systemd systems, and does not address any differences that might exist for fsck-ing an ssd drive.

If you are still reading thanks!  My questions:

1. What is the proper way to run fsck on a systemd computer that has one ssd and one spinning drive?
2. Is /var/log/fsck the proper path to the logs for fsck?

Thanks very much!
m9ke

---

### Post by ajgreeny on 2016-09-13
I have both those exactly same named files in /var/log/fsck with the same contents after 2 years on this OS which I know has been through many fsck operations as I have it set to run every two months.
Have a look at your filesystem with ```
sudo tune2fs -l /dev/sda2
``` which I assume is your root partition.
That will show you three lines with information on filesystem checks similar to this.
```
Last checked:             Fri Jul 22 20:23:51 2016
Check interval:           5184000 (2 months)
Next check after:         Tue Sep 20 20:23:51 2016
```

---

### Post by m9ke2 on 2016-09-13
Thank you ajgreeny.  Trying that now.

---

### Post by m9ke2 on 2016-09-13
I ran the commands suggested by ajgreeny and got the results below.


The below shows that /dev/sda2 and /dev/sdb2 were last checked in May, and the check interval is zero.
Also /dev/sda1 and /dev/sdb1 could not be opened due to a bad magic number.


It looks to me like fsck has not been running regularly as it should.  I also don't know what the magic number error means.


sudo tune2fs -l /dev/sda1 Returned: 
tune2fs: Bad magic number in super-block while trying to open /dev/sda1  Couldn't find valid filesystem superblock.


sudo tune2fs -l /dev/sda2 Returned: 
Last Checked: Tue May 31 and Check Interval: 0 (none)


sudo tune2fs -l /dev/sdb1 Returned: 
tune2fs: Bad magic number in super-block while trying to open /dev/sdb1  Couldn't find valid filesystem superblock.


sudo tune2fs -l /dev/sdb2 Returned: 
Last Checked: Tue May 31 and Check Interval: 0 (none)


Can you assist with getting a valid fsck on my drives and figuring out the magic number error?

---

### Post by Dennis N on 2016-09-13
Here is what I know, including how to set the check interval.

1) Find last time a file system was checked - you need to specify the file system here. 
```
dmn@Sydney:~$ sudo dumpe2fs /dev/sdb6 | grep -i last
dumpe2fs 1.42.12 (29-Aug-2014)
Last mounted on:          /
Last mount time:          Tue Sep 13 16:07:53 2016
Last write time:          Tue Sep 13 16:07:53 2016
Last checked:             Sat Sep 10 10:54:28 2016

```
2) Find maximum mounts allowed between checks. If Maximum mount count = -1 or 0, there is no checking. Here it checks every 30 mounts, and has been mounted 4 times since last check. In recent releases, this has been disabled by Maximum Mount Count set to -1. 
```
dmn@Sydney:~$ sudo dumpe2fs /dev/sdb6 | grep -i count
dumpe2fs 1.42.12 (29-Aug-2014)
Inode count:              1664640
Block count:              6656000
Reserved block count:     332800
Mount count:              4
Maximum mount count:      30

```
_There are other situations which cause a check, such as unclean unmount of a file system._

3) Set Maximum Mount Count to 40.
```
dmn@Roxanne:~$ sudo tune2fs -c 40 /dev/sdb8
[sudo] password for dmn: 
tune2fs 1.42.8 (20-Jun-2013)
Setting maximal mount count to 40
```
-------------------------------------------------------------
systemd runs the fsck programs now through systemd-fsck, which calls the right fsck program for each file system at startup. 
You can see the actions with journalctl. Below, the calls took 6 seconds for all 3 file systems, and it looks like it reports the state, checked or not. I don't know if any were actually checked this time.

```
dmn@Sydney:~$ journalctl -b | grep fsck
Sep 13 16:07:47 Sydney systemd[1]: Created slice system-systemd\x2dfsck.slice.
Sep 13 16:07:47 Sydney systemd[1]: Starting system-systemd\x2dfsck.slice.
Sep 13 16:07:47 Sydney systemd[1]: Listening on fsck to fsckd communication Socket.
Sep 13 16:07:47 Sydney systemd[1]: Starting fsck to fsckd communication Socket.
Sep 13 16:07:53 Sydney systemd-fsck[421]: Xubuntu-1504: clean, 349548/1664640 files, 2948804/6656000 blocks
Sep 13 16:07:53 Sydney systemd-fsck[436]: Common-Files: clean, 51807/7922544 files, 13490381/31744000 blocks
Sep 13 16:07:54 Sydney systemd-fsck[435]: fsck.fat 3.0.27 (2014-11-12)
Sep 13 16:07:54 Sydney systemd-fsck[435]: /dev/sda1: 9 files, 917/130812 clusters

```

On the magic number error, I have no idea what to do about that. Sorry.

---

### Post by Dennis N on 2016-09-13
superblock may not be too hard to fix. Two hits with google:

(for ext4, old - but may still be good)
[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

(a bit newer)
[http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks](http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks)

Maybe you can find others that are better.

Never encountered such errors, or tried this kind of fix myself.

---

### Post by ajgreeny on 2016-09-14
The bad superblock error is most probably because partitions sda1 and  sdb1 are both fat32 EFI partitions; they are normally the first partition on each disk and there is no need to worry about that. tune2fs is fgor ext# partition only.

---

### Post by m9ke2 on 2016-09-14
Thank you ajgreeny and Dennis N.   I will get to work on this following you suggestions and post results back here.

---

### Post by m9ke2 on 2016-09-14
Temporarily set fsck frequency for all four partitions for one restart, restarted, and got the results below.  Reset it to 30 after getting these results:


sudo tune2fs -c 1 /dev/sda1  Returned: Bad magic number in super-block while trying to open /dev/sda1  Couldn't find valid filesystem superblock.
sudo tune2fs -c 1 /dev/sda2  Returned: Setting maximal mount count to 1
sudo tune2fs -c 1 /dev/sdb1  Returned: Bad magic number in super-block while trying to open /dev/sda1  Couldn't find valid filesystem superblock.
sudo tune2fs -c 1 /dev/sdb2  Returned: Setting maximal mount count to 1


Due to the magic number error, I don't think the system was able to increase the fsck frequency  on /dev/sda1 (on an SSD disk) and /dev/sdb2 (on a conventional spinning disk).  


I will come back to the magic number issue later.


For now, on restart, I got a message 'Checking in progress on one disk'.   


Looks like I am getting an fsck on at least one partition (/dev/sda2 and/or /dev/sdb2).  However, since these partitions are on two separate physical disks, should this message be saying 'Checking in progress on *two* disks' not 'Checking in progress on *one* disk' ?

---

### Post by Dennis N on 2016-09-14
Well, after considering all information here, I doubt if anything is wrong. tune2fs and dumpe2fs only work on ext2,ext3,and ext4 file systems, not FAT or swap. So that is probably why you get the errors.

You can check type codes for partitions - I believe only those with code 8300 are checkable on a user defined schedule with fsck (see below in red). systemd also is calling fsck.fat to check FAT filesystems (if there are any) on every boot. I know no way to include FAT file system checks in the periodic checks set up using tune2fs or any other way.  


```
[dmn@Sydney ~]$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

[some output omitted here]

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  
   [COLOR="#FF0000"]2         1050624        82970623   39.1 GiB    8300  [/COLOR]
   3        82970624        91162623   3.9 GiB     8200  
   [COLOR="#FF0000"]4        91162624       345114623   121.1 GiB   8300[/COLOR]  
   [COLOR="#FF0000"]5       345114624       402458623   27.3 GiB    8300[/COLOR]  

```

Code EF00 is for EFI system partitions, code 8200 is for swap.

If I try to get information on partition 1 (or 3) here, I get the same error:

```
[dmn@Sydney ~]$ sudo dumpe2fs /dev/sda1 | grep mount
dumpe2fs 1.43.1 (08-Jun-2016)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda1

```

---

### Post by m9ke2 on 2016-09-14
Thank you Dennis N.  I am away from my computer right now but will try gdisk as you suggest when I get home.  I did not know about the codes (EF00 and 8300) and am anxious to see what i get back from my disks.  Thank you very much!

---

### Post by m9ke2 on 2016-09-14
Thank you Dennis N!

sudo gdisk -l /dev/sda showed two partitions, the first one an EFI system partition with a code of EF00.  The second partition had a code of 8300.  So only the second partition (code 8300) is getting checked, due to partition type. 

sudo gdisk -l /dev/sdb also showed two partitions, one labeled Linux swap with  a code of 8200.  The second partition was labeled Linux filesystem and had a code of 8300.  So again only the second partition (code 8300) is getting checked, due to partition type. 

This proved to me that the partitions belonging to the type than can be checked are in fact coded 8300.  I also wanted to verify that the partitions with code 8300 are actually getting checked:

sudo tune2fs -l /dev/sda2 shows a clean filesystem state and that it was last checked today.
sudo tune2fs -l /dev/sdb2 shows a clean filesystem and that it was last checked today.

I am satisfied that nothing is wrong with my system.  

What I learned in this exercise is that I needed to change the default maximum mount count to get any partition checked by fsck.  Also learned that even though the fsck message at boot time says 'Checking one disk' both my partitions that can be checked are in fact getting checked.  Finally I now know that some partition types such as swap and EFI partitions are not supposed to get checked by fsck.

Dennis N and ajgreeny thanks very much for the help and education!

---

### Post by ajgreeny on 2016-09-15
You're very welcome.

It's good to learn something new and no-one is beyond doing that!

---

