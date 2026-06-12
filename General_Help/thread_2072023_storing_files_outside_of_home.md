---
title: "storing files outside of /home"
date: 2012-10-16
forum: General Help
---

### Post by lmm5247 on 2012-10-16
been looking all over and can't seem to find an answer for this...

i recently re-installed ubuntu and enabled an encrypted home directory upon installation. i quickly realized that /home/.ecryptfs directory is the directory that holds my encrypted files, while /home is just a virtual representation of that directory.

[HTML]http://ubuntuforums.org/showpost.php?p=9790901&postcount=8[/HTML]

however. my home directory is showing as only having 7GB left (on a 100GB partition). i know that it's not ACTUALLY that full, because the OS counts the data twice (once in .encryptfs, and once in /home).

I'd like to move some data out of /home, but I don't know where to put it. can I create folders in /usr without them being deleted/changed by the OS?

---

### Post by BrandonIngalls on 2012-10-16
/home/.ecryptfs/username/.Private is where your encrypted files are stored, it gets mounted at /home/username the file usage is not counted twice.

You can create files anywhere but /proc /sys /dev /tmp /run and they will not be deleted by the system. but it sounds to me like you have some junk files, or files you don't know about...
Open a terminal and try these commands to get a feel of where all your space has gone...
```
df -h

du --max-depth=1 -h
```

---

### Post by lykwydchykyn on 2012-10-16
I would suggest just creating your own top-level folder like /data and putting things there.  The system is pretty much guaranteed not to touch an unknown folder like that.

---

### Post by kjohri on 2012-10-17
One way is to make another partition, say /home1, at the time of installation and put those files in /home1/username, after setting the user and group ids of /home1/username to that of the current user. The advantage is that, in case you wish to reload the OS, you can just format the root partition, keeping /home and /home1 partitions as they are and not formatting them. I am assuming that you have root and /home as different partitions in the first place.

---

### Post by lmm5247 on 2012-10-17
> **BrandonIngalls said:**
> /home/.ecryptfs/username/.Private is where your encrypted files are stored, it gets mounted at /home/username the file usage is not counted twice.

You can create files anywhere but /proc /sys /dev /tmp /run and they will not be deleted by the system. but it sounds to me like you have some junk files, or files you don't know about...
Open a terminal and try these commands to get a feel of where all your space has gone...
```
df -h

du --max-depth=1 -h
```
I know it's not *really* there twice, but apps like Disk Usage Anaylzer count it twice. So (from what I understand), that partition is really only half-full, but the OS thinks otherwise...

```
logan@acer ~ $ df -h
df: `/home/logan/.gvfs': Transport endpoint is not connected
df: `/root/.gvfs': Permission denied
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             200G  7.9G  183G   5% /
udev                  3.9G  4.0K  3.9G   1% /dev
tmpfs                 1.6G  1.1M  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.9G  664K  3.9G   1% /run/shm
/dev/sda1              93G   83G  6.4G  93% /home
/home/logan/.Private   93G   83G  6.4G  93% /home/logan

```

```
logan@acer ~ $ du --max-depth=1 -h
168K	./.macromedia
4.0K	./Pictures
4.0K	./.ssh
4.0K	./.hardinfo
52K	./.gnupg
5.3M	./Downloads
1.5G	./Desktop
32K	./.dbus
88K	./.pulse
64K	./.audacity-data
12K	./.cups
4.0K	./Public
920K	./.gstreamer-0.10
76K	./.gnome2
3.1M	./.cache
121M	./.dropbox
4.0K	./Podcasts
308K	./.fontconfig
212K	./.VirtualBox
2.2M	./.adobe
30G	./Music
4.0K	./Documents
11M	./.config
du: cannot access `./.gvfs': Transport endpoint is not connected
66M	./.thumbnails
28K	./.remmina
16K	./.vnc
4.0K	./.gphoto
1.3M	./.gconf
22G	./Dropbox
28G	./VirtualBox VMs
2.4M	./.local
4.0K	./.gnome2_private
4.0K	./Videos
24K	./.linuxmint
16K	./.freerdp
4.0K	./Audiobooks
4.0K	./Templates
91M	./.mozilla
16K	./.mplayer
81G	.

```
This is actually really helpful, thanks! I can see exactly where all my space is being used up (they're all legit files). So I'll just have to figure out where I'd want to move some stuff to. 

> **lykwydchykyn said:**
> I would suggest just creating your own top-level folder like /data and putting things there.  The system is pretty much guaranteed not to touch an unknown folder like that.
Hmmm, why didn't I think of that? haha :)
I was considering reformatting and increaseing the size of the /home partition, but this is much easier.

> **kjohri said:**
> One way is to make another partition, say /home1, at the time of installation and put those files in /home1/username, after setting the user and group ids of /home1/username to that of the current user. The advantage is that, in case you wish to reload the OS, you can just format the root partition, keeping /home and /home1 partitions as they are and not formatting them. I am assuming that you have root and /home as different partitions in the first place.
At one point, I did have a separate partition for my data (1 for OS, 1 for /home, and 1 for data), but decided to put it all in /home so it would be encrypted. However, now the encryption is problem...

---

### Post by smoka on 2012-10-18
I'd be tempted to back up my data and then boot using GParted Live or something similar, then shrink / partition and increase the /home partition

---

### Post by Lisiano on 2012-10-18
df will tell you the exact amount of free space available. And seeing as how you have 30 gigs of Music, 22 gigs of Dropbox data and 28 gigs of VMs, I say that's 80 gigs, now count in the other small files, the encryption overhead and you get your 83 gigs.

Note, Disk Usage Analyzer might fail to understand the proper disk usage due to it's design. Unlike df, it checks the sizes of every file it can find, as opposed to df which will just ask the filesystem about it's usage.

Another awesome tool to visualize file usage is [Filelight](apt://filelight). Only problem is that it's a QT app, so it will download quite a bit of KDE stuff so it can work. But it does draw way better ring charts than Disk Usage Analyzer.

---

