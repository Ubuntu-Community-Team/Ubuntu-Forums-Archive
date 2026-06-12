---
title: "/ filled up then 'no space left' and lockup."
date: 2016-03-19
forum: General Help
---

### Post by Bucky Ball on 2016-03-19
Hi all. Is this normal for the contents of these folders directly after boot?

```
$ dir /var/tmp
systemd-private-5865b17aff664ec69d18a2659e6b07f6-colord.service-X50gy3
systemd-private-5865b17aff664ec69d18a2659e6b07f6-rtkit-daemon.service-PEEa3z
systemd-private-5865b17aff664ec69d18a2659e6b07f6-systemd-timesyncd.service-5rNeMz

$ dir /tmp
config-err-HdRP7Y
systemd-private-5865b17aff664ec69d18a2659e6b07f6-colord.service-axGfFO
systemd-private-5865b17aff664ec69d18a2659e6b07f6-rtkit-daemon.service-osktJd
systemd-private-5865b17aff664ec69d18a2659e6b07f6-systemd-timesyncd.service-4V2rtl

```

Rather desperate. I am furiously attempting to finish a major review for uni this Wednesday, about to go to bed last night and closing documents to shutdown when I tried to close a Libreoffice doc and got a message that there was an internal error or something like it and Libreoffice couldn't perform any operations on the file. I could shutdown all other LO files fine and once I did the problematic one shut with no whining. 

After that, no space left on disk messages every time I tried to launch anything. I couldn't open gparted to see if the disk actually was full.

Anyhow, I'm on 15.10 with 16.04 on another partition so booted into 16.04 and, sure enough, the 15.04 / partition had about 700mb left available and was full. Crazy thing is, there is virtually nothing on that partition. So I mounted it in a file manager and started to hunt. There is nothing anywhere that is anywhere near big enough to fill 20Gb (the size of the 15.10 / partition). The only thing of consequence was the 2Gb Uni folder which contains all my work. I backed that up, deleted it from the / partition and rebooted into 15.10 which now had enough headroom to allow me to dig a bit deeper.

I can still find nothing, but the output at the beginning of this post might give a clue. What I did discover was that both those folders had about fifty lines like it and a few other bits and pieces. Where have they come from? Deleted the lot, rebooted, and without doing anything else, I get what is shown in my output above in those folders. 
_____

Hunted and grunted (to put it mildly) and found a bunch of clues about what might be happening, a link is still open for a deleted linked file looking promising, then there's [this]("http://askubuntu.com/questions/627594/can-i-delete-older-systemd-private-md32-files-in-var-tmp") and [this]("http://askubuntu.com/questions/266825/what-do-i-do-when-my-root-filesystem-is-full"), none of which has done anything for me (although they might if I had any idea what to do with the output ... clutching at straws there).

I've always had issues with USB on this machine (new build, i7, 16Gb RAM, NVidia GTX 970, Gigabyte MB) where the keyboard dies and comes back to life randomly and less often the USB network adapter does the same, so wondering if related.

