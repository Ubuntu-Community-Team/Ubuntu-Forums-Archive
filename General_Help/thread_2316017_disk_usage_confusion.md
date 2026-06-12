---
title: "disk usage confusion"
date: 2016-03-04
forum: General Help
---

### Post by pjstock on 2016-03-04
I know I should learn to better understand the nuances of disk usage, but for the moment I can only approach it as an intrepid novice and I am finding it maddening.

I am frequently getting Low Disk warnings. 
and all I can do is dive into the usual suspects (usually .Cache > Deja Dups which seems to have something to do with backups...) and delete what seems unnecessary.

This morning though I am stumped.

I got a message saying: "This computer has only 704MB disk space remaining"
but I cannot figure out where that Low Space is happening.

When I examine each drive (and I can only so far do it by doing RightClick > Properties) they all seem to have at least a couple of Gb free.
So here is this 704Mb bottleneck happening?

And when I look at Disk Analyser (attached) it seems to show my "home" folder at 7.2Gb but when I do Properties on (what I think is) the Home folder, I only see 1.9Gb used.
I must be confusing some locations.

Where do I start to unravel this ?
And is there a 101 tutorial somewhere where I could better learn the basics of disk management so I wouldn't feel so helpless?

---

### Post by pfeiffep on 2016-03-04
Possibly using the command line might be helpful in this case ... df will display on your system
> Filesystem     1K-blocks     Used Available Use% Mounted on

---

### Post by pjstock on 2016-03-04
Sorry, Yes, I should know that serious Ubuntu people don't use pictures.....

so, like this:
```
peter@Peter-Desk:~$ df
Filesystem      1K-blocks       Used Available Use% Mounted on
udev              2023464          4   2023460   1% /dev
tmpfs              406648       1512    405136   1% /run
/dev/sda5        20333824   16498972   2778904  86% /
none                    4          0         4   0% /sys/fs/cgroup
none                 5120          0      5120   0% /run/lock
none              2033220      19164   2014056   1% /run/shm
none               102400         56    102344   1% /run/user
/dev/sdd1       488384000  300888940 187495060  62% /media/peter/New Volume
/dev/sde2        19481808   12496416   6985392  65% /media/peter/PETER'S IPO
/dev/sdc1      1953506384 1162479724 791026660  60% /media/peter/Seagate Expansion Drive
/dev/sdb1       204781552  165874296  38907256  82% /media/peter/Internal 250GB
/dev/sda2        53143300   40541820  12601480  77% /media/peter/5ABA2917BA28F0E5
/dev/sdb5        34561752   27665892   5117172  85% /media/peter/40840a5b-68f1-48bd-86e6-12b36db49041
peter@Peter-Desk:~$
```

though that is hard to read.
is this any clearer? (attached)[ATTACH=CONFIG]267643[/ATTACH]

---

### Post by howefield on 2016-03-04
Appears to be a fairly small disk especially if /home is on the same partition or disk as /.

Probably would help to clear out the history/cache from Chrome and Firefox and possibly clear out some old packages

```
sudo apt-get clean
```
```
sudo apt-get autoremove
```

---

### Post by pjstock on 2016-03-04
thank you.
I ran those commands earlier this week.
and when I run them now, there seems no change when I run df again.

So, should I move /home from /?
(and - at the risk of sounding wildly ignorant - what is the difference betwen /home and / ?)

---

### Post by oldos2er on 2016-03-04
> **pjstock said:**
> Sorry, Yes, I should know that serious Ubuntu people don't use pictures.....

Pictures are fine; or you could use *df -h* to make the output of your command a bit easier to understand.

---

### Post by pjstock on 2016-03-04
```
peter@Peter-Desk:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           398M  1.5M  396M   1% /run
/dev/sda5        20G   16G  2.7G  86% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   23M  2.0G   2% /run/shm
none            100M   56K  100M   1% /run/user
/dev/sdd1       466G  287G  179G  62% /media/peter/New Volume
/dev/sde2        19G   12G  6.7G  65% /media/peter/PETER'S IPO
/dev/sdc1       1.9T  1.1T  755G  60% /media/peter/Seagate Expansion Drive
/dev/sdb1       196G  159G   38G  82% /media/peter/Internal 250GB
/dev/sda2        51G   39G   13G  77% /media/peter/5ABA2917BA28F0E5
/dev/sdb5        33G   27G  4.9G  85% /media/peter/40840a5b-68f1-48bd-86e6-12b36db49041
```

