---
title: "Getting to Maintenance Mode"
date: 2007-09-19
forum: General Help
---

### Post by jlyn on 2007-09-19
During startup the files declared :
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.  (i.e., without -a or -p options)
Further information mentions that this can be done in maintenance mode with root filesystem in read-only.

1)  How do I get to maintenance mode.
2)  do I just  put    fsck  on the command line and press enter?  or is there anything else I have to do too?
3)  Then do I just reboot?
4)  If that doesn't work is the only solution to reload the software.
5)  Probable cause -  yesterday I loaded some new software through  Add/Remove . . .

Thanks,
JLyn

---

### Post by apetresc on 2007-09-19
When you boot from GRUB, for each kernel in the boot menu, there should also be a "(Recovery Mode)" line for it as well. Boot from that. Then, yes, just type "fsck" in the shell. (You may or may not have to include the actual device name after the command name, which is just /dev/sda)

---

### Post by jlyn on 2007-09-19
Hello Adrian P,
I am a relative beginner.
When I switch the machine on it boots automatically.
How do I access the GRUB or recovery mode line?
What do I key in and when?
I am disinclined to press ctrl C.
Esc, F8 and Del didn't do it for me.
Thanks,
Lyn

---

### Post by apetresc on 2007-09-19
Hm, that's strange, usually "Esc" accesses the grub boot menu if it's not set to appear by default.

Are you able to access your /boot/grub/menu.lst file in some way? If so, can you post its contents here?

---

### Post by jlyn on 2007-09-19
SORRY SORRY SORRY - I got ESC to work.
But when I put  fsck   in against GRUB>  I got ERROR 27 :  unrecognized command.

---

### Post by Lord Illidan on 2007-09-19
That's not what he meant. Does your grub screen have an option to display the menu? I think it is Escape. Press Escape, and from the menu, chose the Failsafe option.

---

### Post by apetresc on 2007-09-19
> **jlyn said:**
> SORRY SORRY SORRY - I got ESC to work.
But when I put  fsck   in against GRUB>  I got ERROR 27 :  unrecognized command.
Hm, it seems like you're actually getting the grub prompt here, not the boot menu. fsck won't work as a grub command, you actually have to boot into recovery mode.

It may be simpler to use a LiveCD to perform the fsck. Simply boot from a LiveCD (like the Ubuntu install CD), and type```
sudo fsck /dev/sda
```

---

### Post by jlyn on 2007-09-19
Thanks, I have to take my computer to another location and continue from there  (disc and book are there not here).
Sorry for the hiatus.  I will keep the thread open on my laptop.

---

### Post by jlyn on 2007-09-19
Please be patient - I am booting from the disc.  I can select and read help.  It doesn't tell me how to get out of the boot cycle and get to the boot: prompt.
How do I do that?
I am working with dapper drake 6.06 of June 2006
Thanks

---

### Post by jlyn on 2007-09-19
Using the terminal window, after booting from the CD, I put in 
 sudo fsck /dev/sda 
at the ~$  prompt  and got the following back

Couldn't find ext2 superblock, trying backup blocks ...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

---

### Post by jlyn on 2007-09-19
I was reading the bad-block page on the help menus from Terminal.  It sounds quite dire.
Does a bad block mean I should reload the whole system?
It is not a huge deal as this is a computer that I can learn on, not one that has loads of useful stuff loaded.
Thanks.

---