Frankly, fairly clueless with what to do at this point and deep breathing (ain't deadlines fun). Have found a workaround (mount 16.04 partition in 15.10 to access the backed up Uni folder stored there) but it is pretty important I get to the bottom of this. And yes, there is nothing in trash (although something about hidden trash was in some thread I read). About to get back to work and half expecting the /var/tmp and /tmp folders to start filling up when I do. Is there anything I should report? Any log that would help folk help me diagnose?

For now I'll get back to what I need to be doing via my workaround (after six lost, valuable hours screwing around with this) and check back later. Appreciate any and all clues, I have all digits and eyes crossed, and TIA.
_____

*** NOTE: I just booted in to 16.04 and before doing anything this is what I have in those same folders here:

```
$ dir /tmp
config-err-fPbv94
systemd-private-eff1f475153245fd9f05e62f79fcda58-rtkit-daemon.service-QbtlvI
systemd-private-eff1f475153245fd9f05e62f79fcda58-systemd-timesyncd.service-MBo1W2

$ dir /var/tmp
audacity-bucky
systemd-private-4db87bd99aec489eae4f4550e794d9fa-rtkit-daemon.service-QO1cAl
systemd-private-4db87bd99aec489eae4f4550e794d9fa-systemd-timesyncd.service-6d3NEe
systemd-private-8aafe2f854634f41ab28bde4f7d52fda-systemd-timesyncd.service-dF9DyW
systemd-private-b688b69e31e442df987172be2aac0be0-rtkit-daemon.service-oq7gsR
systemd-private-b688b69e31e442df987172be2aac0be0-systemd-timesyncd.service-Gvyxxb
systemd-private-eff1f475153245fd9f05e62f79fcda58-rtkit-daemon.service-z8MDtC
systemd-private-eff1f475153245fd9f05e62f79fcda58-systemd-timesyncd.service-fDZY6S

```

16.04 seems fine at this point so I'm guessing these files and folders in these folders are not the issue and the multitude that was created at crash time in 15.10 were the result of something else? But what something? Which brings me back to the orphan link loop/looking for a deleted file. That doesn't seem to be happening now but still the 15.10 disk is full. Where is that data? Clueless ...

And just for good measure, have attached a pic of htop from 15.10 with no apps launched on desktop. I see some suspiciousness there (sbin action?) but no idea what to do to dig further.

---

### Post by sudodus on 2016-03-19
Just a random guess: Have you checked/repaired the file system? Maybe a bug in LibreOffice or in the USB system damaged the file system.

---

### Post by Bucky Ball on 2016-03-19
> **sudodus said:**
> Just a random guess: Have you checked/repaired the file system? Maybe a bug in LibreOffice or in the USB system damaged the file system.

Hi sudodus. You mean the partition filesystem? EXT4? I can get through updates/upgrades no issue and there seems to be no issues now I have moved the Uni folder. 

The partition is right next to a Win one so I shrank Win by 10Gb and have room to expand the 15.10 / partition into, but changed my mind on that  as I really don't have the time now to deal with anything else going wrong. I'm going to see the sun come up for the next couple of days working on uni major review I need in by Wednesday as it is so will use the Uni folder in 16.04 mounted in 15.10 for the moment and try to blast through it! :|

Will keep sniffing in any spare moments ...

---

### Post by sudodus on 2016-03-19
Boot from another drive and run

```
sudo e2fsck -f /dev/sdxy
```

to check more thoroughly than the simple check at boot! The strange behaviour with a full drive could be caused by some damage to the file system.

You can also look for huge files or directories for example with ***baobab***.

---

### Post by Bucky Ball on 2016-03-19
Bingo, you legend. I like that Baobab app. My /var/log is 10Gb! Can't figure why I wasn't looking there before. Probably because I'm fairly stressed and had become fixated with the errors in /tmp and /var/tmp which I was convinced had nothing to do with it in the end anyway. 

So, is it as easy as deleting all log files in /var/log folder while not touching the folders in there? There may be clues in there as to what is at the root of it filling up, may point to what's dropping a heap of errors (install only about a month and a half old) but haven't time for that now. Wait til next time ...

What do you make of this screenshot? I had some issues with the BIOS resetting to odd times and years and I think that might explain the crazy dates on some of this, but are those dates causing another issue?

---

### Post by sudodus on 2016-03-19
I'm glad that I could help finding what filled your partition.

You have to ask other people how to understand the log files, for example server people. I have not learned that art yet :-P

---

### Post by sudodus on 2016-03-19
109 years - very strange.

What do

```

ls -lt /var/log
ls -ltr /var/log
ls -lSr /var/log

```

show?

---

### Post by Bucky Ball on 2016-03-19
```
$ ls -lt /var/log
total 9869100
-rw-rw-r-- 1 root   utmp      128256 Mar 20 00:34 wtmp
-rw-r----- 1 syslog adm       136967 Mar 20 00:17 auth.log
-rw-r----- 1 syslog adm      1882892 Mar 20 00:17 syslog
-rw-r--r-- 1 root   root      110101 Mar 19 23:47 dpkg.log
-rw-r----- 1 syslog adm      2001426 Mar 19 23:27 kern.log
-rw-r--r-- 1 root   root       26952 Mar 19 17:58 Xorg.0.log
drwxr-xr-x 2 root   root        4096 Mar 19 17:58 lightdm
-rw-r--r-- 1 root   root          55 Mar 19 17:58 prime-offload.log
-rw-r--r-- 1 root   root          30 Mar 19 17:58 prime-supported.log
-rw-r--r-- 1 root   root         549 Mar 19 17:58 boot.log
-rw-r--r-- 1 root   root        1395 Mar 19 17:58 gpu-manager.log
-rw-r--r-- 1 root   root       27645 Mar 19 17:58 Xorg.0.log.old
-rw------- 1 root   utmp        3072 Mar 19 17:37 btmp
-rw-rw-r-- 1 root   utmp      292292 Mar 19 06:00 lastlog
-rw-r----- 1 syslog adm  10098462720 Mar 19 05:42 syslog.1
drwxr-xr-x 2 root   root        4096 Mar 19 05:42 cups
-rw-r----- 1 root   adm            0 Mar 19 05:42 apport.log
-rw-r----- 1 root   adm          640 Mar 19 05:38 apport.log.1
drwxr-xr-x 2 root   root        4096 Mar 19 03:36 upstart
-rw-r----- 1 syslog adm       618577 Mar 18 14:26 syslog.2.gz
-rw-r----- 1 syslog adm        61418 Mar 17 15:31 syslog.3.gz
-rw-r----- 1 root   adm          307 Mar 17 03:55 apport.log.2.gz
-rw-r----- 1 syslog adm        40868 Mar 16 22:52 syslog.4.gz
-rw-r----- 1 syslog adm       120120 Mar 15 17:10 syslog.5.gz
-rw-r----- 1 syslog adm        55516 Mar 14 00:22 syslog.6.gz
-rw-r--r-- 1 root   root         887 Mar 13 18:17 alternatives.log
-rw-r----- 1 root   adm          255 Mar 13 18:03 apport.log.3.gz
-rw-r----- 1 syslog adm        60178 Mar 13 01:59 syslog.7.gz
-rw-r----- 1 syslog adm        37796 Mar 13 01:56 auth.log.1
-rw-r----- 1 syslog adm       658804 Mar 13 00:50 kern.log.1
-rw-r----- 1 syslog adm         5140 Mar  8 03:44 auth.log.2.gz
-rw-r----- 1 syslog adm       199371 Mar  7 17:12 kern.log.2.gz
-rw-r----- 1 root   adm          397 Mar  3 05:06 apport.log.4.gz
-rw-r--r-- 1 root   root       32032 Mar  1 18:21 faillog
drwxr-xr-x 2 root   root        4096 Mar  1 16:58 apt
-rw-rw-r-- 1 root   utmp      144384 Mar  1 06:23 wtmp.1
-rw-r--r-- 1 root   root       54474 Feb 29 18:20 dpkg.log.1
-rw-r--r-- 1 root   root         162 Feb 29 18:12 alternatives.log.1
-rw-r----- 1 syslog adm         7938 Feb 28 01:10 auth.log.3.gz
-rw-r----- 1 syslog adm       512406 Feb 28 01:08 kern.log.3.gz
-rw-r--r-- 1 root   root        4079 Feb 28 00:36 fontconfig.log
-rw-r----- 1 root   adm          324 Feb 25 02:16 apport.log.5.gz
-rw------- 1 root   utmp        1920 Feb 23 17:23 btmp.1
drwxr-xr-x 2 root   root        4096 Feb 23 15:59 dist-upgrade
-rw-r----- 1 root   adm          573 Feb 23 01:57 apport.log.6.gz
-rw-r----- 1 syslog adm         2620 Feb 22 03:17 auth.log.4.gz
-rw-r----- 1 syslog adm       120712 Feb 22 03:15 kern.log.4.gz
-rw-r--r-- 1 root   root         446 Feb 21 01:17 dpkg.log.2.gz
-rw-r----- 1 root   adm          305 Feb 20 23:22 apport.log.7.gz
-rw-r--r-- 1 root   root        7899 Feb 19 01:31 dpkg.log.3.gz
-rw-r--r-- 1 root   root         600 Feb 18 23:42 alternatives.log.2.gz
-rw-r--r-- 1 root   root         137 Feb 14 03:09 alternatives.log.3.gz
-rw-r--r-- 1 root   root         335 Feb 10 20:54 dpkg.log.4.gz
-rw-r--r-- 1 root   root       16823 Feb  9 00:48 dpkg.log.5.gz
-rw-r--r-- 1 root   root         468 Feb  7 15:46 alternatives.log.4.gz
-rw-r--r-- 1 root   root       22042 Feb  6 23:22 Xorg.1.log
drwxr-xr-x 2 root   root        4096 Feb  4 01:20 installer
drwxr-xr-x 3 root   root        4096 Oct 22 20:19 hp
-rw-r--r-- 1 root   root       72222 Oct 22 20:01 bootstrap.log
-rw-r----- 1 root   adm           31 Oct 22 19:57 dmesg
drwxr-xr-x 2 root   root        4096 Oct 22 19:57 fsck
drwxr-x--- 2 root   adm         4096 Feb  4  1907 unattended-upgrades
-rw-r--r-- 1 root   root       70962 Feb  4  1907 dpkg.log.8.gz
-rw-r--r-- 1 root   root        3447 Feb  4  1907 alternatives.log.7.gz
-rw-r--r-- 1 root   root         712 Feb  4  1907 dpkg.log.6.gz
-rw-r--r-- 1 root   root         136 Feb  4  1907 alternatives.log.5.gz
-rw-r--r-- 1 root   root        7274 Feb  4  1907 dpkg.log.7.gz
-rw-r--r-- 1 root   root        1007 Feb  4  1907 alternatives.log.6.gz

```
```
$ ls -ltr /var/log
total 9869100
-rw-r--r-- 1 root   root        1007 Feb  4  1907 alternatives.log.6.gz
-rw-r--r-- 1 root   root        7274 Feb  4  1907 dpkg.log.7.gz
-rw-r--r-- 1 root   root         136 Feb  4  1907 alternatives.log.5.gz
-rw-r--r-- 1 root   root         712 Feb  4  1907 dpkg.log.6.gz
-rw-r--r-- 1 root   root        3447 Feb  4  1907 alternatives.log.7.gz
-rw-r--r-- 1 root   root       70962 Feb  4  1907 dpkg.log.8.gz
drwxr-x--- 2 root   adm         4096 Feb  4  1907 unattended-upgrades
drwxr-xr-x 2 root   root        4096 Oct 22 19:57 fsck
-rw-r----- 1 root   adm           31 Oct 22 19:57 dmesg
-rw-r--r-- 1 root   root       72222 Oct 22 20:01 bootstrap.log
drwxr-xr-x 3 root   root        4096 Oct 22 20:19 hp
drwxr-xr-x 2 root   root        4096 Feb  4 01:20 installer
-rw-r--r-- 1 root   root       22042 Feb  6 23:22 Xorg.1.log
-rw-r--r-- 1 root   root         468 Feb  7 15:46 alternatives.log.4.gz
-rw-r--r-- 1 root   root       16823 Feb  9 00:48 dpkg.log.5.gz
-rw-r--r-- 1 root   root         335 Feb 10 20:54 dpkg.log.4.gz
-rw-r--r-- 1 root   root         137 Feb 14 03:09 alternatives.log.3.gz
-rw-r--r-- 1 root   root         600 Feb 18 23:42 alternatives.log.2.gz
-rw-r--r-- 1 root   root        7899 Feb 19 01:31 dpkg.log.3.gz
-rw-r----- 1 root   adm          305 Feb 20 23:22 apport.log.7.gz
-rw-r--r-- 1 root   root         446 Feb 21 01:17 dpkg.log.2.gz
-rw-r----- 1 syslog adm       120712 Feb 22 03:15 kern.log.4.gz
-rw-r----- 1 syslog adm         2620 Feb 22 03:17 auth.log.4.gz
-rw-r----- 1 root   adm          573 Feb 23 01:57 apport.log.6.gz
drwxr-xr-x 2 root   root        4096 Feb 23 15:59 dist-upgrade
-rw------- 1 root   utmp        1920 Feb 23 17:23 btmp.1
-rw-r----- 1 root   adm          324 Feb 25 02:16 apport.log.5.gz
-rw-r--r-- 1 root   root        4079 Feb 28 00:36 fontconfig.log
-rw-r----- 1 syslog adm       512406 Feb 28 01:08 kern.log.3.gz
-rw-r----- 1 syslog adm         7938 Feb 28 01:10 auth.log.3.gz
-rw-r--r-- 1 root   root         162 Feb 29 18:12 alternatives.log.1
-rw-r--r-- 1 root   root       54474 Feb 29 18:20 dpkg.log.1
-rw-rw-r-- 1 root   utmp      144384 Mar  1 06:23 wtmp.1
drwxr-xr-x 2 root   root        4096 Mar  1 16:58 apt
-rw-r--r-- 1 root   root       32032 Mar  1 18:21 faillog
-rw-r----- 1 root   adm          397 Mar  3 05:06 apport.log.4.gz
-rw-r----- 1 syslog adm       199371 Mar  7 17:12 kern.log.2.gz
-rw-r----- 1 syslog adm         5140 Mar  8 03:44 auth.log.2.gz
-rw-r----- 1 syslog adm       658804 Mar 13 00:50 kern.log.1
-rw-r----- 1 syslog adm        37796 Mar 13 01:56 auth.log.1
-rw-r----- 1 syslog adm        60178 Mar 13 01:59 syslog.7.gz
-rw-r----- 1 root   adm          255 Mar 13 18:03 apport.log.3.gz
-rw-r--r-- 1 root   root         887 Mar 13 18:17 alternatives.log
-rw-r----- 1 syslog adm        55516 Mar 14 00:22 syslog.6.gz
-rw-r----- 1 syslog adm       120120 Mar 15 17:10 syslog.5.gz
-rw-r----- 1 syslog adm        40868 Mar 16 22:52 syslog.4.gz
-rw-r----- 1 root   adm          307 Mar 17 03:55 apport.log.2.gz
-rw-r----- 1 syslog adm        61418 Mar 17 15:31 syslog.3.gz
-rw-r----- 1 syslog adm       618577 Mar 18 14:26 syslog.2.gz
drwxr-xr-x 2 root   root        4096 Mar 19 03:36 upstart
-rw-r----- 1 root   adm          640 Mar 19 05:38 apport.log.1
-rw-r----- 1 root   adm            0 Mar 19 05:42 apport.log
drwxr-xr-x 2 root   root        4096 Mar 19 05:42 cups
-rw-r----- 1 syslog adm  10098462720 Mar 19 05:42 syslog.1
-rw-rw-r-- 1 root   utmp      292292 Mar 19 06:00 lastlog
-rw------- 1 root   utmp        3072 Mar 19 17:37 btmp
-rw-r--r-- 1 root   root       27645 Mar 19 17:58 Xorg.0.log.old
-rw-r--r-- 1 root   root        1395 Mar 19 17:58 gpu-manager.log
-rw-r--r-- 1 root   root         549 Mar 19 17:58 boot.log
-rw-r--r-- 1 root   root          30 Mar 19 17:58 prime-supported.log
-rw-r--r-- 1 root   root          55 Mar 19 17:58 prime-offload.log
drwxr-xr-x 2 root   root        4096 Mar 19 17:58 lightdm
-rw-r--r-- 1 root   root       26952 Mar 19 17:58 Xorg.0.log
-rw-r----- 1 syslog adm      2001426 Mar 19 23:27 kern.log
-rw-r--r-- 1 root   root      110101 Mar 19 23:47 dpkg.log
-rw-r----- 1 syslog adm      1882892 Mar 20 00:17 syslog
-rw-r----- 1 syslog adm       136967 Mar 20 00:17 auth.log
-rw-rw-r-- 1 root   utmp      128256 Mar 20 00:34 wtmp
```

```
$ ls -lSr /var/log
total 9869100
-rw-r----- 1 root   adm            0 Mar 19 05:42 apport.log
-rw-r--r-- 1 root   root          30 Mar 19 17:58 prime-supported.log
-rw-r----- 1 root   adm           31 Oct 22 19:57 dmesg
-rw-r--r-- 1 root   root          55 Mar 19 17:58 prime-offload.log
-rw-r--r-- 1 root   root         136 Feb  4  1907 alternatives.log.5.gz
-rw-r--r-- 1 root   root         137 Feb 14 03:09 alternatives.log.3.gz
-rw-r--r-- 1 root   root         162 Feb 29 18:12 alternatives.log.1
-rw-r----- 1 root   adm          255 Mar 13 18:03 apport.log.3.gz
-rw-r----- 1 root   adm          305 Feb 20 23:22 apport.log.7.gz
-rw-r----- 1 root   adm          307 Mar 17 03:55 apport.log.2.gz
-rw-r----- 1 root   adm          324 Feb 25 02:16 apport.log.5.gz
-rw-r--r-- 1 root   root         335 Feb 10 20:54 dpkg.log.4.gz
-rw-r----- 1 root   adm          397 Mar  3 05:06 apport.log.4.gz
-rw-r--r-- 1 root   root         446 Feb 21 01:17 dpkg.log.2.gz
-rw-r--r-- 1 root   root         468 Feb  7 15:46 alternatives.log.4.gz
-rw-r--r-- 1 root   root         549 Mar 19 17:58 boot.log
-rw-r----- 1 root   adm          573 Feb 23 01:57 apport.log.6.gz
-rw-r--r-- 1 root   root         600 Feb 18 23:42 alternatives.log.2.gz
-rw-r----- 1 root   adm          640 Mar 19 05:38 apport.log.1
-rw-r--r-- 1 root   root         712 Feb  4  1907 dpkg.log.6.gz
-rw-r--r-- 1 root   root         887 Mar 13 18:17 alternatives.log
-rw-r--r-- 1 root   root        1007 Feb  4  1907 alternatives.log.6.gz
-rw-r--r-- 1 root   root        1395 Mar 19 17:58 gpu-manager.log
-rw------- 1 root   utmp        1920 Feb 23 17:23 btmp.1
-rw-r----- 1 syslog adm         2620 Feb 22 03:17 auth.log.4.gz
-rw------- 1 root   utmp        3072 Mar 19 17:37 btmp
-rw-r--r-- 1 root   root        3447 Feb  4  1907 alternatives.log.7.gz
-rw-r--r-- 1 root   root        4079 Feb 28 00:36 fontconfig.log
drwxr-xr-x 2 root   root        4096 Mar 19 03:36 upstart
drwxr-x--- 2 root   adm         4096 Feb  4  1907 unattended-upgrades
drwxr-xr-x 2 root   root        4096 Mar 19 17:58 lightdm
drwxr-xr-x 2 root   root        4096 Feb  4 01:20 installer
drwxr-xr-x 3 root   root        4096 Oct 22 20:19 hp
drwxr-xr-x 2 root   root        4096 Oct 22 19:57 fsck
drwxr-xr-x 2 root   root        4096 Feb 23 15:59 dist-upgrade
drwxr-xr-x 2 root   root        4096 Mar 19 05:42 cups
drwxr-xr-x 2 root   root        4096 Mar  1 16:58 apt
-rw-r----- 1 syslog adm         5140 Mar  8 03:44 auth.log.2.gz
-rw-r--r-- 1 root   root        7274 Feb  4  1907 dpkg.log.7.gz
-rw-r--r-- 1 root   root        7899 Feb 19 01:31 dpkg.log.3.gz
-rw-r----- 1 syslog adm         7938 Feb 28 01:10 auth.log.3.gz
-rw-r--r-- 1 root   root       16823 Feb  9 00:48 dpkg.log.5.gz
-rw-r--r-- 1 root   root       22042 Feb  6 23:22 Xorg.1.log
-rw-r--r-- 1 root   root       26952 Mar 19 17:58 Xorg.0.log
-rw-r--r-- 1 root   root       27645 Mar 19 17:58 Xorg.0.log.old
-rw-r--r-- 1 root   root       32032 Mar  1 18:21 faillog
-rw-r----- 1 syslog adm        37796 Mar 13 01:56 auth.log.1
-rw-r----- 1 syslog adm        40868 Mar 16 22:52 syslog.4.gz
-rw-r--r-- 1 root   root       54474 Feb 29 18:20 dpkg.log.1
-rw-r----- 1 syslog adm        55516 Mar 14 00:22 syslog.6.gz
-rw-r----- 1 syslog adm        60178 Mar 13 01:59 syslog.7.gz
-rw-r----- 1 syslog adm        61418 Mar 17 15:31 syslog.3.gz
-rw-r--r-- 1 root   root       70962 Feb  4  1907 dpkg.log.8.gz
-rw-r--r-- 1 root   root       72222 Oct 22 20:01 bootstrap.log
-rw-r--r-- 1 root   root      110101 Mar 19 23:47 dpkg.log
-rw-r----- 1 syslog adm       120120 Mar 15 17:10 syslog.5.gz
-rw-r----- 1 syslog adm       120712 Feb 22 03:15 kern.log.4.gz
-rw-rw-r-- 1 root   utmp      128256 Mar 20 00:34 wtmp
-rw-r----- 1 syslog adm       136967 Mar 20 00:17 auth.log
-rw-rw-r-- 1 root   utmp      144384 Mar  1 06:23 wtmp.1
-rw-r----- 1 syslog adm       199371 Mar  7 17:12 kern.log.2.gz
-rw-rw-r-- 1 root   utmp      292292 Mar 19 06:00 lastlog
-rw-r----- 1 syslog adm       512406 Feb 28 01:08 kern.log.3.gz
-rw-r----- 1 syslog adm       618577 Mar 18 14:26 syslog.2.gz
-rw-r----- 1 syslog adm       658804 Mar 13 00:50 kern.log.1
-rw-r----- 1 syslog adm      1882892 Mar 20 00:17 syslog
-rw-r----- 1 syslog adm      2001426 Mar 19 23:27 kern.log
-rw-r----- 1 syslog adm  10098462720 Mar 19 05:42 syslog.1
```

These are anomalies from the first output:

```
drwxr-xr-x 3 root   root        4096 Oct 22 20:19 hp
-rw-r--r-- 1 root   root       72222 Oct 22 20:01 bootstrap.log
-rw-r----- 1 root   adm           31 Oct 22 19:57 dmesg
drwxr-xr-x 2 root   root        4096 Oct 22 19:57 fsck
```

This machine wasn't even built in October ... of any year! It was ordered last week of January this year and received it first week of Feb. :-k

---

### Post by sudodus on 2016-03-19
The big bad file has a recent date stamp. I don't *think* the files with an ancient date stamp cause your problems.

---

### Post by Bucky Ball on 2016-03-19
I think you're right, the culprit the recent /var/log/syslog.1. That file is 10.1Gb! It's going now then a reboot.

...

And done and my / partition is now back to 6Gb used and 13Gb free. :D

I tried to open the file to see what was happening there but nothing happened. Machine just started spinning fans and locked up for a couple of minutes then back to normal. File probably too big. Then wouldn't let me delete after that. So I rebooted, killed, rebooted again and all is well.

Solved, until next time, but I'll keep an eye on this and see if I can spot what's filling it up. Might be clues in syslog file remaining. Might be caused by writing there every time USB connects and reconnects. Questions for another day. Back to it.

Thanks a heap for your ideas, suggestions and help. ;)
...

