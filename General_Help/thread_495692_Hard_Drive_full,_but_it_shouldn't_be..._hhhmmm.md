---
title: "Hard Drive full, but it shouldn't be... hhhmmm"
date: 2007-07-08
forum: General Help
---

### Post by siafulinux on 2007-07-08
Hello everyone

Okay here's the problem. I was helping someone set up Linux on their laptop after taking it home. I downloaded a 600mb file overnight and when I got back this morning, the system had downloaded the file but I couldn't extract it because it says I am out of disk space!?

I also could not log into my machine. It threw me back to the login prompt.  I deleted the file to make sure that it somehow wasn't bloated (odd if it was). I can now log in, but it still says I am using a lot of space.

I have 160 gig hard drive, only used up about 20 to 30 gigs of that prior and have only two accounts on here (My wife's is sparse to say the least).... where did my space go? 

Virus maybe? Doubt it, but still...

Any suggestions of what it could be and also how I can find out where the biggest files on my drive are would be appreciated.

Thanks for your time and help
Siafu

---

### Post by taurus on 2007-07-08
When you remove something in nautilus, you need to empty your trash bin too or else it will take up the space.

What''s the output of this command from a terminal?

```
df -h
```

---

### Post by siafulinux on 2007-07-08
Thanks, I've also tried clearing out apt with 
sudo apt-get clean

Gone through each directory and checked file sizes, nothing comes close to 160gigs worth of data. Is something mis-reading?


Output of df -h
----
Filesystem            Size   Used   Avail  Use%  Mounted on
/dev/hda1          146G    136G  2.7G    99%    /
varrun                221M   112K   221M   1%     /var/run
varlock               221M         0    221M   0%      /var/lock
procbususb        221M   132K   221M   1%     /proc/bus/usb
udev                   221M   132K   221M   1%     /dev
devshm              221M     0        221M   0%     /dev/shm
lrm                      221M   34M     187M   16%    /lib/modules/2.6.20-16-386/volatile
/dev/hdb1           150G   80G      70G    54%    /media/hdb1

---

### Post by siafulinux on 2007-07-08
Sorry that's not showing neatly... I tried to space it out.


---

This is interesting:
df -h = 
/dev/hda1          146G    136G  2.7G    99%    /

but sudo du -sh /* shows

4.6M    /bin
65M     /boot
0       /cdrom
148K    /dev
14M     /etc
25G     /home
4.0K    /initrd
0       /initrd.img
0       /initrd.img.old
520M    /lib
48K     /lost+found


Certainly not 120+ gigs worth...

---

### Post by jjross on 2007-07-08
I had something similar happen and it turned out that something corrupted the file system and I used  'fsck' to fix it.
I dont remember the exact command but your problem sounds similar to the one I had.

Maybe this will lead you in the right direction for a fix.

---

### Post by taurus on 2007-07-08
What about

```
sudo du -h /var
```

---

### Post by siafulinux on 2007-07-08
Thanks... I will give it a go; rebooting.

Siafu

---

### Post by siafulinux on 2007-07-08
sudo du -h /var shows...

106G    /var/archives

????

---

### Post by siafulinux on 2007-07-08
Is this safe to remove these files... they are a bunch of .tar.gz files.

systemname.20070708.master.tar.gz

---

### Post by Old Pink on 2007-07-08
> **siafulinux said:**
> sudo du -h /var shows...

106G    /var/archives

????```
sudo du -h /var/archives
```Find the big file, have a look at it, delete it?

---

### Post by siafulinux on 2007-07-08
I went ahead and deleted them... with sudo rm -r /var/archives

Output of df now shows
Filesystem           1K-blocks    Used         Available     Use%  Mounted on
/dev/hda1            152538080  30889288 113900244  22%     /

Now, how do I stop that from happening again? What is doing it?

Thank you Taurus and everyone else who responded! Much, MUCH appreciated :)

---

