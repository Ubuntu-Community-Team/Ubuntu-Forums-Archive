---
title: "HELP: total system crash...don't know why...KERNEL PANIC"
date: 2007-04-23
forum: General Help
---

### Post by residualbit on 2007-04-23
ok first let me start by saying, i have installed nothing new, nor have i updated anything recently...anyway, i turned on my laptop today and after the grub loading screen i got something these messages...

Starting Up...
[11.685480] .. MP-BIOS bug: 8254 timer not connected to IO-APIC
[1.583197] Kernel Panic - not syncing No init found. Try passing init= option to kernel.
[1.583232]


then it freezes, there is still a blinking cursor, but 0 input in accepted. this has been happening since about 7am today. i've never had any problems before. all i can do is continue to restart. sometimes there are more/different warnings or messages but these two are always there, and the kernel panic thing is always the last one....HELP ME PLEASE!

---

### Post by residualbit on 2007-04-23
even though i didnt want to, i reinstalled feisty from a cd (which i checked for errors, its fine) it took about 5 tries even for this because it kept freezing at the splash screen...anyway, worked fine, then i restarted my computer and... SAME PROBLEM! 

i dont know what to do, please help in anyway you can

the laptop is a toshiba A-75, about two years old, pentium 4HT, 1.5gb RAM, 80 gig hardrive.

---

### Post by lakersforce on 2007-04-23
I am sorry, but I dont know how to solve your problem. You should report the bug here: [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
Keep checking this thread, someone might be able to help you out eventually.

---

### Post by residualbit on 2007-04-23
now it says 


Kernel Panic: not syncing: can't allocate buffers

---

### Post by lakersforce on 2007-04-23
I hate that line, Kernel Panic. Really makes you feel uncomfy.

Ok, so my Kernel has panicked...would should I tell it? "Stop, calm down and breathe. You will be allright. No one is going to die!."

---

### Post by residualbit on 2007-04-23
yeah, tell me about, whoever designed linux used terrible syntax on that one...i mean serrioulsy what hope do you have when the info the system runs on "panics"

anyway, i figure i have one option now that i get a kernel panic message no matter what i try to start, boot, or run...

i could install windows via the recovery cd that came with my laptop

then try to install ubuntu over it...


this sucks so bad does anyone know how to solve or even help this problem

---

### Post by residualbit on 2007-04-23
anyone who thinks they might know, i will be more than happy to write down every error message, i just listed the two main ones

---

### Post by lakersforce on 2007-04-24
Perhaps you would be better of with Ubuntu 6.10? I had problems with the 7.04 install cd too (different from your problems though). So I did a upgrade of 6.10 to 7.04 instead and that solved my problems.

---

### Post by Immolatus on 2007-04-24
Did you install vai disk of update manager? If disk then will it run the live cd?
I saw a lot of people having problems with the update manager.
I personally downloaded the live cd/install version and am having kernel panic myself.
It happens at completely random times though never on start up.
I'm thinking it has something to do with xorg so i'm doing without the desktop affects today to see what it does. I figure if I strip down I'll be able to Identify the culprit.
By the way, I've gotten no messages before panic the screen just hangs and caps lock and numlock just blink. No response even to the power button, I have to unplug it and reboot.
This happens about once per day.
I'm running on a laptop as well.

---

### Post by se2131 on 2007-04-24
For reference, I have a Toshiba A75 series, ATI Radeon 9100 card.  I was also experiencing the MP-BIOS error, which was causing Fiesty to freeze every 20 minutes or so.  I found that if I include a "noapic" parameter in the kernel boot options, then it works fine.  I wasn't getting the Kernel Panic error, but perhaps this will work for you (it's worth a shot anyway)

I'm not sure how to do this the 'proper' way (editing the #defoptions line in /boot/grub/menu.lst is what I've been seeing, but the option never shows up the way it should when I do this), but here's what worked for me:

First do:

```

sudo nano /boot/grub/menu.lst

```
and scroll down until you see the line: ## ## End Default Options ## ##

After this, you will see lines that begin w/ title, root, kernel, initrd, and maybe quiet or savedefault.

What you need to do is find the kernel that you are using and edit the "kernel" line.

This is what my edits look like:

```

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c8d81b8b-4a0a-4acb-b18f-6aa156583253 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

Make sure that you edit the kernel that you are planning to use. If anyone knows how to make this option stick for all kernels, please provide your insight.

---

### Post by residualbit on 2007-04-25
i was able to reinstall via the live cd once (after it froze many times) it worked fine, then on restart i started having the same problems...so, i tried using my windows system recovery cd which installed fine but the on reboot, grub still tries to start, and it says grub error 17, i cant do anything! is there anyway i can completely wipe my harddrive of everything and start over?

---

### Post by phidia on 2007-04-25
If you are still getting grub after installing windows something is messed up with the MBR (master boot record)
You can try to fix that from dos-using the recovery cd   [http://leb.net/blinux/list-archive/blinux-list/2001/msg00039.html](http://leb.net/blinux/list-archive/blinux-list/2001/msg00039.html)

---

### Post by residualbit on 2007-04-25
i'll try that, but i cant get ubuntu to load so i cant get into the console...

---

### Post by residualbit on 2007-04-25
i used this thing called "ultimate boot disk" and deleted all my partitions, to technically, nothing should be on my hard drive, but now it tries to start grub again and i get error 22

---

### Post by residualbit on 2007-04-25
also, someone a few posts up said something about their numlock key blinking...my caps locks key is blinking when it crashes...

---

### Post by ashz on 2007-04-25
ur getting the error 22 cause u deleted the partitions....

try this ..

boot into the recovery console using your windows disk.... and in the prompt type "fdisk /mbr" without the quotes

now u can start again

cheers
ash

---

### Post by residualbit on 2007-05-07
just wanted to update everyone that helped...it turns out the problem was a bad RAM chip. I had upgraded it about two years ago, not sure what happened to it or how it went bad, but i popped the old one back in and everything worked fine. Althogh 1.2 gigs down to 512mb sucks...so long gaming

---

### Post by Grundalizer on 2007-06-05
I have the same problem but I cannot get the noapic to stay on the end of the menu.lst even if i save it.  For some reason it is not staying after i close out the window after saving.

---