Not so fast! Syslog.1 has reappeared five or ten minutes after deleting it and is already 2mb. The file won't post here as too large. Will keep watch and see if any bigger after a couple of hours. :-k

---

### Post by sudodus on 2016-03-19
You are welcome :-)

---

### Post by Bucky Ball on 2016-03-19
Not sure if you saw my last edit. syslog.1 reappeared and within ten minutes is 2mb and full of stuff again. Too large to post here as a .gz or txt. I'll keep watching it over next few hours and see what gives. Do you also have a syslog.1 around that size or at all? Something appears to be not right.

* Hmm. Just checked on the laptop and the syslog.1 there is a quarter of the size and that machine is on for weeks on end.

---

### Post by sudodus on 2016-03-19
Maybe you can use the tail command in a wide terminal window and see the last few lines

```
tail /var/log/syslog.1
```

---

### Post by Bucky Ball on 2016-03-19
This what I got:

```
$ tail /var/log/syslog.1
Mar 20 00:53:31 UStudio systemd[1]: Stopped User Manager for UID 110.
Mar 20 00:53:31 UStudio systemd[1]: Removed slice user-110.slice.
Mar 20 00:56:29 UStudio anacron[680]: Job `cron.daily' started
Mar 20 00:56:29 UStudio anacron[1713]: Updated timestamp for job `cron.daily' to 2016-03-20
Mar 20 00:56:30 UStudio cracklib: no dictionary update necessary.
Mar 20 00:56:30 UStudio systemd[1]: Stopping CUPS Scheduler...
Mar 20 00:56:30 UStudio systemd[1]: Stopped CUPS Scheduler.
Mar 20 00:56:30 UStudio systemd[1]: Started CUPS Scheduler.
Mar 20 00:56:30 UStudio colord[761]: (colord:761): Cd-WARNING **: failed to get session [pid 1905]: No such device or address
Mar 20 00:56:30 UStudio rsyslogd: [origin software="rsyslogd" swVersion="8.12.0" x-pid="705" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
```

