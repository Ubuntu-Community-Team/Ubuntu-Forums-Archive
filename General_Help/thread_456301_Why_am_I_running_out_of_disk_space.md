---
title: "Why am I running out of disk space?"
date: 2007-05-27
forum: General Help
---

### Post by coffebuntu on 2007-05-27
I have no idea what is going on here...I have Ubuntu feisty installed on a machine with a 40GB hd. Everything was perfect until today when i powered on and could not log in because of a (paraphrasing here) "disk space full, could not write to home directory" message. I was fighting with it for awhile until I booted from an Ubuntu live cd, then deleted a few files using the command line. Ok after a reboot, I was in. Logged in and everything with no problems...but wait! Since i was in i thought it best to do some cleanup so my drive wouldn't "fill up" again. Using the disk usage analyzer tool it shows 100% of 11.9 GB being used...ok, fine...but then above that it reads only 3.8GB of the file system free?? What is going on? All removable devices are unmounted.

Why is Ubuntu reading only 3.8GB of 40GB free, while showing only 11.9GB of disk space used? I am completely baffled! Please, help! :o

---

### Post by Crafty Kisses on 2007-05-27
Did you completley format when you installed, or did you partition?

---

### Post by drs305 on 2007-05-27
In terminal, type:
```
gparted
```

Assuming you have gparted installed, you will be able to graphically see how your drive is partitioned and how much space you have left in each partition.

You can also get a graphical depiction with System, Administration, System Monitor.

---

### Post by myname on 2007-05-29
Question,

How do you delete files from the command line?  I am running into this very same problem.  I tried deleting from Konqueror (Kubuntu feisty), but I also get the (paraphrased) "not enough disk space to delete" message.  I just need to log in one more time, and copy some files over to make sure they are backed up before I do a reformat.

I tried from the console, but got an error because the directory I need to delete contains a ( in it.

Any help?

--Kevin

---

### Post by fanatik on 2007-05-29
```
df -h
```

will show you filesystem usage.

```
rm -- 'filename'
```

will remove files with dodgy chars in them.

---

### Post by jollemeyer on 2007-05-31
Same problem here !

I believe this is related to the kernel update, which I performed yesterday. My root partition is approx. 14GB in size. I remember that I was using less than 7GB before the update, leaving 7GB free space. However, now my disk is 100% full !

I tried to figure out, where all the disk space has been allocated:

/usr    2.2 GB
/var    0.2 GB
/lib      0.2 GB
/home 0.5 GB
The other folders contain only small amounts of data.

Given the values above, I should allocate approx. 3GB, but somehow I seem to allocate 14GB ?!?

So, where is all my disk space gone ??

By the way, I'm using the following IDE controller:
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)

My hard disk is a Samsung SP0802N (IDE drive).


I will reboot to the previous kernel and see, if my free disk space appears again ...

Please help!

---

### Post by jollemeyer on 2007-05-31
OK, I just rebooted to the previous kernel version.

The disk allocation is the same there. So this is probably not related to the kernel update as I previously suspected.

I already performed a fsck. This is the output:
  ```
128997 inodes used (6.89%)
    1377 non-contiguous inodes (1.1%)
         # of inodes with ind/dind/tind blocks: 8956/725/0
 3422389 blocks used (91.38%)
       0 bad blocks
       1 large file

  104250 regular files
   13335 directories
    1255 character device files
    4547 block device files
       2 fifos
     526 links
    5616 symbolic links (5041 fast symbolic links)
      13 sockets
```

The question remains: Where is all my disk space gone? 
As stated in my previous post, my files sum up to approx. 3GB, whereas 'df -h' claims I am using 13GB.

Am I missing anything ?

---

### Post by jollemeyer on 2007-06-01
Here is what I found when googling around:

[INDENT]The standard cause for this is some user process keeping a deleted file open. When this happens, the space is not visible via 'du', since the file is no longer visible in the directory tree. However, the space is still used by the file until it is deallocated, and that can only happen once the last process which has the file open either closes its file descriptor to the file, or the process exits. You can use the lsof program to try to find which process is keeping an open file. Usually it's some log file, or some large data base file which gets rotated out, but some older process are still keeping the log file open. [/INDENT]

This should explain where all my disk space is gone.

But how can I recover it?

I did a reboot, but the files still seem to be allocated. Strange ...

Can anyone help us out?

---

### Post by fanatik on 2007-06-01
run:

