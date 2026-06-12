---
title: "A lot of issues with my computer. Would anyone like to help?"
date: 2008-04-05
forum: General Help
---

### Post by arelis on 2008-04-05
Hello, everybody from the Ubuntu forums. I've been having weird troubles with my computer lately. It's different each time, although some of the problems repeat. The most of them i have fixed by simply restarting (rebooting) my computer. However the slowness comes back very quickly. I will list the issues here:

Compiz is **_NOT_** on. **_Compiz is [B][U]NOT_** on[/U][/B]

[LIST]
[*] After some general working on the PC, or some gaming, or doing ANYTHING in ubuntu, after about 7 hours programs refuse to start, and when you start graphical apps in the terminal, it gives "Segmentation fault". The same thing happened in Debian.
[*] Crashes may also happen when i run heavy games
[*] The PC in general is slow, and that with only pidgin, a terminal, the file browser, and firefox open (with 8 tabs). With "In general", i mean symptoms like: When i want to drag the scrollbar, i press it and drag it, sometimes that is delayed. The highlight is also delayed. A lot of stuff on the screen is delayed.
[*] YouTube video's sometimes hang, then after about 2 seconds continue. The sound hangs as well.
[*] While running Compiz, the PC frequently crashes, forcing me to reboot. (I see that this line causes a lot of confusion. Compiz is **_NOT_** on. This is only **_WHILE_** compiz is on)
[/LIST]

However, in the past i had some other problems as well, including:
[LIST]
[*] A segmentation faulting apt-get (reboot fixed it)
[*] The inability to start programs because the libraries were wrongly linked
[/LIST]

Most of these crashes even leave the magic sysrq-trick to dust. So i can't use that, or ctrl+alt+backspace, or ctrl+alt+delete, or ctrl+alt+f1. If it was an ordinary xorg crash, that would've worked. However, this does not apply to ALL the crashes.

My computer has an ATI Radeon 9600 for a video card, an AMD Sempron 2800+ for a processor, and 768MB RAM (memory)
I am using the open-source Radeon drivers (the default ones. The non-restricted ones)

I have already done a memtest86+ for 2 hours, and another day 5 hours extra. That counts for 7 hours. Seems good enough to me. So it's not the memory.
I've been suspecting the harddisk, because there's a version of Windows on the OTHER harddisk that DOES work, without any problems. It was on this PC as it was bought.

Then again, it may very well not be the hardware's fault. Could be software, drivers, or my own fault.

I have already done reinstalls plenty of times, and usually the problems come back. Or another problem comes along.

---

### Post by dstew on 2008-04-05
> When i want to drag the scrollbar, i press it and drag it, sometimes that is delayed.A lot of your problems sound like display issues. The restricted driver may work better, have you tried it?

---

### Post by arelis on 2008-04-05
> **dstew said:**
> A lot of your problems sound like display issues. The restricted driver may work better, have you tried it?
Yes. I didn't have Compiz while using that, though, and i had some other problems. Like the pc crashing when i wanted to switch users. But games like Nexuiz ran pretty well using it.

---

### Post by arelis on 2008-04-05
I hope bumping my own thread is no breaking of rules. Right now my pc isn't slow for some reason, with about the same amount of programs open. But i think it would happen again. Can anybody please help me further?

---

### Post by dstew on 2008-04-05
Probably the thing to do is look at some of your logs following a crash to see if you get any clues as to what is happening. The logs are stored in the /var/log directory. You should check the syslog.0 file after a crash. Other logs to look at are the Xorg.0.log and the Xorg.0.log.old. There is a graphical System Log window in System --> Administration, but I am not sure how to use it to look at older logs.

---

### Post by prshah on 2008-04-05
> **arelis said:**
> I hope bumping my own thread is no breaking of rules. Right now my pc isn't slow for some reason, with about the same amount of programs open. But i think it would happen again. Can anybody please help me further?

Most likely your swap is corrupted; you can refresh it by ```
sudo swapoff -a
sudo mkswap /dev/xxx9
sudo swapon -a

```
 where xxx9 is your swap partition; such as sda5, sda6 or whatever.

Make sure you close all programs BEFORE swapoff.

You can also clear the files in the /tmp directory.

---

### Post by arelis on 2008-04-07
I'm sorry, but that didn't fix it. I had firefox and GNOME open. After a reboot, it didn't get fixed. Sometimes, my computer is still slow. Although i haven't had the segmentation faulting issue for a whole day now.

---