As just edited in my last post, checked on another machine that is on for days at a time and syslog.1 is quarter of the size.

---

### Post by sudodus on 2016-03-19
This is my current **syslog.1** in a computer that shutdown and cold boot daily:

```
$ [COLOR="#0000FF"]ls -lh /var/log/syslog.1[/COLOR]
-rw-r----- 1 syslog adm [COLOR="#cc0000"]**759K**[/COLOR] mar 19 00:25 /var/log/syslog.1

$ [COLOR="#0000FF"]tail /var/log/syslog.1[/COLOR]
Mar 19 00:15:52 xenial32 kernel: [  206.968632] sd 5:0:0:0: [sdd] Start/Stop Unit failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 19 00:17:01 xenial32 CRON[2632]: (root) CMD (/root/idling)
Mar 19 00:17:01 xenial32 CRON[2633]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 19 00:17:01 xenial32 CRON[2631]: (CRON) info (No MTA installed, discarding output)
Mar 19 00:17:45 xenial32 anacron[744]: Job `cron.daily' started
Mar 19 00:17:45 xenial32 anacron[2648]: Updated timestamp for job `cron.daily' to 2016-03-19
Mar 19 00:23:03 xenial32 ntpd[1638]: xxxxx local addr xxxxx -> <null>
Mar 19 00:23:09 xenial32 ntpd[1638]: xxxxx local addr xxxxx -> <null>
Mar 19 00:23:16 xenial32 ntpd[1638]: xxxxx local addr xxxxx -> <null>
Mar 19 00:25:02 xenial32 rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="735" x-info="http://www.rsyslog.com"] rsyslogd was HUPed


```

