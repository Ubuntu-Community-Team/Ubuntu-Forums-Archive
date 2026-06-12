---
title: "No space on my root drive"
date: 2017-06-12
forum: General Help
---

### Post by jkonrad on 2017-06-12
My simple home server running on 16.04 has stopped working. It believes it is out of space on the "/" partition. However, it should have lots of space. To make it more confusing, I am getting different reports from different commands to check for use. Here is a result of dh -h

```
Filesystem      Size  Used Avail Use% Mounted on
udev            2.8G     0  2.8G   0% /dev
tmpfs           577M   62M  515M  11% /run
/dev/sda1       141G   42G   93G  32% /
tmpfs           2.9G   24K  2.9G   1% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           2.9G     0  2.9G   0% /sys/fs/cgroup
/dev/sdb        2.7T  1.2T  1.5T  46% /media/external3tb_bay01
/dev/sdd1       1.8T  289G  1.5T  17% /media/external2tb_bay03
/dev/sdc1       1.8T  289G  1.5T  17% /media/external2tb_bay02
/dev/sde1       917G   35G  836G   4% /media/external1tb_bay04
tmpfs           100K     0  100K   0% /run/lxcfs/controllers
none            4.0M     0  4.0M   0% /var/spool/greyhole/mem
tmpfs           577M     0  577M   0% /run/user/1000

```

You should notice that my /dev/sda1 has lots of room. That is where "/" is mounted. But then here is the result of df -i
```
Filesystem        Inodes   IUsed     IFree IUse% Mounted on
udev              732890     576    732314    1% /dev
tmpfs             737733    1574    736159    1% /run
/dev/sda1        9388032 9388032         0  100% /
tmpfs             737733       7    737726    1% /dev/shm
tmpfs             737733       4    737729    1% /run/lock
tmpfs             737733      16    737717    1% /sys/fs/cgroup
/dev/sdb       183148544  555896 182592648    1% /media/external3tb_bay01
/dev/sdd1      122101760  266300 121835460    1% /media/external2tb_bay03
/dev/sdc1      122101760  265726 121836034    1% /media/external2tb_bay02
/dev/sde1       61054976  157438  60897538    1% /media/external1tb_bay04
tmpfs             737733      12    737721    1% /run/lxcfs/controllers
none              737733       1    737732    1% /var/spool/greyhole/mem
tmpfs             737733       4    737729    1% /run/user/1000

```

I am not sure where to begin. I do not spend enough time on this box to really know how to trouble shoot on the command line. Any help?

[Edit]
I have learned that this is an inode problem. However, I still do not know how this has happened. Is there a way to find lots of files I can delete?

---

### Post by Bashing-om on 2017-06-12
jkonrad; Hey .

'ncdu' is handy for finding what's using space .
```

sudo apt install ncdu

```
 run from terminal .

[INDENT][INDENT]right tool for the right job
[/INDENT][/INDENT]

---

### Post by shridhar-kapshikar on 2017-06-12
[COLOR=#242729][FONT=Arial]The wonderful [/FONT][/COLOR]ncdu[COLOR=#242729][FONT=Arial] program provides the graphical output in the CLI and works perfectly, 
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
Also, you can check for deleted files with ```
[/FONT][/COLOR]lsof | grep -i deleted[COLOR=#242729][FONT=Arial]
```[/FONT][/COLOR][COLOR=#242729][FONT=Arial] .Then you can see if a process is hanging on to an inode that you think was deleted. If so, restart the parent process to release the old (deleted) file. [/FONT][/COLOR]

---

### Post by jkonrad on 2017-06-12
Ok. I found a few files I could delete. That gave me enough space to install ncdu, though I think it was already in place. Anyway, it is working away finding files. Hopefully it will find folders of cache type files.

Anyway to just remove all cache and temp files in Ubuntu Server?

---

### Post by Bashing-om on 2017-06-12
jkonrad; Uh Huh .

> 
Anyway to just remove all cache and temp files in Ubuntu Server?


One can remove the cache and no-longer-needed-obsolete files:
```

sudo apt clean
sudo apt autoremove

```

Might get ya the operating head room .

[INDENT][INDENT]maybe not soooo yes
[/INDENT][/INDENT]

---

### Post by VMC on 2017-06-12
Your *inodes* is the problem:
   ```
[COLOR=#000000][FONT=&amp]/dev/sda1        9388032 9388032         0  100% /[/FONT][/COLOR].
```
 [B][Look here for some guidance]("https://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html").

Here's a better script:
[/B]```
sudo find . -xdev -type f | cut -d "/" -f 2 | sort | uniq -c | sort -n
```

---

### Post by jkonrad on 2017-06-13
Thanks. Trying the script now. I tried "sudo apt autoremove" and I just get

####:/var/spool/greyhole$ sudo apt autoremove
Reading package lists... Error!
E: Could not create temporary file for /var/cache/apt/pkgcache.bin - mkstemp (28: No space left on device)
E: The package lists or status file could not be parsed or opened.

There must also be a process filling up my inodes as soon as I delete items. I have deleted thousands of files now and it just creeps back up to 100%. I am tracking that down too, or trying to anyway.

---

### Post by efflandt on 2017-06-15
See what is in /tmp or if some error is generating lots of logs in /var/log that are not being rotated into compressed files and eventually deleted. Note that when you reboot, everything in /tmp is deleted.

---

### Post by jkonrad on 2017-06-17
Thank you to everyone who helped me out with this problem. I was never able to get any of the scripts to run properly. However, I was able to remove old kernel versions which gave me just enough file space to try a few more things. Eventually I used "dd" to do a byte by byte copy of the current OS drive to a larger one, then booted from a livecd (or USB in this case) and used gparted to move and resize the partition (I read that here [https://askubuntu.com/questions/78076/how-to-replace-my-disk-without-having-to-rebuild-my-ubuntu-install)]("https://askubuntu.com/questions/78076/how-to-replace-my-disk-without-having-to-rebuild-my-ubuntu-install") . Now my server can breathe again and actually run services. I suspect a package I use to clone my shares for redundancy. It spools a lot of files into /var/spool and I do not think it was cleaning up after itself properly. Anyway, thanks again for all the tips they helped!

---

### Post by Bashing-om on 2017-06-17
jkonrad; Great !

Where there is a will there is a way /

If this matter is now concluded to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

