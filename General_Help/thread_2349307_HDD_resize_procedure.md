---
title: "HDD resize procedure"
date: 2017-01-13
forum: General Help
---

### Post by czgirb on 2017-01-13
At the beginning, my HDD's partition was divided as follow :
 

 [B]_20GB ... /
[/B]**_10GB ... swap**
**250GB ... /home**
**_10GB ... Windows Recovery**
 

 when re-installed ubuntu 14.04, I forget to stated that I have “**swap**” and “**/home**” partition.

 

 and since Nov 2016, i've been informed that my “**/**”, which is 20GB is insufficient. So, by using Gparted-LIVE I deleted my swap, and directly resize (enlarged) my “/”. is what I've done is OK?

  Cos recently, I feel that all downloads was ended by “**failed**”. at first, I don't think so, but since it was happen four times and all have the same results.
It's forced me for having a **concern/perceptioned** that was … maybe … it was caused by all files was unable to be write in my “/” properly.

 

 Is my concern/perception is right? If YES, how can I repaired all mistakes that I've been made?

 Please guide me … Thanx

---

### Post by yancek on 2017-01-13
You must be installing a lot of software to fill up a 20GB / partition.  If you are downloading something from the internet, you would be logged in as a normal user and since you have a separate /home partition, what you download would go to the /home/user/Downloads directory by default.  What are you downloading?  Does this happen when you download software from the repositories or just generally from different internet sites?

Ubuntu like other Linux systems is designed as a multi-user system and therefore a normal user does not generally have permissions to 'write' to anything outside the /home/user directory.  More details/specifics would help.  You can run this command to show how full your mounted partitions are:  sudo df-h

Reducing swap to increase root should not be a problem.  Many systems never use swap.  It depends on the size of RAM, 4GB or more should suffice unless you are hibernating.

---

### Post by czgirb on 2017-01-13
czgirb@ubuntu:~$  sudo df-h
[sudo] password for czgirb: 
sudo: df-h: command not found
czgirb@ubuntu:~$

---

### Post by ajgreeny on 2017-01-13
You need a space between the df and the -h, ie, **df -h**, not **df-h** as you typed it.
That command will also tell us if you now have a separate /boot partition which can cause problems installing updates or new packages if old kernels are not removed and remain on disk.

I have never had a root partition in my system larger than 20GB and I have added quite a lot of applications, including plexmediaserver which uses a lot of space in root, but even so, I have only 8.8GB of used space in / (46%).

I think whoever told you you must have a larger root partition than 20GB is being over-pessimistic and I doubt you will get anywhere near filling it.

---

### Post by oldfred on 2017-01-13
If when you reinstalled, you did not use Something Else and include your existing /home, then you are not using your /home but a new /home inside your / (root) partition.

Post this:
sudo cat /etc/fstab

And if /home not mounted you can move it to your existing partition. You can just skip the steps on creating the partition. You probably still want to copy data from /home folder in / if you have used it for a while as it will have newer data. Of course good backups are required before any major system reconfiguration.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by czgirb on 2017-01-13
czgirb@ubuntu:~$ sudo df -h
[sudo] password for czgirb: 
```
Filesystem      Size  Used Avail Use% Mounted on
udev            981M   12K  981M   1% /dev
tmpfs           199M  1.3M  197M   1% /run
/dev/sda1        28G   18G  8.0G  70% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            991M  1.9M  989M   1% /run/shm
none            100M   68K  100M   1% /run/user
/dev/sda4       202G  167G   25G  88% /media/czgirb/207GB
/dev/sdb1       459G  428G  7.8G  99% /media/czgirb/500GB
czgirb@ubuntu:~$
```

---

### Post by czgirb on 2017-01-13
> **ajgreeny said:**
> You need a space between the df and the -h, ie, **df -h**, not **df-h** as you typed it.
That command will also tell us if you now have a separate /boot partition which can cause problems installing updates or new packages if old kernels are not removed and remain on disk.

I have never had a root partition in my system larger than 20GB and I have added quite a lot of applications, including plexmediaserver which uses a lot of space in root, but even so, I have only 8.8GB of used space in / (46%).

I think whoever told you you must have a larger root partition than 20GB is being over-pessimistic and I doubt you will get anywhere near filling it.

as informed by the system, I really used more than 20GB
within my ubuntu 14.04, I only installed:
- Thunar
- Audacity, DeaDBeeF, MediaInfo, Handbrake, Puddletag, and VLC
- Gnome and Unity TweakTool.
- Wine ... Medival CUE, Media Monkey, and Foobar
and when i do:
- sudo apt-get autoclean
- sudo apt-get clean
- sudo apt-get autoremove
there will be no result

---

### Post by oldfred on 2017-01-13
Is your sda4 your old /home?

But all your partitions are effectively full. Is external is NTFS it is over full as NTFS needs 30% free to work well and at 10% free you can not run defrag.
But even if ext4 partitions you should not fill them. 
Either time for major housecleaning or larger hard drive.

---

### Post by geeksmith on 2017-01-13
If you're concerned about no longer having swap space, go to [https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)

Scroll to and follow the instructions under the heading "Four-step Process to Add Swap File".

You'd also do well to follow the link posted by oldfred to move your home directory to that 250GB partition. Your "df" output shows that you're not using it right now.

---

### Post by czgirb on 2017-01-13
yes! my previous /home is sda4 ... now, my /home should be inside my / ... so be it. cos it means i do not need to stated which one is when i reinstall new OS.
when i explore my /home, it only contains current wallpaper only.
so, back to the previous topic ...  as i said "... it forced me for having a **concern/perceptioned** that was &#8230; maybe &#8230; it was caused by all files was unable to be write in my &#8220;/&#8221; properly." is it possible to be happen or not? if it is, how can i repair the mistake? please guide me ...

---

### Post by oldfred on 2017-01-13
Your /home has a lot of hidden files & folders including .wine and whatever is in it. Your Firefox & Thunderbird profiles are in /home in hidden folders.
If nothing to save you can just mount old /home in your fstab. Last step in link on moving /home above.

But that does not solve issue of just about all partitions are effectively full. 
Even / at 20GB has a lot of data. Did you save a lot in your /home that is in /?

---

