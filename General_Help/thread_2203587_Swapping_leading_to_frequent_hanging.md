---
title: "Swapping leading to frequent hanging"
date: 2014-02-04
forum: General Help
---

### Post by divine shine on 2014-02-04
I have my ubuntu installation alongside Windows. Initially it was simply a try-out installation to learn how the OS works, but later on I started loving the system more and migrated my full-time works to ubuntu. 8-)

During the switch, I realized that my installation wasn't capable of full-time use since it was installed without separate mount points for root and home directories. I used gParted to create separate mount points for my root and home directories and also increased the space allocated to the root, home directories as well as the swap partition.

Initially, I had a 2GB swap and then I increased it to 4GB. As of now, gParted shows me 4GB of swap space; But System Monitor shows me only 2GB of swap space. I have no idea what has caused this problem.

Now, I have 8GB of RAM, but can't afford 16GB of swap (considering the optimum swap allocation is 2x RAM).

After the re-allocation of memory, my system swaps out in a period of 2 hours and then hangs up. I'll have to do a emergency restart to start over again.

I have no idea why this is happening and what is causing this problem. My inference is it is because of the swapping out of the memory. But the best part is my RAM usage is always around 2-2.5GB/7.7GB when the swap memory is filled up. I looked up solutions for cleaning up the swap memory, but was in vain.

Does anyone here have experienced a similar problem. Any help with this regard would be greatly appreciated! This problem has been tormenting me for months now. :confused:

---

### Post by tgalati4 on 2014-02-04
Open a terminal and post the output of:

```
uname -a
free
```

Sounds like a 32-bit problem.  Did you load the 32-bit or 64-bit version?

1xRAM for swap size is needed if you want to hibernate your system.  Hibernate takes the RAM footprint and copies it to the hard drive so when you wake up the entire contents of RAM gets reloaded.  Sleep or suspend keeps power running to the RAM so that it wakes in 3 to 8 seconds.  This works OK, unless you run out of battery power or if there is a power glitch, so hybrid mode was created.  Keep in RAM and dump to hard disk as a precaution.  If your swap is too small then hibernate won't work or it will lock up.  The fact that your RAM doesn't exceed 2.5GB of use is consistent with a 32-bit installation.

---

### Post by divine shine on 2014-02-05
Thank you for the reply tgalati4.

Here's the output you requested :
```

shine@divine-lap:~$ uname -a
Linux divine-lap 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
shine@divine-lap:~$ free
             total       used       free     shared    buffers     cached
Mem:       8040848    5446116    2594732          0     167076    3595468
-/+ buffers/cache:    1683572    6357276
Swap:      2096124          0    2096124

```

This is just after a restart, so, swapping hasn't started out yet.

I have a 64-bit system. I've had my system working properly initially with the underrated configurations. The problems arouse when I made changes to the directories(partitions) on my hard-drive.

I'm well aware of the hibernate, sleep, suspend and hybrid sleep options. But I don't use any of these. The systems sleeps occasionally when I leave my desk for other work. Otherwise, I don't need any of these options. I stated the RAM usage to reveal the fact that the swapping was not occurring due to insufficient RAM. The RAM is not always consistent at 2.5GB. It varies between 2-2.5GB when the freeze of swap at 2GB occurs.

But according to gParted, my partitions shows 4GB of swap area. But still, my system fills up at 2GB and freezes at that point.

---

### Post by buzzingrobot on 2014-02-05
You said the system "swaps out" after 2 hours.  What, exactly, happens? Does the swap partition suddenly fill and the system stop? Or, does swap  grow steadily?

It's curious because swap use should be minimal, or nonexistent, until memory use exceeds physical ram.  Then, something will temporarily be written out to swap. When RAM use drops down again, swap use will end.

The 5+ gigs of RAM used immediately after a reboot draws my attention. It's five times what I see. Are you autostarting anything unusual?

What does System Monitor say are the most memory-hungry processes after a reboot?

---

### Post by deadflowr on 2014-02-05
> During the switch, I realized that my installation wasn't capable of  full-time use since it was installed without separate mount points for  root and home directories

Having a single partition won't affect your ability to use Ubuntu.