---

### Post by howefield on 2016-03-04
/ is the basically the root of your file system.. the beginning, everything branches off from there.

/home is a folder that all your user documents and files are stored.  

All I am saying is that you appear to have a fairly small partition for all the system files and all the user files, so you are likely to continue having this issue.

Did you clear out the browser caches, there is about a gig and a half in there ?

Also, for information it is best to enclose your terminal output in code tags as I have done for you above, [ code][ /code] - without the spaces :) See the difference ?

---

### Post by pjstock on 2016-03-04
Ahh, yes, I see.

I think I have now cleared my browser caches.
where would I see that 1.5gb you say were showing in there (or if it is now cleared) ? In Disk Analyser or using the df command?

---

### Post by howefield on 2016-03-04
> **pjstock said:**
> where would I see that 1.5gb you say were showing in there (or if it is now cleared) ? In Disk Analyser or using the df command?

Either of the above, comparing what you have posted already with what you now get.

Slightly unnecessary sidenote : a disk usage analyser that I favour is ncdu - a command line tool but easy to navigate, quick and easy on resources.

```
ncdu 1.11 ~ Use the arrow keys to navigate, press ? for help                                                                                
--- / --------------------------------------------------------------------------------------------------------------------------------------
.   6.1 GiB [##########] /Data                                                                                                              
.   4.1 GiB [######    ] /usr
. 670.9 MiB [#         ] /var
  389.8 MiB [          ] /lib
   48.4 MiB [          ] /boot
   27.8 MiB [          ] /opt
.  15.3 MiB [          ] /etc
   12.8 MiB [          ] /sbin
.  12.6 MiB [          ] /bin
.   8.7 MiB [          ] /run
    7.7 MiB [          ] /home
    3.6 MiB [          ] /lib32
  492.0 KiB [          ] /dev
. 212.0 KiB [          ] /tmp
!  16.0 KiB [          ] /lost+found
    8.0 KiB [          ] /media
    4.0 KiB [          ] /lib64
e   4.0 KiB [          ] /srv
!   4.0 KiB [          ] /root
e   4.0 KiB [          ] /mnt
e   4.0 KiB [          ] /cdrom
!   4.0 KiB [          ] /Desktop
!   4.0 KiB [          ] /.gnome-desktop
.   0.0   B [          ] /proc
.   0.0   B [          ] /sys
@   0.0   B [          ]  initrd.img
@   0.0   B [          ]  vmlinuz

 Total disk usage:  11.3 GiB  Apparent size:  11.3 GiB  Items: 395119
```

---

### Post by pjstock on 2016-03-04
I don't think I got that code /code thing right.
do I remove the square brackets?

No I think I just follow you instructions "without the spaces"

```

--- /home/peter -----------------------------------------------------------------------------------------------
    2.3GiB [##########] /.cache                                                                                
    1.2GiB [#####     ] /dvdrip-data
    1.2GiB [#####     ] /.google
  932.7MiB [####      ] /.thunderbird
  409.8MiB [#         ] /.wine
  403.2MiB [#         ] /.config
  395.7MiB [#         ] /Downloads
  149.5MiB [          ] /.local
   61.0MiB [          ] /.mozilla
   55.9MiB [          ] /Desktop
   49.3MiB [          ] /.recoll
   21.5MiB [          ] /Pictures


```

---

### Post by howefield on 2016-03-04
Doesn't look like you cleared browser history ect from chrome. 

Might also be worth clearing history from Thunderbird > Tools > Clear Recent History.

A lot of space eaten up by .cache and dvdrip-data that you could look at.

You can navigate around using the arrow keys to cursor down and highlight a line and press enter to see the file sizes inside. 

The # signs just show the relative size of the file or folder, not a huge deal.

---

### Post by gordintoronto on 2016-03-05
Have you tried removing old versions of the kernel? I find the easiest way to do that is to install Synaptic Package Manager, then search for, for example, (for 15.10) 4.2.0-25

Three or four files should show up as installed, and I can "completely remove" them to free up space. Repeat for older kernel versions. Generally, keep at least the two latest versions.

After removing kernels, run this command: sudo update-grub

This will also display what kernels you have installed.

If you have a boot partition, this can have a dramatic effect.

Oh shucks, I just followed my own advice and freed up 2 GB.

---