du -ks /* | sort -n

might take a while, but should show you the culprits. :)

---

### Post by jollemeyer on 2007-06-01
@fanatic: I don't think the 'du' command will help me any further.
My problem is that I have a misreading between 'du' and 'df'. 

When I sum up all 'du' values, I end up allocating approx. 3GB. However, 'df' tells me, I allocate 13GB !

I believe this is related to open files that are dead in the system and still allocate space. The are counted with 'df' but not with 'du'. My previous posting points in this direction. However, I have no idea how to remove the dead files.

'lsof' tells me that quite some files are open, but I don't know if they are indeed dead or just in the current session.

I already fscked my filesystem. However, that didn't bring me any further :( 

Any help is appreciated ...

---

### Post by jollemeyer on 2007-06-01
@fanatik: As I said before, 'du' only finds 3GB.

```
0	/cdrom
0	/initrd.img
0	/initrd.img.old
0	/proc
0	/sys
0	/vmlinuz
0	/vmlinuz.old
4	/initrd
4	/opt
4	/srv
16	/lost+found
32	/media
88	/tmp
296	/dev
4624	/bin
5568	/sbin
7172	/root
9368	/etc
19912	/boot
146852	/home
186612	/var
259496	/lib
2235064	/usr
```


Whereas 'df -h' gets this result:

Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/hda6              15G   13G  678M  96% /

So, where are the remaining 10GB ??

I attached the output of 'lsof' as well.


Any help is appreciated.

---

### Post by jollemeyer on 2007-06-03
I found the reason for my disk space problem.

I accidentally wrote files the the mount point of a secondary drive at the root file system.

The files there filled my root partition but were not counted by 'du' when the secondary drive was mounted to the mount point.

I discovered the problem when I booted a Live CD and investigated my file structure in detail. Since the secondary drive was not mounted to that mount point, I could find the parasitic files easily. 

I just had to delete them and to correct my mount setup.

To make a boring story short: The problem was in my side. No problem in Ubuntu.

Maybe this is of help to somebody else ...

---

### Post by Wolfie Lee on 2008-01-26
It seems I have the same, or a similar problem, I am running a similar set-up (My main OS is on a 40GB HDD, while I have a new 500GB HDD for my storage...although in order to use it, I had to install the system, WITHOUT  any updates or applications, onto my new storage drive {I'm a SERIOUS NOOB, and could not get the main HDD / OS to recognize / mount / use the new drive any other way...and I will NEVER fill It up, most likely, so this is ok with me...for now}. I'm too new to fully understand how, exactly, you:     A.) found to culprit files / logs to delete
B.) How You were able to delete them WITHOUT re-installing the system to the OS drive ( I do NOT want to do this, as I will lose my unfinished torrent downloads)


:confused:

---

### Post by kaivalagi on 2008-02-04
Hi,
I have the same issue too it seems. I can't manage to get to the bottom of the free disk space available versus's (partition size) - (what is actually used)

I am running gutsy 64 bit and after dumping about 10Gb the system still reports I have the same amount of free space as before??? 

I have rebooted, tried forcing fsck etc to no avail...

I'm confused!

I've attached a screenshot from disk usage analyser, the numbers just don't add up to 12.5GB!

I've had a brief look at my mount points and all seems okay, I am not sure what to do next...

Any help would be really appreciated :)

---

### Post by kaivalagi on 2008-02-04
Just to make sure I also ran the command fanatik kindly provided (du -ks /* | sort -n) in the terminal and got the following (note I removed my /home and /media directories as these relate to other partitions and disks which don't factor in)

0       /cdrom
0       /initrd.img
0       /lib64
0       /proc
0       /sys
0       /vmlinuz
4       /initrd
4       /mnt
4       /srv
16      /lost+found
20      /opt
96      /dev
128     /tmp
3128    /lib32
5848    /bin
7268    /sbin
10988   /etc
18628   /boot
180608  /lib
396368  /var
3020552 /usr
9351860 /root

That root folder seems rather large! That looks like where the space has gone, but when I delve deeper I can't find the 'root' cause

This is driving me nuts, any ideas....please :)

---

### Post by kaivalagi on 2008-02-04
Sorry for all the posts but I figured it. It turned out to be what everyone has suggested to check, the trash in the root folder. I just couldn't find the affending files/folders as I was looking as a non-root user. All sorted now, space reclaimed!

So, if anyone else has a similar problem make damn sure you check the root trash folder as a root user, i.e:

run: gksudo nautilus /root/.Trash &

Cheers

---