That aside, it's seems quite troubling that your swapping as much as you are.
Did you increase swappiness or something?
+1 to buzzingrobot's question of what are you starting up at launch?
And what apps do you run that eat so much?

---

### Post by divine shine on 2014-02-06
> **buzzingrobot said:**
> You said the system "swaps out" after 2 hours.  What, exactly, happens? Does the swap partition suddenly fill and the system stop? Or, does swap  grow steadily?

No. The swap grows steadily over time. I don't exactly know when it starts swapping, but the system freezes approximately 2 hours after boot.

> **buzzingrobot said:**
> It's curious because swap use should be minimal, or nonexistent, until memory use exceeds physical ram.  Then, something will temporarily be written out to swap. When RAM use drops down again, swap use will end.

This was my idea of swap too. But now, my idea is shaken. swap simply fills up with loads of space free on my RAM.

> **buzzingrobot said:**
> The 5+ gigs of RAM used immediately after a reboot draws my attention. It's five times what I see. 

It wasn't exactly 'immediately' after reboot. It was like around 15minutes or so after boot.

Here's the output of 'free' immediately after reboot.

```

shine@divine-lap:~$ free
             total       used       free     shared    buffers     cached
Mem:       8040848    1515896    6524952          0     117324     662820
-/+ buffers/cache:     735752    7305096
Swap:      2096124          0    2096124

```

> **buzzingrobot said:**
> Are you autostarting anything unusual?

What does System Monitor say are the most memory-hungry processes after a reboot?

I don't have anything 'unusal' that autostarts. I've got GNOME-Shell, dropbox and variety with maximum memory eat-up immediately after reboot.
This is how I saw my 'processes' tab, in descending order of Memory Used, in my System Monitor right after reboot :
GNOME-shell : 89.1MiB
dropbox : 51.0MiB
variety : 42.1MiB
evolution-calendar-factory : 39.0MiB
ubuntuone-syncdaemon : 32.2MiB

I don't think there's anything unusual in any of the above processes either.

> **deadflowr said:**
> Having a single partition won't affect your ability to use Ubuntu.

I know. But the initial configuration for my system was a 10GB on the whole - for both the home and root partitions. Initially that was more than enough since I didn't use Ubuntu much. But when I started using Ubuntu, my home directory filled up very fast. That is when I expanded the memory allocated and created proper partitions for each of the directories.

> **deadflowr said:**
> it's seems quite troubling that your swapping as much as you are.
Did you increase swappiness or something?

Yes, I did. When I increased the space allocated for the directories. I did increase my swap from 2GB to 4GB. But the change hasn't been yet reflected on my System Monitor. Though gParted shows 4GB of swap area allocated, my System Monitor still shows me only 2GB and I think that is what is creating this problem.

Thank you for your replies buzzingrobot and deadflowr. Appreciate the help. :)

---

### Post by buzzingrobot on 2014-02-06
Swap does work the way you think.  If you show swap usage steadily increasing, *something* is using it.  You should see also your RAM use pretty well maxed out at that time. Or the system, for some reason, is measuring the wrong thing.

When you said you created new partitions for root and home, did you edit /etc/fstab to reflect those changes?  (Just to be sure, when you said you used Gparted to create new "mount points", you created new *partitions* for each?  Fstab needs to reflect those changes.)

---

### Post by sudodus on 2014-02-06
I suggest that you show us the structure of your swapping. Please post the output of each of the following commands

```
swapon -s
grep swap /etc/fstab
sudo blkid|grep swap
cat /proc/sys/vm/swappiness
sudo parted -l
```