---

### Post by Bucky Ball on 2016-03-19
Thanks for that. [This post]("http://ubuntuforums.org/showthread.php?t=1384521&page=2&p=12235341&viewfull=1#post12235341") might throw some light on my problem. I seem to be getting 'HUPed'.

---

### Post by sudodus on 2016-03-19
I think we need help from someone who is good at reading log files :-)

---

### Post by Bucky Ball on 2016-03-20
You could be right.

Anyhow, no change last night or so far today. syslog.1 is there and still 2mb, no change. Positive signs. I'm busily working away at other things but did have a quick check prior to having a break and found this in syslog, not syslog.1:

> Mar 20 14:58:06 UStudio systemd-tmpfiles[1618]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.

Hmm. Here's that file. 

```
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.

# See tmpfiles.d(5) for details

v /var 0755 - - -

L /var/run - - - - ../run

d /var/log 0755 - - -
f /var/log/wtmp 0664 root utmp -
f /var/log/btmp 0600 root utmp -

d /var/cache 0755 - - -
```

If my calculations are correct, presume syslog means this line:

> d /var/log 0755 - - -

Off-topic, don't need support on this thread with it, just mentioning. There is nothing untoward happening and would imagine nothing to do with the original issue so probably ignore is best plan. At least for now. :)

---