### Post by arelis on 2008-04-11
I hope, again, that bumping my own thread isn't against the rules (should read those someday. Right now i think it's "You should only bump your own thread if you have additional information related to the topic"), but I installed the Restricted drivers for my ATI Radeon 9600, and up to now i'm not noticing any slowness anymore. But things could change in time, so we'll see. Also, when my computer boots up, right before GRUB shows up, i see a cursor blinking, and that continues for about a minute (didn't count using a stopwatch..). Is that signs of a broken harddrive? Because, if it is, then it is my final confirmation that almost all of my problems are related to the harddrive that is in this computer, that was in my previous computer as well which showed a lot of the same problems.

Now that i'm at it, here's my harddrive layout:

/dev/hda: Harddrive with Windows on it. Partition table:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14945   120045681    7  HPFS/NTFS

/dev/hdb: Harddrive with Ubuntu on it. Partition table:
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1216     9767488+  83  Linux # Where Ubuntu itself is installed
/dev/hdb2            1217        1403     1502077+  82  Linux swap / Solaris
/dev/hdb3            1404        7781    51231285   83  Linux # This is the home directory

Would using Ubuntu on a second harddrive have to do with it?

---

### Post by njparton on 2008-04-11
Try removing compiz (not just turning it off) and then using metacity as your gnome window manager.

---

### Post by arelis on 2008-04-11
> **njparton said:**
> Try removing compiz (not just turning it off) and then using metacity as your gnome window manager.
Alright, i did that just now. I don't notice any difference at the moment.

---

### Post by arelis on 2008-04-11
> **arelis said:**
> Alright, i did that just now. I don't notice any difference at the moment.
I would like to notify you guys that "it" has happened again. Every graphical application that I start gives me a segmentation fault. example:
export DISPLAY=:0.0
robinl@robins-computer:~$ gnome-terminal
Segmentation fault (core dumped)

I'll go reboot now. This just happened, after i installed the open-source version of virtualbox to test out another OS. This happens many times, by the way. Sometimes, after using my computer for a while (or leaving it on a day), this would happen, and the computer would refuse to start any graphical application. I am typing this from the "links2" browser on the command-line, right now.

---

### Post by ryanhaigh on 2008-04-11
I don't have time to read all replies but I would suggest running memtest from the livecd to test for defects in your ram. The fact that the problems occur after some usage or when using 'heavy' apps (virtualbox for example) leads me to think that some of your ram may be bad.

---

### Post by njparton on 2008-04-11
> **arelis said:**
> Alright, i did that just now. I don't notice any difference at the moment.
 
Then at the very least you can rule out compiz specific issues and you've removed something gimmicky and a bit buggy from your system.
 
How did you set metacity to be your default window manager?

---

### Post by roots on 2008-04-11
regarding the point that problems occur after some time i would 

1. check your system's components for overheating: cpu, gfx, mem, chipset, hdd 
2. run a long (24 hrs) memtest from live cd again
3. remove/exchange some memory sticks
4. thoroughly check hard drives for errors
5. stress test your cpu for errors

assuming that you *haven't* been playing with cpu/gfx clockings, hard drive parameters or memory clockings/timings.

good luck!


cheers,
.roots

---

### Post by arelis on 2008-04-11
> **njparton said:**
> Then at the very least you can rule out compiz specific issues and you've removed something gimmicky and a bit buggy from your system.
 
How did you set metacity to be your default window manager?
Metacity was my default window manager all along and I recognise the window decoration I get when it runs metacity. But to verify, here's ps aux | grep metacity:
robinl@robins-computer:~$ ps aux | grep metacity
robinl    6966  0.4  1.2  16480  9532 ?        S    16:08   0:24 /usr/bin/metacity --sm-client-id=default0
robinl    7734  0.0  0.0   2992   764 pts/0    R+   17:48   0:00 grep metacity

And here is ps aux | grep compiz:
robinl@robins-computer:~$ ps aux | grep compiz
robinl    7738  0.0  0.0   2992   764 pts/0    R+   17:48   0:00 grep compiz
robinl@robins-computer:~$ 
Let's also check for Beryl:
robinl@robins-computer:~$ ps aux | grep beryl
robinl    7740  0.0  0.0   2992   764 pts/0    R+   17:48   0:00 grep beryl
robinl@robins-computer:~$ 

So, yes, compiz is off. And if i want to remove compiz, i get this:
robinl@robins-computer:~$ sudo apt-get remove compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

I am running GNOME, and since metacity is gnome's default window manager, i see no reason to not have it running.

@roots: I would check those hardware parts in about a week. But until i may reach the insides of the computer, and have RAM i can replace it with, AND a new harddrive to replace the old one... i won't.
The tests i have already run are:
1. Installing tons of other distributions (Arch Linux, SuSe Linux, Debian, Fedora)
2. Memtest86 for 2 hours
3. SMART test on the harddrive
4. more advanced test on the harddrive
5. SpinRite (!!) on the harddrive
6. Write zeros (From the manufacturer tool (Western Digital)) on the harddrive (this erases the harddrive COMPLETELY)
7. Dust removal in the computer (by blowing away the dust)
8. Memtest86 for 5 hours (while away at someone elses' house). Seriously, I think 7 hours is more than enough. I don't think the segmentation faults are related to the memory.
9. Reinstall of Ubuntu (yet again)
10. Re-creating the SWAP file
11. Switching back to Ubuntu again (by reinstalling)
12. Switching to the open-source 'radeon' driver
13. Switching back to the Restricted ATI drivers (i do notice the PC is FASTER while using that.)

How do i do those other tests?
1. check your system's components for overheating: cpu, gfx, mem, chipset, hdd
5. stress test your cpu for errors

One thing i also have noticed is that when using the K7-kernel on Debian, it went faster too. (Reminder: The processor is an AMD Sempron 2800+)

---

### Post by arelis on 2008-04-11
My topic is getting behind again. Does anyone have a reply?

---

### Post by dstew on 2008-04-11
> I don't think the segmentation faults are related to the memory.Do you ever get a segmentation fault when the computer is cold? Could some buildup of static electricity or heat over time be affecting the processor or memory or hard drive?

---

### Post by arelis on 2008-04-17
> **dstew said:**
> Do you ever get a segmentation fault when the computer is cold? Could some buildup of static electricity or heat over time be affecting the processor or memory or hard drive?
That could very well be the cause. I've not paid attention to the temperature of the computer when it happened. When it happens again, i'll check.

---