See also this link [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by divine shine on 2014-02-06
> **buzzingrobot said:**
> Swap does work the way you think.  If you show swap usage steadily increasing, *something* is using it.  You should see also your RAM use pretty well maxed out at that time. Or the system, for some reason, is measuring the wrong thing.

Yes, I know. That is exactly why I mentioned that I have an 8GB RAM and when the system freezes, the RAM usage is around 2-2.5GB. I don't do much RAM/memory intensive work. Mostly, it's just surfing the web. Occasionally, I use a few simulators when I'm developing apps. But even during that time, the RAM usage never crosses 4.5GB. Another interesting thing I noticed was that the 'free' command does not reflect the amount that is reflected by the System Monitor. The 'free' command showed 2.75GB of usage when the System Monitor was on 1.2GB. Is that supposed to be normal?

> **buzzingrobot said:**
> When you said you created new partitions for root and home, did you edit /etc/fstab to reflect those changes?  (Just to be sure, when you said you used Gparted to create new "mount points", you created new *partitions* for each?  Fstab needs to reflect those changes.)

Yes. I edited the /etc/fstab to reflect the /home and /root directory changes. But I don't think I had to change the swap area's entry (at least I don't remember doing it). I just moved the partitions using gParted to create some unallocated space after swap and extended the swap area. gParted does show 4GB of linux-swap area, but System Monitor shows only 2GB. That probably might be the problem too. Something is not measuring right!

---

### Post by divine shine on 2014-02-06
> **sudodus said:**
> I suggest that you show us the structure of your swapping. Please post the output of each of the following commands

```
swapon -s
grep swap /etc/fstab
sudo blkid|grep swap
cat /proc/sys/vm/swappiness
sudo parted -l
```


Here's the output of the above commands :

```

shine@divine-lap:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda9                               partition    2096124    0    -1

shine@divine-lap:~$ grep swap /etc/fstab
# swap was on /dev/sda9 during installation
UUID=94d2a8ce-ec9c-4123-9681-a5ad81f7eff0 none            swap    sw              0       0

shine@divine-lap:~$ sudo blkid|grep swap
[sudo] password for shine: 
/dev/sda9: UUID="94d2a8ce-ec9c-4123-9681-a5ad81f7eff0" TYPE="swap" 

shine@divine-lap:~$ cat /proc/sys/vm/swappiness
10

shine@divine-lap:~$ sudo parted -l
Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  525MB   524MB   fat32           EFI system partition          boot
 2      525MB   567MB   41.9MB  fat32           Basic data partition          hidden
 3      567MB   701MB   134MB                   Microsoft reserved partition  msftres
 4      701MB   1226MB  524MB   ntfs            Basic data partition          hidden, diag
 5      1226MB  93.7GB  92.4GB  ntfs            Basic data partition          msftdata
 6      93.7GB  452GB   359GB   ntfs            Basic data partition          msftdata
 7      452GB   468GB   16.1GB  ext4                                          msftdata
 8      468GB   485GB   16.1GB  ext4                                          msftdata
 9      485GB   489GB   4295MB  linux-swap(v1)
10      489GB   500GB   11.0GB  ntfs            Microsoft recovery partition  hidden, diag


Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? OK                                                             
Warning: Not all of the space available to /dev/sdb appears to be used, you can fix the GPT to use all of the space (an extra 45756080 blocks) or
continue with the current setting? 
Fix/Ignore? Ignore                                                        
Model: ATA LITEONIT LMT-32L (scsi) //This is my SSD drive I have on my system. Haven't used it though.
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  8589MB  8588MB               Basic data partition

```

---

### Post by sudodus on 2014-02-06
I would use the following commands to try to fix the swap.

Turn off swap

```
sudo swapoff -a
```

And re-make the swap (to use all 4 GB of the partition)

```
sudo mkswap -U 94d2a8ce-ec9c-4123-9681-a5ad81f7eff0 /dev/sda9
```

Try to turn it on

```
sudo swapon -a
```

And run those previous commands again (from post #8). I hope that all four gigabytes will be available now.

-o-

I see that you have decreased the swappiness to 10 (which is the minimum, many people are happy with the default value, 60). But that should not cause your problem.

---

### Post by divine shine on 2014-02-06
Thank you so much sudodus. That refreshed my swap area. System Monitor now shows 4GB of swap area. Now to wait and see whether the swapping happens anymore.

> **sudodus said:**
> I see that you have decreased the swappiness to 10 (which is the minimum, many people are happy with the default value, 60). But that should not cause your problem.

I have no idea what swappiness is all about and I haven't changed the value. How can I change something I don't even know of? ;) :P

Would that be the cause of my problem? Should I try and reset the swappiness to its default value (i.e., 60)?

Though, I don't think that might be the problem. I've made that deduction from the fact that my swap used to 'fill up' and freeze my system. And during this process, there used to be lots of free space on my RAM. So, if the swap was actually measuring the right thing and working the way I think it should be, i.e., using the swap only when the RAM memory is insufficient for a process to work and freeing swap as soon as there's free space on the RAM to accommodate the process. If that was the way the swap was supposed to work, then my swap was acting really weird!

Well, now that it atleast shows me the exact amount of memory, let's hope the problem is fixed! :)

Thanks for the support again. :)

---

### Post by deadflowr on 2014-02-06
> I have no idea what swappiness is all about and I haven't changed the value. How can I change something I don't even know of

Here
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

easier to read a well put together link than rewrite it for you.

---

### Post by divine shine on 2014-02-06
I did read this earlier when sudodus posted, but before that I had no idea what that was. I came across the term for the first time today when I was going through the link. ;)

