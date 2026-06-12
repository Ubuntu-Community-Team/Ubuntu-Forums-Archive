---
title: "Boot Help?"
date: 2013-04-14
forum: General Help
---

### Post by unawokendreamer on 2013-04-14
Hello

So my laptop has a busted screen and when I'm booting certain screens are a type of information that my second screen can't read.  This hasn't been a problem as i turn on the computer it just runs naturally till it is information that my screen can read.

Here's the problem...

My laptop has over heated and booting up in some sort of recovery mod (I think).  Through the cracked screen i can see that there are 4 choices and i believe the last two are memory tests. The fist one goes to a blank screen with a cursor at the top. So I chose the second one, this leads to a new menu with 16 choices. Can someone tell me what ones to choose? I can't see my choices otherwise I'd know.

Oh, and my harddrive is not partitioned, thus the four options at the beginning.

Thanks

---

### Post by grahammechanical on 2013-04-14
It would help if you told us what version of Ubuntu you are using? If you are using 12.04 then the second option should be recovery mode but if you are using 12.10 then the second option might be a sub-menu with recovery mode and all the old kernels listed.

Recovery mode will bring to a text mode screen with these options

> resume --------------------------resume normal boot
clean --------------------------------------------try to make free space
dpkg ---------------------------------------------repair broken packages
failsafx -----------------------------------------run in failsafe graphic mode
fsck ----------------------------------------------check all file systems
grub ---------------------------------------------update grub boot menu
network --------------------------------------enable networking
root --------------------------------------------drop to a root shell prompt
system-summary  ----------------------- system summary

The root option brings you to a command line but the file system will be in read only mode. It will not let you update the OS. You need the file system to be in read/write mode. Here is the method I use:

1) select failsafex mode and at the next screen back out of failsafex mode to the recovery mode menu. The file system is now in read/write mode.
2) select root to get to a root shell prompt.

I am guessing that the overheating has corrupted the ability of the X-server to set a video mode. I had a similar situation when a fanless graphic card overheated. The X-server gets its video mode settings directly from the monitor and not from a configuration file. I think that you are being put into Fail Safe mode.

Regards.

---

### Post by unawokendreamer on 2013-04-14
Pretty sure I'm on 12.10.

---

### Post by unawokendreamer on 2013-04-14
I'm on 12.10, but I'm unsure how to do what you are asking. I literal have no view of the choices and the second menu is 16 choices long.

---

### Post by unawokendreamer on 2013-04-14
So I found out that the first menu says:

Ubuntu
Advanced options for ubuntu
Memory test
Memory test

Then i googled "advanced options for ubuntu" and got the next menu, which is:

Ubuntu with Linux [something-something] generic
Ubuntu with Linux [something-something] generic (recovery mode)

It says those two lines eight more times, making a total of 16 lines. I got really excited at this point, however if I choose generic, I get a blank screen with a cursor at the top. And if I choose recovery mode, I get and wall of text and all I can catch at the bottom is:

[       0.599073] Freeing initrd memory: 14792k freed

Any help would be great.

---

