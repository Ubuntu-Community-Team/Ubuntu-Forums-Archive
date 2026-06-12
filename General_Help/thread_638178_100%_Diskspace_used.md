---
title: "100% Diskspace used"
date: 2007-12-11
forum: General Help
---

### Post by lemonwonder on 2007-12-11
Hi.

I use Ubuntu Gusty.

I am trying to download a 300mb file.

At first it said I had not enough diskspace. So I used gParted to edit the diskspace and Ubuntu have like 3.5gb more space. I tried again and STILL the same problem.

Under "computer" i an see the windows partition, and the ubuntu partition.

I have just noticed that there is ANOTHER ubuntu partition called "filesystem" and it has boot somewhere in its properties. That has a lock next to it, and I cannot resize or move it.

Its that part that is full.

That part is named filesystem, and seems to have EXACTLY tge same stuff in as the 7.7gb file which i made bigger (was 4.Xgb)

Help plz

---

### Post by Pumalite on 2007-12-11
Post:
df -h

---

### Post by lemonwonder on 2007-12-11
lemonwonder@lemonwonder-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             3.8G  3.6G   88K 100% /
varrun                125M   96K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   56K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   34M   92M  28% /lib/modules/2.6.22-14-generic/volatile
lemonwonder@lemonwonder-desktop:~$ 


I presume u ment in terminal...

What that does not show is wot i can see in the "computer"

It shows the filesystem, but doesnt show the 4.5gb WINDOWS partition, or the 7.7gb Volume.
When I open the volume I got an XAuthorization error, now im doing it i just have to stick in password and stuff. That 1 isnt mounted... but it looks as if it has same stuff as filesystem.

---

### Post by Pumalite on 2007-12-11
You are going to find a way to give more space to sda4 (I imagine is your '/' partition)
A good size for '/' is around 10 GB. Try using Gparted Live CD to resize your partition. Or you'll have to delete stuff in /temp.

---

### Post by lemonwonder on 2007-12-11
I dnt have a gparted live cd... I have it installed... cant i use it? Its only a 20gb hd too.. volume 2 (the 7.7gb) and filesystem have exactly the same files in them, can i get rid of volume 1 or somin? Or can u use vnc to have a look at what the settings r (i have vnc port fowared)

---

### Post by Pumalite on 2007-12-11
I can tell you you have to use Gparted Live CD (to resize you have to work in an unmounted drive). The other question I can't answer for you because only you know what you have there or how is your set up.

---

### Post by raja on 2007-12-11
You cannot partition your disc with a program installed on it because the disc has to be unmounted (not active) while the partitioning is being done. You can use the Ubuntu live cd to do this too. You need more space - not necessarily in the root partition, if you create a separate home partition. 
If you have space on the windows partition, you may be able to resize and squeeze out some space. You can see [here]("http://www.psychocats.net/ubuntu/separatehome") for instructions on creating a separate home partition.

---

### Post by lemonwonder on 2007-12-11
Thanks pumalite... u helped a bit :D

Raja, thanks heaps. I understand what you saying, pumalite probably said the same thing but I did not understand. What I would like to know, is WHY there are 2 of every file.... why is there a "Filesystem" and a "Volume 2" that both have 3.7gb used, and both have the same files... surely thats a waste... that makes 5gb only valueable for 2.5gb of stuff...

---

### Post by raja on 2007-12-11
Hi,
There definitely is no duplication of files. All you have assigned to Ubuntu is one partition that is 3.8 GB in size. You can look at the disk with gpart (System->Administration->Gnome partition editor) to see what your partitions are currently - you can even try to post a screenshot of that. Or else you can post the output of ```
sudo fdisk -l /dev/sda
```

---

### Post by dcstar on 2007-12-11
[LIST=1]
[*]System-Administration-Synaptic-Settings-Preferences-Files-Delete Cached Package Files
[*]Install the "**logrotate**" package (to ensure that log files don't eat up your disk space)
[*]Install the "**pysdm**" package to allow you to mount (and use) your other partitions.
[/LIST]

That should give you some space to get a working system going.

You may also want to do a search for "separate /home partition" so you don't fill up your root partition with user files.

---

### Post by lemonwonder on 2007-12-11
[IMG]http://img80.imageshack.us/img80/217/screenshotdevsdagpartedgt6.png[/IMG]
The 2nd 1 and 3rd 1 have like... all same files.

"Disk /dev/sda: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002d0f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         865     6948081    c  W95 FAT32 (LBA)
/dev/sda2             866        1546     5470132+  83  Linux
/dev/sda3            2355        2438      674730    5  Extended
/dev/sda4   *        1547        2354     6490260   83  Linux
/dev/sda5            2385        2438      433723+  82  Linux swap / Solaris
/dev/sda6            2355        2384      240912   82  Linux swap / Solaris"

---

