---
title: "e2fsprogs is installed but not found"
date: 2016-09-17
forum: General Help
---

### Post by ineuw on 2016-09-17
Using Xubuntu 16.04 the **e2fsprogs** app was installed as it was supposed to be, and reinstalled with synaptic, hoping to get lucky, but it's dead in the water not unlike the Bismark battleship. Typing in the terminal e2fsprogs with or without sudo, makes no difference. I get **e2fsprogs: command not found** I have no idea what I am doing wrong. These are the list of files found by the locate command.

-rw-r--r-- 1 root root   299 Apr 20 18:09 e2fslibs:i386.list
-rw-r--r-- 1 root root   281 Oct 30  2015 e2fslibs:i386.md5sums
-rw-r--r-- 1 root root    39 Oct 30  2015 e2fslibs:i386.shlibs
-rw-r--r-- 1 root root 19454 Oct 30  2015 e2fslibs:i386.symbols
-rw-r--r-- 1 root root    60 Oct 30  2015 e2fslibs:i386.triggers
-rw-r--r-- 1 root root    17 Oct 30  2015 e2fsprogs.conffiles
-rw-r--r-- 1 root root  3387 Sep 17 20:19 e2fsprogs.list
-rw-r--r-- 1 root root  3672 Oct 30  2015 e2fsprogs.md5sums
-rwxr-xr-x 1 root root   259 Oct 30  2015 e2fsprogs.preinst

---

### Post by steeldriver on 2016-09-17
What exactly are you trying to do? 

e2fsprogs is a *package* that provides various commands (such as `e2fsck` and `tune2fs`) - afaik there's no single command called `e2fsprogs`

---

### Post by ineuw on 2016-09-17
steeldriver, I wanted to use their defragment tool 'e2defrag': but I got **command not found**. Just attempted to use 'e2fsck -vc' and got nothing but the options menu. So, now I see that the package is installed, ecept the the defrag component 'e2defrag' is missing?

---

### Post by steeldriver on 2016-09-17
There appears to be an `e4defrag` command - is that perhaps what you're looking for?

[http://packages.ubuntu.com/xenial/amd64/e2fsprogs/filelist](http://packages.ubuntu.com/xenial/amd64/e2fsprogs/filelist)

---

### Post by ineuw on 2016-09-17
steeldriver, my thanks for your help. 'e4defrag' is for 64 bit systems, but found the 32bit as well, named  'e2freefrag'.

---

### Post by DuckHook on 2016-09-17
At the risk of sticking my nose in where not needed (or wanted), why do you wish to defrag?

---

### Post by ineuw on 2016-09-17
I have no problem with your asking and the answer is: curiosity and learn more about what reliable software is available for Xubuntu. - To allay your concerns, as things currently stand, configuring it in the terminal is a bit above my pay grade. I am not willing to spend time to learn it because I would like to do some more important things. :-)

---

### Post by DuckHook on 2016-09-17
> **ineuw said:**
> …the answer is: curiosity and learn more about what reliable software is available for Xubuntu.Ah. You are obviously a bear after my own heart.> …configuring it in the terminal is a bit above my pay gradeActually, it is terribly simple to use, and made all the more so by the fact that it is rarely needed in Linux. The ext4 filesystem is exceedingly robust and resistant to fragmentation. The only time you need to worry about fragmentation is if you routinely fill a partition close to its max capacity, or you torrent. torrent files are notorious for causing fragmentation.

You can check to see if a HDD needs defragging with a command of the form (for 64-bit):```
sudo e4defrag -c /dev/sda1
```…replacing the name of the device partition as appropriate. This will return a simple report stating amount of fragmentation and recommending whether defrag is necessary or not. To actually defrag, just run the same command without the -c flag. As already said, terribly simple.

Good Luck and Happy Ubuntu-ing!

---

### Post by ineuw on 2016-09-17
Thanks for the command. You will laugh when I tell you that Xu 16.04 is installed on its own 100GB partiton of which it uses about 6 GB the rest is empty. Then, there is another 100 GB of an ext4 partition set aside for data, backup, and archiving. I overbought drive capacity. 1 SSD for booting Window 7 Pro, 1x1TB Seagate and 1x500GB Seagate. with the combined use of less than 300GB. So everything is backed up in duplicate alternately on the drives. :-) If one dies, I am still OK.

---

### Post by DuckHook on 2016-09-17
I have similar belts & suspenders backup measures, so all the power to you. You will have to defrag your NTFS partitions regularly, but won't ever have to touch your ext4 partitions if you keep to similar good habits in the long term.

If your problem is now solved, *please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