---

### Post by divine shine on 2014-02-06
I'd like to inform with regret that my system still is swapping even after fixing the missing swap area.

So we can rule out the problem being caused by the missing swap area.

Anyone, any ideas?? :/

---

### Post by sudodus on 2014-02-07
> **divine shine said:**
> Would that be the cause of my problem? Should I try and reset the swappiness to its default value (i.e., 60)?


Yes, I think it is worth trying with swappiness=60. Even if we don't understand why, it is fairly easy to try, and maybe ...

> **divine shine said:**
> I'd like to inform with regret that my system still is swapping even after fixing the missing swap area.

So we can rule out the problem being caused by the missing swap area.

Anyone, any ideas?? :/

Please keep a system monitor on, and check which program is active, when the RAM usage is growing. There are graphical system monitors, and there are ***top*** and ***htop***, that run in terminal windows.

Edit: You can also install and try ***iotop***, which needs sudo

```
sudo iotop
``` or 
```
sudo iotop -o
```

---

### Post by divine shine on 2014-02-10
> **sudodus said:**
> Yes, I think it is worth trying with swappiness=60. Even if we don't understand why, it is fairly easy to try, and maybe ...

That'd only increase the amount of processes that uses the swap space right? We want lesser usage of swap space.

> **sudodus said:**
> Please keep a system monitor on, and check which program is active, when the RAM usage is growing. There are graphical system monitors, and there are ***top*** and ***htop***, that run in terminal windows.

I've been opening up my 'System Monitor' before any other programs after boot up for the past few months! 'System Monitor' is graphical enough to let you know that your swap is filling up!! Unfortunately, there's no one process that doesn't use the swap. Last night I tried browsing the net alone with nothing else, and watching videos without anything else beside that too. But both still didn't prevent the system from freezing.

---

### Post by sudodus on 2014-02-10
> **divine shine said:**
> That'd only increase the amount of processes that uses the swap space right? We want lesser usage of swap space.

The system might get choked somehow, if it does not start swapping early enough. I can't say that higher swappiness would help, only that it might be worth trying.
> 
I've been opening up my 'System Monitor' before any other programs after boot up for the past few months! 'System Monitor' is graphical enough to let you know that your swap is filling up!! Unfortunately, there's no one process that doesn't use the swap. Last night I tried browsing the net alone with nothing else, and watching videos without anything else beside that too. But both still didn't prevent the system from freezing.

There seems to be something very wrong with your system.

Is there any chance, that you can determine, if it is a hardware or software problem?

---

### Post by divine shine on 2014-02-18
> **sudodus said:**
> There seems to be something very wrong with your system.

I know. And that's exactly why I'm here seeking help. None of my reading elsewhere has helped at all.

> **sudodus said:**
>  Is there any chance, that you can determine, if it is a hardware or software problem?

I just don't know what exactly is the problem. I can't determine a swap error since it resides in the hard-drive and the possibility is less probable. But all other components seem to be working fine according to the hardware diagnostic toll that is provided by the manufacturer of my system. Do you have any suggestions?

---

### Post by sudodus on 2014-02-19
- I browsed the thread quickly and found nothing about testing the RAM. Maybe you can run memtest (from the grub menu). It should be run for hours and one error is too much.

- Try with higher swappiness.

- Try running another system (that has swap) in the same computer, for example from a USB 3 pendrive or another hard disk drive.

---

