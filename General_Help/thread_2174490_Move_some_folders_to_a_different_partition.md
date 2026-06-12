---
title: "Move some folders to a different partition"
date: 2013-09-14
forum: General Help
---

### Post by cpu2007 on 2013-09-14
I hope someone can help me with this as eventually I'm going to start having problems.

I have a 8gb SSD and I decided to install ubuntu on the ssd, the speed increased drastically and I love it.
THen I followed a tutorial showing how to move the /home folder to a different partition. I followed it and managed to set the home folder to the hdd (that has more space)

Now, I noticed that the space in my ssd is filling up and what I understand is that when I install programs,they get installed in the ssd.
I've installed mysql,eclipse and some other software; anyway I can move the folders containing software to the HDD?

Here's the current situation with my partitions:

```

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb2       7.2G  6.1G  685M  91% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           769M  872K  769M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G  192K  3.8G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sdb1        93M  121K   93M   1% /boot/efi
/dev/sda1       459G  155G  281G  36% /home


```

Thank you

---

### Post by CeejRab on 2013-09-14
Hi there, 

Im not sure i understand your situation perfectly, but it seems to me that youre doing a little too much modifying to the OS... No operatying system is intended to pull information from separate storage disks, so thats the fist recipe for trouble. However, i can understand your method of moving the home folder, but as for trying to move installed packages to a different storage disk is a little trickier. The OS wont know where to look for what it needs and thats going to cause technical difficulty as you mentioned. There may be methods for modifying directory paths for certain system folders, but they arent tested and proven yet and could cause you major system failure.

My reccomendation would be to run the operating system solely off one storage disk, either the SSD or the spinning disk HD. I have a Acer Aspire One netbook with 120GB HD, but it has two SSD expansion slots i could use. I find its too much of a hassle and the speed difference is only partially worthwhile because your disk size is so limited on SSD and when running the EXT4 filesystem for ubuntu on a spinning HD the speed difference is hardly discernable except to numbers on a benchmark test. Ive run dozens of distros off SSD storage and i cant say any of them were slower on my HD.

Hope this helped a little bit... Basically im afraid your approach itself is going to cause problems short term and long term. I would run ubuntu straight from your main spinning disk HD rather than trying to cram onto SSD and move folders etc to save disk space... My humble opinion from experience!

Take care and happy Ubuntu-ing

-Christian

---

### Post by Cyril380 on 2013-09-14
You can use symlink to point a folder to another one in a different partition/hard drive.

---

### Post by CatKiller on 2013-09-15
8 GB isn't very big for a system drive. My personal recommendation would be to get a larger SSD and copy your existing / to that. Fairly straightforward, solves the storage problem and allows you to retain the performance boost.

The alternative, of having some things on your HDD, is certainly doable. It's the same process as you used for /home; create a partition, mount it at the appropriate place using fstab. You can even use different filesystems to take advantage of the fact that files in different locations are likely to have different characteristics.

There are a number of downsides to that approach, though. First, it's significantly easier to set that up at install time. Moving a running system around is a complete pain. Second, allocating the appropriate partition sizes is a black art and your partition structure is likely to get very complicated very quickly. Thirdly, the more stuff you move off the SSD, the less of a speed boost you'll get from using the SSD. There's no performance gain from having your binary on a fast SSD if the system has to wait for a slow HDD to load the libraries that it needs, or configuration files. Logs and documentation won't slow anything down, but they're tiny.

---

### Post by Impavidus on 2013-09-15
Your installed programs are in /usr. This is the directory probably taking most of your disk space on your SSD. You can move it to your HD, but this way you'll lose most of the speed advantage of the SSD. A bigger SSD would solve the problem, but if you don't want to buy new hardware some fix is still possible.

Maybe you can find that there's a directory somewhere in /usr that contains a large amount of data, of which only a few programs use a lot. For example, I found that my /usr/share/games directory contains 2GB, more than half of which is flightgear data. You could move one or more of these directories to your HD, which should only have an impact on speed when using one of those programs. Moving the entire /usr/share directory to your HD may have a significant impact on speed.

If you decide to move a single directory to your HD, you have to make a partition for it. Then use rsync to copy all data to the new partition (on a temporary mountpoint), modify /etc/fstab, rename the old directory as a backup and create an empty new directory with the same name, owner and permissions, and then remount the new partition on the location where the data used to be. If it works, delete the backup to free your SSD space. It's basically the same procedure as when moving your /home directory to a separate partition, as explained here: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you want to move multiple directories, you have to create a single partition for all of them on your HD (else your HD partitions will become a mess, although it should work), give it a nice mount point, copy the directories you want to move to the new partition and replace the originals with symlinks.

