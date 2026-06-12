---
title: "Low Disk Space Warning pop-up window after reboot"
date: 2013-11-01
forum: General Help
---

### Post by CindyP on 2013-11-01
I have been getting these messages after every reboot since last July.  I finally got alarmed a few days ago when the remaining space was 224MB
[LIST]
[*]July: "The 'Filesystem Root' has only 772.2 mb Disk Space remaining.
[*]30 October: 224.2 mb remaining
[*]30 October (later): 79.4 mb remaining
[*]after I performed the cleanup steps described in this Ubuntu forum [link]("http://ubuntuforums.org/showthread.php?t=2172112&highlight=Low+disk+space") the warning still popped up but looked like it was getting better:  519.1 mb Remaining
[*]now today 1 November I have finally done it and there is NO "0" space remaining!
[ATTACH=CONFIG]247441[/ATTACH]
[/LIST]

Here are the results from many of the troubleshooting commands recommended in earlier similar posts:
df - report file system disk space usage
du - estimate file space usage for root / 
du - estimate file space usage for /var

```

cindy@Calanthe2:~$  df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda6      ext3       20G  6.1G   13G  33% /
udev           devtmpfs  1.5G  4.0K  1.5G   1% /dev
tmpfs          tmpfs     599M  1.6M  597M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.5G  160K  1.5G   1% /run/shm
/dev/sdb5      ext4      917G  499G  372G  58% /home
/dev/sda7      ext4      173G  157G  7.2G  96% /media/VideoStore

cindy@Calanthe2:~$  sudo du -h --max-depth=1 / | sort -h
[sudo] password for cindy: 
du: cannot access `/proc/10259/task/10259/fd/3': No such file or directory
du: cannot access `/proc/10259/task/10259/fdinfo/3': No such file or directory
du: cannot access `/proc/10259/fd/3': No such file or directory
du: cannot access `/proc/10259/fdinfo/3': No such file or directory
du: cannot access `/home/cindy/.gvfs': Permission denied
0	/proc
0	/sys
4.0K	/cdrom
4.0K	/dev
4.0K	/mnt
4.0K	/selinux
16K	/lost+found
200K	/srv
256K	/tmp
1.8M	/run
2.6M	/root
8.6M	/bin
9.1M	/sbin
17M	/etc
48M	/boot
215M	/opt
274M	/lib
761M	/var
4.7G	/usr
157G	/export
157G	/media
499G	/home
817G	/

cindy@Calanthe2:~$ sudo du -h --max-depth=1 /var | sort -h
4.0K	/var/crash
4.0K	/var/local
4.0K	/var/mail
4.0K	/var/opt
1.6M	/var/spool
6.7M	/var/backups
11M	/var/tmp
17M	/var/log
182M	/var/cache
544M	/var/lib
761M	/var

