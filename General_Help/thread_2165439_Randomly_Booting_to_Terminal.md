---
title: "Randomly Booting to Terminal"
date: 2013-08-04
forum: General Help
---

### Post by Petro Dawg on 2013-08-04
I thought I would give Ubuntu 12.04.2 a try, and did a fresh install today.  Everything seemed to work great until I rebooted a couple times.  Sometimes, apparently randomly, X fails to start and I am faced with a login prompt to terminal.  From there I can login, type "startx", and use the GUI as normal.  But it's kind of annoying to have to do that, so... 

How do I go about tracking down what might be causing this?

---

### Post by zero2xiii on 2013-08-05
Hay,

Not sure in your case what might cause it, however look here for how to accomplish what you are experiencing and try doing the reverse:
[http://askubuntu.com/questions/63085/directly-boot-to-terminal-bypassing-x](http://askubuntu.com/questions/63085/directly-boot-to-terminal-bypassing-x)

Cheers

---

### Post by Petro Dawg on 2013-08-05
I'm not sure what exactly caused it, but I think I got it to stop by doing some maintenance on the computer.  I noticed that I could not get the error to reproduce when I turned "fast boot" off in the BIOS (maybe just luck, I dunno).  So I figured perhaps it was taking too long for my system to ready all the drives (it seems I read an old obscure reference to slow drive detection causing boot issues in Ubuntu).  

Since "Slow Boot" was a little too slow for my taste, I removed one of the hard drives (3 might have been too many), positioned the Linux drive to sda1, replaced the ribbon cable, reinstalled GRUB, and turned "Fast Boot" back on.   So far I have had no more issues with X not loading.  I also noticed my Windows HD had the jumper set to master when it was supposed to be cable select (now fixed).  I'm not sure if any of those things actually helped, but so far so good. 

If the problem doesn't reoccur within the next few days I will marked this thread solved.

---

### Post by papibe on 2013-08-05
Hi  Petro Dawg.

Next time it happens, log into text mode and save the X log:
```
cp /var/log/Xorg.0.log ~/lastX.log
```
Then, when you get to the desktop, take that file:
```
~/lastX.log
```
paste it here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and post back link here so we can take a look.

Regards.

---

### Post by Petro Dawg on 2013-08-05
> **papibe said:**
> Hi  Petro Dawg.

Next time it happens, log into text mode and save the X log:
```
cp /var/log/Xorg.0.log ~/lastX.log
```
Then, when you get to the desktop, take that file:
```
~/lastX.log
```
paste it here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and post back link here so we can take a look.

Regards.

Thanks, I printed out your post so I have the command available if it happens again.

Hopefully it will not happen again, but if it does, I will certainly post the log.

---

### Post by Petro Dawg on 2013-09-01
Had no issues for nearly 3 weeks, then I decided to add a CD burner to my PC and when I started up the computer it went straight to terminal on my first boot.  Then I removed both my DVD and CD burner and replaced with a single DVD/CD Burner and again went straight to terminal on the first boot.  Both times I made changes in BIOS to either add or delete a slave drive.

Here is the requested [COLOR=#000000]Xorg.0.log[/COLOR] file from the last occurrence...   [http://paste.ubuntu.com/6053079/](http://paste.ubuntu.com/6053079/)

The problem is beginning to appear related to making system hardware changes.  It first occurred after I added a third hard-drive (which has since been removed).

---

### Post by Bashing-om on 2013-09-01
Petro Dawg; Hey !

Don't know ... but I had a somewhat similar issue when I did a fresh install and moved my drives around. Like to have driven me insane chasing down what was not happening. This approach for my hard drives fixed it for me:
The device.map file is located in /boot/grub/ It isn't required but can be used in Grub 2.
```

sudo grub-mkdevicemap

```
reboot and verify the file exist and drives are listed as expected:
```

cat device.map

```

[INDENT][INDENT]hey it is a thought
[/INDENT][/INDENT]

---

