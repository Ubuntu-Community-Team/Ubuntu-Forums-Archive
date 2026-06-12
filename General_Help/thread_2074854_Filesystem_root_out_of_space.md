---
title: "Filesystem root out of space"
date: 2012-10-21
forum: General Help
---

### Post by jpc2769 on 2012-10-21
My root partition is running out of space as well, it is 10G. How do I find and delete stuff to clear up room?

Not only is my partition completely full, I can't remove packages I don't need because there is no space. Can anyone help, or am I up s- creek without a paddle?

So my /usr folder is 5.2 Gig, and has a subdirectory /usr/bin, which has 2,104 items. The first item in /bin is a folder called /X11, which also has 2,104 items. In /X11 is a copy of all the files in /bin, as well as another subfolder (/usr/bin/X11/X11) which also has 2,104 items, all the same as /usr/bin! This repeats ad nauseum. Is this normal? Can I delete any of this stuff to make some room?

Jason

---

### Post by howefield on 2012-10-22
Post moved to it's own thread.

Please do not from hijacking other posters threads.

---

### Post by *^kyfds( on 2012-10-22
How much space would you say is taken up by your software?

---

### Post by drmrgd on 2012-10-22
Aside from the usual suspects - making sure the trash is empty, clearing up old log files in /var/log, etc - I like to run this command to list the top 10 directories by size:

```
du -hsx * | sort -rh | head -10
```

Run this from root, home, where ever, and it'll tell you the 10 largest directories that you have on you system, which will help narrow things down.  

Also, you're probably about to get 10 responses all saying to use Bleach Bit to clean your system up. Although I've never used it myself, I guess you can consider this #1.

---

### Post by spjackson on 2012-10-22
What you are seeing with X11 is normal. There is a symbolic link in /usr/bin/X11 which points to its parent directory. This does not take up any space, although it does look confusing in the GUI.

With one exception, /usr does not normally get filled up with useless files - unless you install a lot of packages you do not want or need. The exception is that if you get lots of kernel updates, you can accumulate lots of kernel headers in /usr/src. In that case, you can safely remove old kernel headers via synaptic (or other package manager).

As for other actions that can be performed, we really need some more information about your setup. Can you please run the following commands in a terminal and post the output?
```

df -h
df -i

```

---

### Post by Cheesemill on 2012-10-22
> **jpc2769 said:**
> So my /usr folder is 5.2 Gig, and has a subdirectory /usr/bin, which has 2,104 items. The first item in /bin is a folder called /X11, which also has 2,104 items. In /X11 is a copy of all the files in /bin, as well as another subfolder (/usr/bin/X11/X11) which also has 2,104 items, all the same as /usr/bin! This repeats ad nauseum. Is this normal? Can I delete any of this stuff to make some room?

You only have one copy of those 2,104 files. The X11 folder is just a symlink to the /usr/bin folder.

To find out what directories are taking up the most room you can do:
```
sudo du -h --max-depth=1 | sort -hr
```

Just cd to / and then run the command, it will list the size of all of the directories in / sorted largest first. You can then drill down into your directories to find out where your space has gone.

Post back the results if you are unsure.

---

### Post by jpc2769 on 2012-10-25
> **spjackson said:**
> ...With one exception, /usr does not normally get filled up with useless files - unless you install a lot of packages you do not want or need. The exception is that if you get lots of kernel updates, you can accumulate lots of kernel headers in /usr/src. In that case, you can safely remove old kernel headers via synaptic (or other package manager).

Thanks, removing old kernel headers freed up about a gigabyte.

BleachBit freed up another 100MB

> As for other actions that can be performed, we really need some more information about your setup. Can you please run the following commands in a terminal and post the output?
```

df -h
df -i

```

Here they are:

```


jason@jason-ThinkPad-X230-Tablet:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7       9.2G  7.6G  1.2G  87% /
udev            3.8G   12K  3.8G   1% /dev
tmpfs           1.6G  944K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G 1020K  3.8G   1% /run/shm
/dev/sda5       462M   44M  395M  10% /boot
/dev/sda8       198G   63G  126G  34% /home
/dev/sda1       1.5G  769M  732M  52% /media/SYSTEM_DRV
/dev/sda2        71G   43G   29G  61% /media/Windows7_OS
jason@jason-ThinkPad-X230-Tablet:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda7        610800 326281   284519   54% /
udev             983929    564   983365    1% /dev
tmpfs            986986    506   986480    1% /run
none             986986      1   986985    1% /run/lock
none             986986     12   986974    1% /run/shm
/dev/sda5        122400    232   122168    1% /boot
/dev/sda8      13156352  50214 13106138    1% /home
/dev/sda1        814712   6240   808472    1% /media/SYSTEM_DRV
/dev/sda2      29677744 109100 29568644    1% /media/Windows7_OS

```

Jason

---

### Post by jpc2769 on 2012-10-25
> **Cheesemill said:**
> You only have one copy of those 2,104 files. The X11 folder is just a symlink to the /usr/bin folder.

To find out what directories are taking up the most room you can do:
```
sudo du -h --max-depth=1 | sort -hr
```

Just cd to / and then run the command, it will list the size of all of the directories in / sorted largest first. You can then drill down into your directories to find out where your space has gone.

Post back the results if you are unsure.

This is what I get:
```


du: cannot access `./proc/4165/task/4165/ns/net': No such file or directory
du: cannot access `./proc/4165/task/4165/ns/uts': No such file or directory
du: cannot access `./proc/4165/task/4165/ns/ipc': No such file or directory
du: cannot access `./proc/4165/ns/net': No such file or directory
du: cannot access `./proc/4165/ns/uts': No such file or directory
du: cannot access `./proc/4165/ns/ipc': No such file or directory
du: cannot access `./proc/17671/task/17671/fd/4': No such file or directory
du: cannot access `./proc/17671/task/17671/fdinfo/4': No such file or directory
du: cannot access `./proc/17671/fd/4': No such file or directory
du: cannot access `./proc/17671/fdinfo/4': No such file or directory
113G    .
63G     ./home
44G     ./media
5.4G    ./usr
1002M   ./var
219M    ./lib
172M    ./opt
33M     ./boot
14M     ./etc
8.8M    ./bin
8.7M    ./sbin
3.4M    ./lib32
1.4M    ./run
268K    ./tmp
84K     ./root
16K     ./lost+found
16K     ./.kde
12K     ./dev
8.0K    ./.config
4.0K    ./srv
4.0K    ./selinux
4.0K    ./mnt
4.0K    ./lib64
4.0K    ./cdrom
0       ./sys
0       ./proc

```

./home and ./media are different partitions; ./usr seems to be the main culprit. What can I safely get rid of from there?

Jason

---

### Post by spjackson on 2012-10-25
I doubt that there's much more you can to do to /usr unless you have installed a lot of software you don't use or need. I certainly have many packages that I've installed, tried for a while and never touched again.

You can probably shave something off /var.

```

sudo apt-get clean

```
will tidy up /var/cache/apt/

Another thing to look at might be /var/log/

---

### Post by drmrgd on 2012-10-25
As spjackson says, there's not much you can do without removing packages that you don't need / want.  The first time I installed Ubuntu, I was following some advice saying to make root about 10GB.  I quickly found out that after a few months of working and installing packages, I had filled it just as you did.  So, now, I personally think that 10GB is a little too lean for root.  Again, that's based on my usage, which doesn't seem too different from yours.

---