```
And two screenshots from GParted showing how my disks are allocated
[ATTACH=CONFIG]247442[/ATTACH]  [ATTACH=CONFIG]247443[/ATTACH]

Yes, I see that the partition mounted at /media/VideoStore is 96% full but that partition was only created yesterday from some old space on an old internal hard drive when I wanted to get all my videos out of my /home. 

One last thing I wanted to mention was this [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/881376") It mentions that there was a problem with the Low Disk Space screen popping up Repeatedly but said "This bug was fixed in the package gnome-settings-daemon - 3.6.4-0ubuntu10".   Is there any way that I can get that fix on my 12.04 lts system?   

Is it possible this message is a bug since I am clearly running with 0 space left or is my system in imminent danger?
Is there something else I should be doing to ensure I have an ongoing and viable system?

Thanks, CindyP

---

### Post by Bucky Ball on 2013-11-01
sda7 has three mount points! This could be causing some confusion, but unsure. I would get rid of two of them, the ones which begin with /export/. No idea about them. 

Try that and reboot. sda7 should rightfully be mounting at /media/Videostore (don't know what or where /export is, but I'm guessing it is of your own creation).

Also, your / partition is EXT3. This indicates you are using an old install (release) or you have manually used EXT3 during install. Which? 12.04 uses EXT4 for / so this is also a mystery ... :-k

---

### Post by Impavidus on 2013-11-01
> **Bucky Ball said:**
> 
Also, your / partition is EXT3. This indicates you are using an old install (release) or you have manually used EXT3 during install. Which? 12.04 uses EXT4 for / so this is also a mystery ... :-k
Not much of a mystery, probably installed as 9.04 or before, then upgraded to 12.04. I have a Precise box still using ext3 (I think, would have to check it), upgraded all the way from Dapper Drake.

---

### Post by Bucky Ball on 2013-11-01
> **Impavidus said:**
> Not much of a mystery ...

True, not one at all in your circumstance, really. Best to go for clarity, though, and that question remains unanswered by the OP. ;)

---

### Post by CindyP on 2013-11-01
> **Bucky Ball said:**
> sda7 has three mount points! This could be causing some confusion, but unsure. I would get rid of two of them, the ones which begin with /export/. No idea about them.  Try that and reboot. sda7 should rightfully be mounting at /media/Videostore (don't know what or where /export is, but I'm guessing it is of your own creation). 

Yes the /export mount points are confusing to me too.  And yes they are of my creation.  I set up NFS shares for a Raspberry Pi XBMC project following [this cookbook]("http://raspberrypihtpc.wordpress.com/how-to/how-to-ubuntu-12-04-nfs-and-xbmc-resolved/")  Since the shares worked with the RaspberryPi I assumed the setup was OK.   I have just commented out those shares in my fstab and rebooted.  
```

#NFS Exports for XBMC
#/media/VideoStore/Movies    /export/Movies     nobootwait  bind                     0  0  
#/media/VideoStore/TV_Shows   /export/TV_Shows   nobootwait  bind                     0  0  

```

(of course my NFS shares don't work now) but so far no low disk message either.   I will wait until the morning to see if the message pops up overnight.   

> **Bucky Ball said:**
> 
Also, your / partition is EXT3. This indicates you are using an old install (release) or you have manually used EXT3 during install. Which? 12.04 uses EXT4 for / so this is also a mystery ... :-k   
> **Impavidus said:**
> Not much of a mystery, probably installed as 9.04 or before, then upgraded to 12.04. I have a Precise box still using ext3 (I think, would have to check it), upgraded all the way from Dapper Drake.

My last install from scratch was the previous LTS and I upgraded to 12.04, added a second hard drive etc.  That is how my partitions have gotten so messy and why /  is on EXT3.   Do I NEED to change this to EXT4?

Well so far so good on the low disk.  I might have to open a separate question on the NFS shares.

---

### Post by Bucky Ball on 2013-11-01
Thanks for the clarification. No, shouldn't be an issue using EXT3/4. Just wanted to rule that out in case something was going on there.

Hmm, interesting about the NFS shares, and probably a good idea opening a new thread about that. Is the RPi still attached? Not sure how you have it set up, but if you are attempting to access the Pi with those shares when you boot and fstab is run, that would be a problem. 

Are you using RaspBMC on the Pi (I presume)? I am, and as a side note, I go Video>Files>Add Video and you can add a location of a remote drive (on your local network or probably the WAN) that way. You will see 'Enter name or browse for path' and under that a box with <none>. Click that and you get an input window and there you'll see a button with 'ip address'. Away you go. 

You need to setup static IPs to do it this way and have the exact path to the directory where your 'Videos' are (in your case /media/VideoStore/Movies).

---

### Post by CindyP on 2013-11-01
Thanks Bucky Ball for all your help.  Everything is sorted now.   The mounts in fstab were all wrong and causing the double count I think.  Removing the fstab entries removed the Low Disk Space pop-up.   Also changing my /etc/exports file and adding the new /media/VideoStore made them available to see from my Raspberry Pi (yes running RASPBMC) so much cleaner and all works now.   Problem SOLVED!

---

### Post by Bucky Ball on 2013-11-02
Glad to be of assistance. Excellent news and enjoy! ;)

---

