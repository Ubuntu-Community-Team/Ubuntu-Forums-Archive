---
title: "HD Erasing Software"
date: 2007-07-07
forum: General Help
---

### Post by init1 on 2007-07-07
I saw HD erasing software at bestbuy. Is this really necessary? Can't I just do a
> dd if=/dev/zero of=/dev/thedevicehere
several times?

---

### Post by cmillican on 2007-07-07
Why not just use fdisk?

---

### Post by tgm4883 on 2007-07-07
> **cmillican said:**
> Why not just use fdisk?

I would assume that he is trying to make the data unrecoverable.

AFAIK, the software your talking about just writes 1's and 0's on the whole drive 7 times (I think 7 is the DOD requirement)  So doing what the OP posted seems like it would work.

---

### Post by cmillican on 2007-07-07
I downloaded KillDisk and used it on an old laptop I had...worked perfectly, but only wrote 0's over everything...had to pay to get the 7X random 1's and 0's...it wasn't much though, because you're only paying for the development and bandwidth to download instead of manufacturing, packaging, shipping, etc.

---

### Post by djchandler on 2007-07-07
Download DBAN from sourceforge. It is the best price, free. I've known of the programmer's work on other platforms going back about twenty years, and he is nothing if not meticulous. You have the ability to far surpass US Department of Defense specifications.

Wiping a hard drive is advisable before disposal or making a contribution of it.  Recovery of old data is possible unless it has been overwritten multiple times. FDisk will not overwrite the data, even if you reformat it. Writing zeros once across the whole disk will not completely wipe away the underlying magnetic impression of old data. Get the whole story at

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

D. J.

---

### Post by init1 on 2007-07-07
Well, if the proprietary software just writes 1's and 0's, then is there any reason not to use dd? If I used /dev/random, it would write random data to the drive, so that might work better. I was just curious. I wouldn't want someone I know to pay for software when I could do the same thing for free.

---

### Post by djchandler on 2007-07-08
> **init1 said:**
> Well, if the proprietary software just writes 1's and 0's, then is there any reason not to use dd? If I used /dev/random, it would write random data to the drive, so that might work better. I was just curious. I wouldn't want someone I know to pay for software when I could do the same thing for free.

Well, there is certainly no reason to pay for the software. I just like the convenience of DBAN as it all fits on a floppy, or you can make a bootable cd with it. That way you don't have to worry about what OS is on the computer booting device. DBAN loads a Linux kernel and then runs itself in text mode. There is nothing easier to use. its user interface just takes you back a couple of decades or so. You actually have to use the keyboard. If you already have a computer case open and it is easy to connect the drive you want to wipe, and the os you need to run the application you are suggessting is bootable, there isn't anything wrong with your approach either. Repeat it at least 7 times, the more the better. If the data being wiped is sensitive, I would advise using DBAN. I really like the random data algorithms Darik uses in DBAN.

---

### Post by init1 on 2007-07-08
Thanks, looks like I got some good advice. Almost all distros, even floppy distros, have dd so I guess I should be OK. I may get DBAN, just in case I need it later.

---

### Post by djchandler on 2007-07-08
You are welcome.

You'll find a use for DBAN someday. It's easy, compact, and works. Darik M. knows what he is doing.

DJ

---

### Post by KoolBeans on 2008-01-07
Is there a way to use the secure erase commands built into the hard drive regardless of the bios freeze lock?
All HD's built after 2002 include this built in feature. It allows a complete erase with unrecoverable data in about 1 hour, based on 100gb size drive.

[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

Update:
Three different ways can bypass a BIOS security freeze lock:
1.  Most preferred method:  If another computer is available, boot the drive 
from another computer.  Since the freeze lock is entirely BIOS dependent, another 
computer's BIOS may not freeze lock the drive.

2.  Second method:  Switch the drive to another drive channel or another position 
on the channel, e.g. Switch drive from secondary master S0 to secondary slave S1 
or vice versa.  Some BIOSs do not send the Freeze Lock command to all channel 
master/slave positions.

3.  Least preferred method:  **There exists some danger to your drive in using 
this method, use at your own risk**  Shut down the computer system.  Unplug the 
four-wire power cable of the hard drive while leaving the signal cable plugged in.  
To eliminate the danger of ESD, always ground yourself when removing the power 
cord.  Power on the system and boot into DOS with a DOS boot disk.  Once DOS has 
booted up and you are at a command line interface plug the power cord of the hard 
drive back in.  Run HDDerase.exe.  The logic in this method is to prevent the 
drives detection in BIOS, which is when the freeze lock command is issued. 

Apparently you have to muck with the hardware in some manner to subvert the bios freeze lock :(

---