### Post by matt_symes on 2016-03-20
Hi

I suspect that the "109 years" problem may have been called by timesyncd going bang maybe and not getting time from an ntp server.

Need more info from that errant syslog.1 file to really know what the problem is though.

Kind regards

---

### Post by Bucky Ball on 2016-03-20
> **matt_symes said:**
> Hi

I suspect that the "109 years" problem may have been called by timesyncd going bang maybe and not getting time from an ntp server.

Need more info from that errant syslog.1 file to really know what the problem is though.

Thanks matt_symes. Wish I could give you that info, and I've tried, but at 2mb I can't seem to upload it anyway to the forums. There's a ton of info in there to sift through!

* Bingo. A tar.gz file below.

---

### Post by Bucky Ball on 2016-03-20
PS: Wouldn't worry about the 109 year timestamp issue. Generated from when the BIOS kept setting its own random time and Ubuntu was using that when I first got the machine. I'd boot and try to go to a web page and all the certificates would be wrong and couldn't do anything. I finally realised it's because the date was 13 July 2043 or some other random date.

That has been fixed awhile, but the timestamp on some files still relates to when they were last modified (the machine thinks 109 years ago). If I open them the timestamp corrects itself. :)

Also a bump in case you missed the fact that I tar.gz-ded the syslog1 file and attached to last post.

---