So, have a look at the space hogs in /urs/share. You may be able to find something interesting to move.

---

### Post by CeejRab on 2013-09-15
Ditto. the speed won't be discernible if its searching across drives for libraries and configs. Best to run from all one drive whether it be SSD or spinning HD. Just my recommendation from experience! 

If however you store large files that you don't desire to keep on the OS's storage device, you can always make a new folder on another drive and just go to it manually to get or use the files you need. Place a shortcut to it in your home folder and you won't even realize its a different drive ;)

All the best,

-Christian

---

### Post by cpu2007 on 2013-09-15
Thank you everyone for all the replies. As many of you, clearly, mentioned, moving folders to different partions will make a mess, make it complicated and obviously it will slow down applications.

The problem is that I don't mind if applications load slowly, I am comfortable with the system booting up quickly and the basic services of the system running fast(which is what's going on right now);however, I'd like to have a separate place thirdy party applications as this will allow me to install extra application without worrying about filling up my ssd. I could buy a new ssd but having a new ultrabook, I'd prefer to not touch it as it's still under warranty and ssd might be soldered.

Having said that, what I understand is that system files usually don't grow too much in size(unless there's a system upgrade or other similar things), so installing applications probably is what is filling up my ssd in my opinion. Wouldn't be possibly to move just the applications out? or isn't there anyway to manually choose where to install an application when downloading it?if so, is it possible to choose to insall all the branches of that application in the HDD instead of SSD?I am asking this because many app store their info in different folders, under different branches, I don't want an app to have half of it's data under HDD and some other under SSD.

I followed the home partitioning tutorial and didn't understand much but I did manage to move my partition successfully , however not sure yet how I can apply this to sysem files as I'm confused which folders are really safe to move.

---

### Post by CeejRab on 2013-09-15
Sounds like youve got a plan! Im personally not comfortable suggesting methods on moving system folders such as package libraries etc, but hopefully you will get what youre looking for from someone else who has played around with that more than i have! 

I understand your point, good choice too, its not that great an idea to dig into a brand new laptop and try to put new hardware in right away. 

I would encourage you to try a benchmark yourself or look at other's benchmark tests on booting from ssd or from HD because i think you'll find youre really not at that great of an advantage booting from SSD but still (albeit willingly you said) waiting for things to load from another drive.

All the best with your project! I hope it works out well for you.

---

### Post by jamesisin on 2013-09-15
What others have said about speed is correct.  Since it is rare for an application to consist of a single file but instead they tend to be collections of libraries and files upon which the core application relies, you are likely to see speed issues continuing even after the application in question has been loaded into memory.  Also, if you rely too heavily on your RAM your system will use more paging/swap which again is impacted by slower drive speeds.  I think the best recommendation is to obtain a larger SSD (they have really dropped in price).  I like Crucial.

If you get a larger SSD you could then use this 8GB SSD for your swap partition and perhaps see additional I/O benefits.

---

### Post by cpu2007 on 2013-09-15
I haven't benchhmarked the speed of hdd and ssd but I never seen such a visual improvement before on any laptop i owned.
Bootup time was around 25 secs when I was on the HDD(and it was fast ) , on the ssd it takes around 15 secs and apps like firefox fire up very quickly.

I'd definately consider a bigger ssd as I can see the advantages of having one. However, I'll stick with a software fix at the moment if it allows me to keep the system if the ssd and all the rest in the hdd without compromising too much.

---

### Post by Impavidus on 2013-09-16
The directories /var, /opt, /usr and any directories therein can safely be moved to another partition. Any program using files in those directories will slow down when you move those directories from your SSD to your HD, the more so when they have to load more files from the HD. So, browse your file system and try to locate any big directories that aren't heavily used by system programs, only by user programs. To list the size of various directories in for example /usr, use```
du --max-depth=2 /usr | sort -n
```

Files in Linux are more or less sorted by type, not application they belong to, so you can't simply move specific applications to your HD.

Two things that could slowly fill up are your /boot  and /usr/src directories, because old kernels and kernel headers aren't automatically uninstalled. Use your package manager to uninstall them, keeping one old version.

---

### Post by jamesisin on 2013-09-16
You can also remove old packages from your system with these:

```
sudo apt-get autoremove
sudo apt-get autoclean
```

---

