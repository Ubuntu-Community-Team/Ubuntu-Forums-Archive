---
title: "Problem with disk storage"
date: 2006-12-03
forum: General Help
---

### Post by soaring747 on 2006-12-03
I am using the Edgy Eft version, and here's my problem: The system is either not reporting the storage correctly after large files are deleted or there is a file that is hidden even from root that takes up too much memory

I am receiving out of storage errors and warnings from gnome and kde of my home directory being out of room. (This is actually quite a miracle feature of Ubuntu, I would have otherwise expected disk reporting for /, I am thankful that it reports on all itss mounted devices.)

I put the /home directory on a 1.7GB separate partition so that I wouldn't lose all my personal files in the event of a system crash that would be unrecoverable even after reboot. After installing vmware-server, I downloaded  Solaris so I could see what it was like. Well, midway through download, I ran out of room. This was my mistake as I tried to download several of the files at one time.

The downloads canceled and I deleted their files. (I should mention, not sure whether it makes a difference or not, that the trash bin remained empty. I assumed that the delete was permanent and didn't go in there because of the tremendous combined files size.)

When I went to use synaptic to install flight gear, it wouldn't download. I assumed something was wrong and it was quite possibly related to the previous warnings. I therefore went to check the size of /home, which was reported to be at full capacity, all 1.7GB. I thought this to be an easily correctable error, so I attempted to move all of the contents to another folder (root/savedhome/) and then back again to let the status update itself. 

Well, the file reporting has changed to its correct size (when viewed from right click -> properties). However, I still cannot download and I still get warnings from the system that inadequate space is available on /home.

Is there a command I should run?

All the best.

---

### Post by mssever on 2006-12-03
> **soaring747 said:**
> I am using the Edgy Eft version, and here's my problem: The system is either not reporting the storage correctly after large files are deleted or there is a file that is hidden even from root that takes up too much memory

I am receiving out of storage errors and warnings from gnome and kde of my home directory being out of room. (This is actually quite a miracle feature of Ubuntu, I would have otherwise expected disk reporting for /, I am thankful that it reports on all itss mounted devices.)

I put the /home directory on a 1.7GB separate partition so that I wouldn't lose all my personal files in the event of a system crash that would be unrecoverable even after reboot. After installing vmware-server, I downloaded  Solaris so I could see what it was like. Well, midway through download, I ran out of room. This was my mistake as I tried to download several of the files at one time.

The downloads canceled and I deleted their files. (I should mention, not sure whether it makes a difference or not, that the trash bin remained empty. I assumed that the delete was permanent and didn't go in there because of the tremendous combined files size.)

When I went to use synaptic to install flight gear, it wouldn't download. I assumed something was wrong and it was quite possibly related to the previous warnings. I therefore went to check the size of /home, which was reported to be at full capacity, all 1.7GB. I thought this to be an easily correctable error, so I attempted to move all of the contents to another folder (root/savedhome/) and then back again to let the status update itself. 

Well, the file reporting has changed to its correct size (when viewed from right click -> properties). However, I still cannot download and I still get warnings from the system that inadequate space is available on /home.

Is there a command I should run?

All the best.
The way I would approach this problem would be to run du -h on different folders until you found the cuplrit. And be sure to include hidden files/folders (their names begin with a dot) as well, as that's likely where the bloat is hidden.

I would do it this way:
cd to the root level of the partition and do ls -Al. Look for anything that's hogging space. Then, for each directory, do du -h directory_name. If it seems to be too big, cd to that directory and repeat the above steps. You should be able to find the trouble with a little time and patience.

---

### Post by dmartinsca on 2006-12-03
I have Disk Usage Analyzer under Applications > Accessories. I can't remember installing this program, so maybe it's installed by default? If so it provides an simple graphical way to see what file/directories are hogging the space.

If that's not installed, I would pick a partition to try to clean up, open a terminal, and change to it's mount point. I'll show an example using my root partition..

```
dmartins@dmartins-laptop:/$ cd /
dmartins@dmartins-laptop:/$ sudo du -x --max-depth=1 | sort -g | column -t
0        ./dev
0        ./proc
0        ./sys
4        ./home
4        ./initrd
4        ./srv
8        ./mnt
48       ./lost+found
52       ./media
288      ./tmp
3028     ./root
4944     ./bin
6444     ./sbin
8256     ./boot
10320    ./opt
12492    ./etc
92660    ./lib
500128   ./var
2346556  ./usr
2985240  .
```
This lists the size of all the directories & does not count file on different partitions (like your home partition). The directories are listed from top to bottom, smallest to largest in kilobytes. I'd like to get a closer look at /usr so i switch to that directory and run the same command again. You can scroll through previously entered commands by using the up/down arrows to save yourself some typing.
```
dmartins@dmartins-laptop:/$ cd /usr
dmartins@dmartins-laptop:/usr$ sudo du -x --max-depth=1 | sort -g | column -t
16       ./usr
28       ./X11R6
168      ./local
224      ./m68hc11
6684     ./sbin
7780     ./games
17228    ./include
82596    ./src
112096   ./bin
918392   ./lib
1201340  ./share
2346556  .
```
Just repeat this process till you find where your space has gone. Chances are, if your root partition is full there are lots of package files stored in /var/cache/apt/archives which can be removed. Run ls -lh as required to list individual files in that directory.

---

### Post by soaring747 on 2006-12-04
Ah ha! I was absolutely right! It turns none of the files were ever deleted!

All the space was being consumed in .local/share/Trash/files

Thanks bunches. :)

---

