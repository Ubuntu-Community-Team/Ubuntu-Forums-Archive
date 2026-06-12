---
title: "undestanding disk usage (for newbies)"
date: 2018-07-13
forum: General Help
---

### Post by pjstock on 2018-07-13
I am a long time user/lover of Ubuntu but I seem to never have really progressed beyond the Newbie level of sophistication in that use.
So, Disk Usage analysis still baffles me.
this morning I had a popup message (which I failed to grab a snap of) alerting me to Low Disk Space (down to 830Mb). I clicked on Examine which popped up the graphic disk use tool.

But for the life of me I cannot find the low disk space.

all my disks seem to show sufficient (2Gb-3+GB) Free disk space.
the base 80GB HDD is partition as follows: 21GB for LInux, 4GB for swap and 54GB for other (I think it's WIndows and storage)

I know that serious Ubuntu/Linus users drill down and use terminal commands to really assess their disk use, but I've never figured that out.
Can anyone either tell me what they see from my screenshots OR coach me through command line instructions to get a grip on this.

Many thanks

Peter

---

### Post by &amp;KyT$0P# on 2018-07-13
Please post the output from running these commands in Terminal -
```
df -hT
df -hTi
```

---

### Post by pjstock on 2018-07-13
```
peter@CollierDesk:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.0G     0  2.0G   0% /dev
tmpfs          tmpfs     397M   12M  385M   3% /run
/dev/sdb5      ext4       33G   29G  3.1G  91% /
tmpfs          tmpfs     2.0G   13M  2.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     397M   88K  397M   1% /run/user/1000
/dev/sdd1      fuseblk   932G  247G  686G  27% /media/peter/WD
/dev/sdc1      fuseblk   1.9T  1.6T  254G  87% /media/peter/Seagate Expansion Drive
/dev/sda5      ext4       20G   17G  2.1G  89% /media/peter/9ee3603b-73ca-47fe-8364-5fb0925fcd20
/dev/sda2      fuseblk    51G   43G  8.3G  84% /media/peter/5ABA2917BA28F0E5
/dev/sde1      vfat       15G   13G  1.9G  88% /media/peter/3429-E77A
```

```
peter@CollierDesk:~$ df -hTi
Filesystem     Type     Inodes IUsed IFree IUse% Mounted on
udev           devtmpfs   201K   589  200K    1% /dev
tmpfs          tmpfs      210K   854  209K    1% /run
/dev/sdb5      ext4       2.2M  673K  1.5M   32% /
tmpfs          tmpfs      210K    52  210K    1% /dev/shm
tmpfs          tmpfs      210K     6  210K    1% /run/lock
tmpfs          tmpfs      210K    18  210K    1% /sys/fs/cgroup
cgmfs          tmpfs      210K    14  210K    1% /run/cgmanager/fs
tmpfs          tmpfs      210K    38  210K    1% /run/user/1000
/dev/sdd1      fuseblk    686M   11K  686M    1% /media/peter/WD
/dev/sdc1      fuseblk     65M  891K   64M    2% /media/peter/Seagate Expansion Drive
/dev/sda5      ext4       1.3M  603K  667K   48% /media/peter/9ee3603b-73ca-47fe-8364-5fb0925fcd20
/dev/sda2      fuseblk    8.6M  176K  8.4M    3% /media/peter/5ABA2917BA28F0E5
/dev/sde1      vfat          0     0     0     - /media/peter/3429-E77A
peter@CollierDesk:~$
```

---

### Post by TheFu on 2018-07-13
I hate GUI tools for this stuff.   GUIs lie and  usually only provide about 20% of the functionality for any command/subsystem. 

If you choose to use BTRFS, beware that it lies about disk use.  The storage commands which have been with Unix systems for 50 yrs, df and du, don't know the correct answers when btrfs is being used.  

Also, on Unix systems, temporary files are created and destroyed by processes all the file.  The alarm might have been triggered just before one was deleted.
Also, out-of-storage conditions often alert based on having less than 10,5, 2, 1% of the total storage available.  5% on a 4TB disk is very different from 5% on a 25G disk.  One is a huge problem and the other doesn't mean jack.

Whatever you do, never run out of storage on the OS disk partitions.   /var, /, are the most important.  It is fine if /home or /opt run out of storage, provided that those are NOT the same partitions (or LVs) as /var or /.

So, to start, let's gather some  data, in a compact, thorough form, as text.
```
df -hT
df -i
sudo du -h /

```
Please post the output using code tags like I've done above.  Things line up that way.  Otherwise, the output will be unreadable.

inodes ... if you run out of inodes, then it doesn't matter if there are 2TB free.  No inodes available means no new files (even temp) can be created.

IMHO, 90% of the power for any computer comes from the command line and automation.
If you really want the become a power user, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a start.

---

### Post by pjstock on 2018-07-13
sorry, but how do I use Code Tags for output? I did search for an answer, but don't see one that makes sense to me.
Hmm, here's something. let me try this.

```

peter@CollierDesk:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.0G     0  2.0G   0% /dev
tmpfs          tmpfs     397M   12M  385M   3% /run
/dev/sdb5      ext4       33G   29G  3.1G  91% /
tmpfs          tmpfs     2.0G   13M  2.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     397M   88K  397M   1% /run/user/1000
/dev/sdd1      fuseblk   932G  247G  686G  27% /media/peter/WD
/dev/sdc1      fuseblk   1.9T  1.6T  254G  87% /media/peter/Seagate Expansion Drive
/dev/sda5      ext4       20G   17G  2.1G  89% /media/peter/9ee3603b-73ca-47fe-8364-5fb0925fcd20
/dev/sda2      fuseblk    51G   43G  8.3G  84% /media/peter/5ABA2917BA28F0E5
/dev/sde1      vfat       15G   13G  1.9G  88% /media/peter/3429-E77A

```

```

peter@CollierDesk:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev              204948    589    204359    1% /dev
tmpfs             214459    854    213605    1% /run
/dev/sdb5        2203648 688847   1514801   32% /
tmpfs             214459     63    214396    1% /dev/shm
tmpfs             214459      6    214453    1% /run/lock
tmpfs             214459     18    214441    1% /sys/fs/cgroup
cgmfs             214459     14    214445    1% /run/cgmanager/fs
tmpfs             214459     38    214421    1% /run/user/1000
/dev/sdd1      718601584  10651 718590933    1% /media/peter/WD
/dev/sdc1       67428237 912303  66515934    2% /media/peter/Seagate Expansion Drive
/dev/sda5        1299984 617270    682714   48% /media/peter/9ee3603b-73ca-47fe-8364-5fb0925fcd20
/dev/sda2        8924056 180053   8744003    3% /media/peter/5ABA2917BA28F0E5
/dev/sde1              0      0         0     - /media/peter/3429-E77A
peter@CollierDesk:~$ ^C

```

then do you really want sudo du -h / ?
It seems to generate a HUGE amount of lines in response. (it's still running several minutes later.

---

### Post by TheFu on 2018-07-13
I don't see any issues, inodes are fine, / has 3.1G available, so you should watch / carefully, especially before patching.

Basically, don't let /var, /boot or / fill up. Really want at least 1G available to avoid big issues.  When a Unix OS partition gets over 95% full, it does slow things down and leads to fragmentation.  90% or less full is much better for performance on smaller partitions.

I'd move /home/ to a different disk, if you don't want to watch / closely.  That would effectively solve the problem.  It might not be an issue at all, ever. Just depends on use  patterns.

```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb5      ext4       33G   29G  3.1G  91% /
```

If it isn't clear, the tmpfs and control group stuff can be ignored.  
External disks mounted outside the core OS directories don't matter at all for how well the OS runs. Fill those up as much as you like.  Same for /home, provided it uses a different partition than any of the critical areas mentioned above.

The fuseblk mounts are terribly slow.  For flash drives, that probably is so much more convenient to make sense.  I guess if they are NTFS or FAT-whatever, there isn't much choice.

Does this help?

---

### Post by pjstock on 2018-07-13
Very helpful, thank you. 
and beyond the warning I got that prompted this post/question, I shoudl have added that my system does bog down to a near crawl after a day or two Live!. I have to reboot the system to get it functioning smoothly again. And that lasts for about a day.
(while I should probably post that question seperately , I'll just note that I am running . Ubuntu 16.04 with 4Gb RAM on a 32 bit Intel® Pentium(R) Dual CPU E2200 @ 2.20GHz × 2 )

but otherwise, when you suggest:  "I'd move /home/ to a different disk,"
Just MOVE it (/home) ?
Or are there precautions I need to take (like who knows? maybe something in the OS is in there and won't function if I just brute force "move" it.)

---

### Post by col48 on 2018-07-13
Many experts advocate having /home in its own partition - like having a disk within a disk - or on a separate medium.  (But an external HD _*may*_ be slower than your main HD).

The fact that this means a clean install of the OS can then be done on the partition containing the OS (/) without affecting your data (one of the reasons for doing this) does show that 
```
maybe something in the OS is in there and won't function if I just brute force "move" it.) 
```
is not a concern.

Nevertheless, I would advocate backing up both source HD and destination HD before making the move.  There might be a power cut, for instance!

---

### Post by oldfred on 2018-07-13
I agree with TheFu, as usual, that graphical tools just do not tell a correct story.

I prefer for du, to start with one level first. Then drill down from that on anything that looks too large.
sudo du -hc --max-depth=1

Are you housecleaning?
       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

 Caution deborphan will delete anything you manually installed. See comment: 

Are you regularly running chkdsk & defrag on your NTFS partitions. You can only do that from Windows or a Windows repair disk. And NTFS really likes 30% free. At 10% free it gets very slow even in Windows and the Linux NTFS driver often is somewhat slow with NTFS anyway.

---

### Post by TheFu on 2018-07-13
First, if you aren't 100% certain, make a know-I-can-recover-backup, because when things go wrong doing these things, sometimes they go really,really, wrong and all data is wiped.

There's a guide for moving /home. Let's see if google finds it ("ubuntu home move") - yep. 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Make certain that after the move, everything looks just like it did before, at the file system level.  Unix is dumb for almost everything.  If stuff appears to be in the correct place, that is fine.

You can move **any** real directory onto a different disk in the same way.  When you are all done, if the data appears in the correct place, with the correct permissions, everything will be fine.  A "mount point" is just a directory, usually empty.  So, you can mount extra storage pretty much anywhere a directory exists. If HOME is on a slow disk, it will feel slow, so best to make that a SATA or eSATA connection. USB will always be slower.

Lastly, /home isn't anything magical. You can place a HOME directory pretty much anywhere you like, provided the permissions are correct, the password entry points at it and it is, or will become, available as needed.  In many commercial environments, HOME directories are NFS mounts and password entries are provided by LDAP.

---

### Post by VMC on 2018-07-13
Peter, Try this so we might find a pulprit or two eating your disk space:```
sudo du -ahx / | sort -rh | head -20
```

---

### Post by pjstock on 2018-10-05
I'm afraid I am Back. and am even more confused than before.
I was muddling along without having moved /home keeping free space at about 1GB
But I seem to have really chewed up my disk space now. I am getting a warning that I am down to 112MB or so. (earlier it was 0mb but I was able to find a few useless files to quickly delete so at least I could run the system)
the only thing I changed as that I put a very large (358MB) audio recording MP3 file (a recording of a long long lecture) on an external drive, but each time I try to open it for editing in Audacity, my disk space plunges to Zero and everything shuts down.
I expect Audacity is trying to open a temporary file or something that that is killing my free space, at least temporarily, but long enough to foul everything up.

so I am just trying to fight back to a functioning system. 
How do I find where space is being wasted? 
How do I find big or useless files to delete?

and even before all this, I found that I have to reboot my system daily in order to have it function reasonably, without bogging down to dead slow or freezing up completely. I am getting reeeealy fed up. If my system is just underpowered, then I will march out tomorrow and get a new box. But I thought Ubuntu was supposed to run pretty lean and I thought this setup - for my relatively simple needs - should have been sufficient. (System specs are attached as a photo).

I expect you are going to ask for this output: (let me see if I get these Code Tags right. I doubt I will.)

```
peter@CollierDesk:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.0G     0  2.0G   0% /dev
tmpfs          tmpfs     397M  6.6M  390M   2% /run
/dev/sdb5      ext4       33G   32G  132M 100% /
tmpfs          tmpfs     2.0G  5.1M  2.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     397M   60K  397M   1% /run/user/1000
/dev/sdd1      vfat       15G  8.5G  6.1G  59% /media/peter/3429-E77A
/dev/sde1      fuseblk   932G  246G  686G  27% /media/peter/WD
/dev/sdc1      fuseblk   1.9T  1.6T  231G  88% /media/peter/Seagate Expansion Drive

peter@CollierDesk:~$ df -hTi
Filesystem     Type     Inodes IUsed IFree IUse% Mounted on
udev           devtmpfs   200K   589  200K    1% /dev
tmpfs          tmpfs      210K   849  209K    1% /run
/dev/sdb5      ext4       2.2M  744K  1.4M   35% /
tmpfs          tmpfs      210K    56  210K    1% /dev/shm
tmpfs          tmpfs      210K     6  210K    1% /run/lock
tmpfs          tmpfs      210K    18  210K    1% /sys/fs/cgroup
cgmfs          tmpfs      210K    14  210K    1% /run/cgmanager/fs
tmpfs          tmpfs      210K    31  210K    1% /run/user/1000
/dev/sdd1      vfat          0     0     0     - /media/peter/3429-E77A
/dev/sde1      fuseblk    686M   11K  686M    1% /media/peter/WD
/dev/sdc1      fuseblk     59M  909K   58M    2% /media/peter/Seagate Expansion Drive
peter@CollierDesk:~$ ^C

```

can anyone guide me here?

---

### Post by TheFu on 2018-10-05
Ubuntu is lean, but you can't remove all the available storage and expect **any** OS to keep working.
Ubuntu fits in 10GB, so everything else are files you've decided are important. Reprioritize.
You have over 3TB, so free up 30G on /.

Commands already in this thread will help you find space, but most of it is likely in your HOME.
I'm assuming you are cleaning up old kernels and old installed packages.

---

### Post by pjstock on 2018-10-08
I found 9GB tied up as it seems thumbnail images of my photo editing / management app, Picasa. I don't think they serve a purpose so I just deleted them.
and I am now removing old kernels and packages.
Thank you.

though I would still like to know why this system runs like molasses unless I reboot it every morning.

---

### Post by dragonfly41 on 2018-10-08
> [COLOR=#000000]I'll just note that I am running . Ubuntu 16.04 with [/COLOR][COLOR=#ff0000]4Gb RAM[/COLOR][COLOR=#000000] on a [/COLOR][COLOR=#ff0000]32 bit[/COLOR][COLOR=#000000] Intel® Pentium(R) Dual CPU E2200 @ 2.20GHz × 2[/COLOR]

[COLOR=#000000]> I would still like to know why this system runs like molasses unless I reboot it every morning.[/COLOR]

I would also look at System Tools > System Monitor > Processes to inspect how much RAM is in use by various processes (including multiple browser tabs which is a hog).
If there is very heavy RAM usage your system might well run slow.
Either keep running processes lean in your workflow and/or invest in more RAM (perhaps go for double your RAM size).

[COLOR=#b22222][Added note][/COLOR]
I was curious to search to see if your cpu is 32bit or 64bit.

[https://www.quora.com/Is-the-Dual-Core-E2200-a-64-bit-processor-or-a-32-bit-processor](https://www.quora.com/Is-the-Dual-Core-E2200-a-64-bit-processor-or-a-32-bit-processor)

You might gain performance improvement by installing 64bit Ubuntu. 
Why not try running a 64bit LiveUSB to test this?

---

### Post by pjstock on 2018-10-08
INteresting. When I checked Resource usage just before rebooting, my system was at 73% of RAM (of 4GB)
On reboot it is at first 48% and now 55% (though I expect as i "do" stuff that number will rise, til it all bogs down and I have to reboot again.)
so, maybe more RAM.
thanks

---

### Post by oldfred on 2018-10-08
If you have 4GB of RAM, that should not be the issue. Unless editing videos or have many tabs & other programs open all at once.

       Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Difference between Details screen on RAM and free command
[http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649](http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649)
[https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221](https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221)

---

### Post by pjstock on 2018-10-09
[COLOR=#b22222][Added note][/COLOR]
I was curious to search to see if your cpu is 32bit or 64bit.
[https://www.quora.com/Is-the-Dual-Core-E2200-a-64-bit-processor-or-a-32-bit-processor](https://www.quora.com/Is-the-Dual-Core-E2200-a-64-bit-processor-or-a-32-bit-processor)

Hmmm, that's interesting. I just followed the prompts when I originally installed this OS. I assumed that it just matched my CP\U.
but I will try the 64-bit Live version and see if it works better.
thanks

---

