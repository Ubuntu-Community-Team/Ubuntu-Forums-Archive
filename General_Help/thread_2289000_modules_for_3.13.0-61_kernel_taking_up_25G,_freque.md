---
title: "modules for 3.13.0-61 kernel taking up 25G, frequent low space warning on root"
date: 2015-07-31
forum: General Help
---

### Post by EarlsFurniture on 2015-07-31
I have several machines running 12.04. On one of them, I keep getting a 'low disk space on root' error. Checking df, reported 100% usage on that partition. I noticed I had partitioned root with about 15gb, which I thought should be sufficient, but I went ahead and used Gparted (in a live session of course) to move partitions and resize root to about 32gb. Within a few seconds of rebooting, again, I get the low space error and checking df tells me I'm still at 100% usage with now 32gb!!

Note, every other machine, on 12.04 running various kernels (none of them 3.13.0-61) reports no more than about 850mb of space usage for /lib as a whole.

A check with du revealed the culprit to be /lib/modules/3.13.0-61 and its subdirectories taking up 25GB! (yes, I'm using the Trusty HWE stack on this machine, hence the 3.13 kernel instead of 3.2)
The odd thing is that the current running kernel, and the highest installed is 3.13.0-59. I've never seen any offer to upgrade to -61 yet.

Is the -61 kernel building itself in the background for faster installation later? Is the huge space requirement part of the build process? Why have I never noticed this before? Perhaps there is a bug in this new kernel's build process that causes it to not clean up after itself as it goes along.

Because of this space issue, I can't do upgrades, or even remove unneeded software. (I recently switch to virtualbox from vmware on this machine and do not have the space to remove vmware)

Any ideas?

---

### Post by Simon_Tomoko on 2015-07-31
What is the output of the command; [COLOR=#000000][FONT=monospace]df -h  

[/FONT][/COLOR]

---

### Post by EarlsFurniture on 2015-07-31
As I noted, 100% on /

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        32G   30G     0 100% /
```

---

### Post by oldfred on 2015-07-31
I prefer to use synaptic, so I can see more details. But had let my system grow to too many kernels. I try to keep 2 but let it grow a couple then purge.

 cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.13.0-{XX,XX,XX,XX,XX,XX}-generic
Example, I just ran this and it worked fine:
sudo apt-get purge linux-image-3.13.0-{54,55,57}-generic

I do have -61 installed.
fred@trusy-ar:/boot$ uname -a
Linux trusy-ar 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:21:34 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

I use about 13GB, in working install, others have nothing and are tiny, but I do keep data in data partition:
fred@trusy-ar:~$ df -Th | grep sd | sort
/dev/sda1      vfat      500M   16M  484M   4% /boot/efi
/dev/sda3      ext4       24G   13G   11G  54% /
/dev/sdb3      ext4       24G  4.3G   19G  19% /media/fred/vivid
/dev/sdb4      ext4      385G   83G  283G  23% /mnt/data
/dev/sdb5      ext4       28G  3.5G   23G  14% /mnt/backup
/dev/sdb9      ext4       23G  3.7G   19G  17% /media/fred/wily_b

       Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by EarlsFurniture on 2015-07-31
Thank you very much for that detailed reply but I already delete old kernels and only keep two at a time. (when I switch to an HWE stack, I also keep one original level kernel just in case)

So that isn't the problem.

Specifically, the 3.13.0-61 kernel's lib/modules folder contains 25GB of data. No other kernel ever came close to this.

As well, dpkg reports that this kernel fails configuration and I can't seem to get it to configure.

Best I can figure out, the kernel was building itself in the background (without me telling it to), left a huge mess, and I can't get rid of it. (using dpkg to remove -61 can't be done because dpkg reports it as 'not configured so can't be removed')

Perhaps synaptic will do the trick, and I'll give it a shot,but I thought it was just a front-end. Since -61 isn't actually installed yet, I don't see how Synaptic or apt-get will be able to remove it.

I've never seen a kernel which hasn't even been offered for updating drop itself into / and have it's modules take up so many GB of space. As I noted, every other kernel, on this machine and others report at most &#8776; 850MB in that folder.

It makes no sense why that one kernel is so giant. Something is definitely wrong.

---

### Post by EarlsFurniture on 2015-07-31
So I tried Synaptic to re-install 3.13.0-61, however it complained about broken held packages. But there are not any.

So I tried Synaptic to remove instead, which it tried to do, but froze at depmod, tying up the system, and while still usable, I couldn't print while it was working. I killed all relevant processes to the removal, and I'll let it try again overnight. My next attempt will be to simply manually remove everything I can related to that kernel and see what happens and hopefully, not bork the system. (it shouldn't since it is still running -57)

I've searched the web to no avail. I can't seem to figure out what is causing /lib/modules to take up so much space.

---

### Post by EarlsFurniture on 2015-07-31
Update, so far, it appears that even though I prematurely killed synaptic and related processes that were removing the -61 kernel files, it seems it did the trick anyway and simply didn't return from execution. I can't find any files or folders related to that version kernel on the system. And now, I see that / is only using 5.5GB or about 19% which is significantly more reasonable. (/lib also reports as containing only 474M now)

So while the symptom of low disk space on / has been solved, the cause has not. I'll wait to see if -61 gets pushed again and starts taking up space. I attempted upgrade, dist-upgrade and aptitude full-upgrade and none reported any new kernels available. Synaptic still shows -61 as an option to install but I'm not about to test my luck.

---

### Post by oldfred on 2015-07-31
I cleaned up linux-image, but found that there were still headers.
       
Also headers:
dpkg -S /usr/src/*
Example, some did not have -generic at end:
sudo apt-get purge linux-headers-3.13.0-39-generic
Multiples at once, Not sure if you want to try -61, but I would only try with above by itself.
sudo apt-get purge linux-headers-3.13.0-{40,43,46,48,49,51,53,54,55}-generic
 Cleans up both /lib/modules & /usr/src

---

### Post by EarlsFurniture on 2015-07-31
Thank you, but this wasn't a headers problem either. It was a problem only in /lib/modules.
(Yes, headers are not removed when you remove a kernel, that has to be done separately, or at least I've had to every time)

---

