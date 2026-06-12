---
title: "out of space"
date: 2014-03-26
forum: General Help
---

### Post by night116 on 2014-03-26
My ubuntu 13.10 stated I had run out of room on my /dev/sdb6 so I deleted a few gig or so, it stated it was in my home dir where I kept my downloads, but it still shows up as being at 100% full. how to clear this? it shows as 32.1Gb total-658.7Mb free- 31.5Gb used at 100%
sdb5 is at 1% used
sdb7/home is at 32% used
I have tried the following
$ sudo apt-get autoclean
$ sudo apt-get autoremove 

but that only showed up as 978.1 free on sdb6

---

### Post by papibe on 2014-03-26
Hi night116.

Could you post the result of these 2 commands?
```
df -h

df -i
```
Regards.

---

### Post by night116 on 2014-03-26
```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb6        30G   30G     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.8G   12K  7.8G   1% /dev
tmpfs           1.6G  1.5M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.8G  156K  7.8G   1% /run/shm
none            100M   56K  100M   1% /run/user
overflow        1.0M 1016K  8.0K 100% /tmp
/dev/sdb7       1.3T  300G  894G  26% /home
/dev/sdb5        19G  207M   18G   2% /boot
/dev/sdg1       3.7T  2.3T  1.4T  63% /media/night/HD-LBU31

$ df -i
Filesystem        Inodes   IUsed     IFree IUse% Mounted on
/dev/sdb6        2003120  319049   1684071   16% /
none             2043207       2   2043205    1% /sys/fs/cgroup
udev             2040682     626   2040056    1% /dev
tmpfs            2043207     669   2042538    1% /run
none             2043207       3   2043204    1% /run/lock
none             2043207       7   2043200    1% /run/shm
none             2043207      29   2043178    1% /run/user
overflow         2043207      23   2043184    1% /tmp
/dev/sdb7       83738624  255656  83482968    1% /home
/dev/sdb5        1250928     289   1250639    1% /boot
/dev/sdg1      372149236 3912495 368236741    2% /media/night/HD-LBU31
```

---

### Post by papibe on 2014-03-26
Thanks.

It is not your home that is full, but your root partition.

I would start by doing this so you can have at least enough space to operate:
```
sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove
```
After that please post again this command to see how much you gain:
```
df -h
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by night116 on 2014-03-26
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb6        30G   30G     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.8G  4.0K  7.8G   1% /dev
tmpfs           1.6G  1.5M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.8G  156K  7.8G   1% /run/shm
none            100M   36K  100M   1% /run/user
overflow        1.0M  8.0K 1016K   1% /tmp
/dev/sdb7       1.2T  300G  825G  27% /home
/dev/sdb5        19G  207M   18G   2% /boot
```

---

### Post by drmrgd on 2014-03-26
Seems there's a lot more on root that is taking space and might be able to be cleared.  You can try running this command starting from the root directory:

```

sudo du -hsx * | sort -rh | head -10

```

That will show you the top 10 largest files / directories in root.  You may get a 'du: cannot access `proc/....`' error, which is fine.  Once you have that list, you can then head into that directory shown and run the command again, which will show you the largest directories / files in that sub directory.  Repeating this strategy should help you narrow down where the problem lies.  One other good place to start is /var, which often gets bloated due to inflated log files indicating another problem on the system.

---

### Post by PJs Ronin on 2014-03-26
You could use Disk Usage Analyser from Dash... command line is 'baobab'.   Gives a nice graphic representation of where space is being used.   Has saved my butt on several occasions.

---

### Post by night116 on 2014-03-26
thanks all for your help, I had no choice but to start again as it refused to do anything due to no room. lucky I had backups from every night and this time set up the OS on a sepparate HDD and home on another. only took an hour or so.

---

### Post by oldfred on 2014-03-27
> only took an hour or so. 				

Not fair, we are here to help you fix thing even if it takes days or weeks. :)
And having good backups, makes it too easy to recover.

Actually 30GB seems very large for a / when you have a separate /home. Not sure what you still had in /, but part of issue may have been root's trash which is a bit harder to empty.

---