### Post by divine shine on 2014-03-18
I finally figured out what was wrong with my system. I think it was GNOME shell that was swapping up. I reached this conclusion because I tried killing and restarting GNOME shell; though the system was still swapping, it had reset from the beginning. So, I think the issue is with GNOME shell. I haven't tried any other desktop environments yet.

My system is pretty screwed up as of now. I tried installing the Linux Deepin desktop environment which was still based on the raring packages/repositories and that seriously messed up my system. I can't seem to use my "apt-get" at all now. So, I can't basically add or remove anything from my system. Since I myself brought all this trouble on myself, I thought it would be best to amend it by doing a fresh install of Ubuntu on my home partition when Ubuntu 14.04LTS is released in less than a month from now. I'll update as soon as I do a fresh install of Ubuntu 14.04LTS and let's just wait and see whether this is a bug in the GNOME shell or was it just a bug from conflicting packages in my installation.

I would like to thank all of you awesome guys who has helped me out with this problem especially sudodus. :)

---

### Post by efflandt on 2014-03-19
With 8 GB RAM I never even configure any swap on my 64-bit 12.04 desktop or 13.10 laptop because they do not hibernate. I don't even have swap on my 2 GB tablet PC because it boots Linux from SDHC (Win7 Pro boots from its 32 GB SSD), but with 1 GHz 2 core cpu it does not run many programs simultaneously. Those systems all use default Unity desktop.

---

### Post by buzzingrobot on 2014-03-19
Regardless of the amount of RAM in a system, swap will be used if the amount of code and data in play exceed RAM.  That's why it was included in Unix in the first place.  Re-purposing the swap partition for hibernation is a considerably more recent thing.

Ordinary desktop and laptop users these days usually seldom push their hardware to its limits, but it still serves its purposes. I routinely had the machine swapping on an 8-gig MacBook when editing/managing images in Photoshop and Lightroom.

---

### Post by mcduck on 2014-03-19
+1 to this. Removing swap doesn't improve your computer's performance in any way (although it might save bit of disk space if you are really short on space and are absolutely sure you're not going to use the computer for anything that might exceed it's available RAM, or need swap for other reasons.

Furthermore, swapping doesn't decrease the performance either. (That's just a common misconception caused by sluggish performance and swapping happening at the same time). In the situation where swap is used, your system has already ran out of available RAM, and wouldn't be able to operate at all if it didn't have the swap available. And of course a computer operating slowly because it needs to use hard drive space to extend memory is still performing bette than a computer that fails to do the job at all... ;)

So, in almost every possible case, swapping doesn't cause slowness, instead some other problem causes slowness *and* swapping.

---

### Post by divine shine on 2014-03-19
I read pretty too much about swapping, but I knew from the start that swapping was used similar to the 'pagefile.sys' in Windows which was supposed to use the swap partition as virtual memory in the absence of sufficient physical memory. But my concepts were all simply proved wrong when my system started swapping at less than 30% of physical memory usage. I was completely wonder-struck at this very weird behaviour of my system.

Until recently, I kind of figured out the culprit. It was during these recent swapping periods that my GNOME-shell session crashed and restarted(which it was never supposed to be doing in the first place) on its own. I then noticed that the swap usage had gone down from 27% to just 3% though it still continued swapping. I tried manually killing GNOME-shell and it restarted on its own. This time the swap was reset to 0% though it still was continuing to swap (noticed using the 'top' monitor). From all those observations, I concluded that GNOME-shell was the one to blame.

But unfortunately, I could not confirm whether this was a bug in the GNOME-shell's code or was it just me,  because, though I've been facing this problem for quite some time, I could make this observation only now; which was after I screwed up my system pretty bad recently. Like I mentioned in my comment #21, I installed conflicting desktop environments that was not supposed to be actually mixed up together. So, that screwed up system in such a way that I couldn't even use my package-manager 'apt-get' anymore. Though I was facing this swapping problem from long before this screw-up, I can't confirm whether it was caused due to this bug or something else. That is why I thought of waiting for the LTS release, do a fresh install and then see whether I face the same problem. If it did, then I could strongly confirm it is a bug in GNOME-shell and then file a bug at Launchpad.

Thanks for your input guys. :)

---

