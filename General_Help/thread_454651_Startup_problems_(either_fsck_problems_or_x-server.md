---
title: "Startup problems (either fsck problems or x-server freezing)"
date: 2007-05-25
forum: General Help
---

### Post by knallkopf on 2007-05-25
Hi Ubuntu people

First of all: Great distro, great forums and sorry for asking questions that might have been already answered. I searched the forums, but didn't find a solution for my specific situation so far.

When I start my computer, I have basically two choices: Either I start in normal mode or in Recovery Mode. If I boot up Normal mode. everything works fine until X starts. I get the NVIDIA logo and then it's over. The screen just flickers, there is no reaction to keyboard or mouse and not even pressing the reset button helps.
But if I boot in Recovery Mode, everything works as it should, until it comes to fsck. For two of four hard drive partitions to be mounted, fsck tells me, there were inconsitencies. So I wait and wait (takes ten to twenty minutes) and then I get a maintainance shell. After mounting all drives (mount -a) and changing to runlevel 3 (init 3), I can login normally. Of course that is more like a hack, than a regular startup process. Also, I'm concerned, that I always have inconsitencies on my disks.

I already tried to run fsck manually from maintainance shell and virtual shell (without the checked fs being mounted of course), but still got errors on my next startup.

My hardware:
ASUS A8N-VM CSM (Motherboard with integrated NVIDIA GeForce GPU)
AMD Athlon 3700 (2200 Mhz)
1 GB RAM, 2 S-ATA HDs, 1 (old) IDE Disk, and some more that's not related, I suppose

I'm running Kubuntu 6.10 right now, kernel 2.6.17-11.
Has anyone a great tip for me or maybe running the same or similar hardware or having similar problems? I really apreciate your advice, because after months of trying and not succeeding in booting up my operating system in less than thirty minutes, I just need help :-)

Thanks in advance

---

### Post by mbradlcu on 2007-05-25
just for testing could you set the driver in the /etc/X11/xorg.conf to vesa from (most likely) nvidia.. Also isn't ubuntu's default runlevel 2? 
If it does boot up with the alternative driver then you may either want to manually install the nvidia drivers and remove the packaged ones,, or check out the /var/log/Xorg.0.log in the recovery mode.

---

### Post by snakedr on 2007-05-25
Check out the /etc/fstab file. The last number on each line determines whether fsck is run or not. I do not check other file systems that are mounted at boot time other than the root partition. I do not check any mounted vfat or ntfs partitions. 

Run "man fstab" on a console to see the different settings for fstab. Check out the section for the sixth field for further information.

You will have to edit this file as root to change the settings.

---

### Post by knallkopf on 2007-05-26
Hazaah! :-D

I changed my fstab according to snakedr's tip (disabled checking), which accelerated the process by factor 20. Then I checked my /etc/inittab to find out, it has been deleted one month ago (Don't ask me why or how). I put in a backup and changed default runlevel to 2. That still led to the same problem (X freezing, me having to make a cold reboot). But then I changed it to 3, and now it worked like a charm!

But AFAIK, the only difference between Runlevel 2 and 3 is that there is no NFS support in RL 2 (according to comment in inittab). Why does X Crash in RL 2 then, but not in 3? What has starting of X (or kdm) have to do with NFS?

Anyhow, thanks for the help, this is great!

---

### Post by mbradlcu on 2007-05-27
oops "S" means start "K" means kill,,, my bad ; (

---

