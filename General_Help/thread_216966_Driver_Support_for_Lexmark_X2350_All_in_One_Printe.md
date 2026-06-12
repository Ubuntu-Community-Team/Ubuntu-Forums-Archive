---
title: "Driver Support for Lexmark X2350 All in One Printer"
date: 2006-07-16
forum: General Help
---

### Post by Joedude on 2006-07-16
Maybe it's the wrong place to put this but...

Been looking for a driver for the Lexmark X2350 All in One Printer

I guess the title said it all. If this is in the wrong place, I'm sure a mod or admin will move it to the appropriate one...forgive my indiscretion please.

Anyway, everywhere I looked on the internet says there isn't any support for it...which will make me very sad :-(

Any help I can get in this arena would be greatly appreciated. I would even be able to return the favor in any way I can with in reason ;-)

Joedude, aka the lost one

---

### Post by nealklomp on 2006-07-16
I have a similar printer, the dell 922 AiO, which is basically a rebranded Lexmark X5250. I have been looking for a way to run it with Ubuntu for 6 months. I am forced to keep XP on my desktop to run the printer.

---

### Post by Joedude on 2006-07-16
That's not very encouraging....

Back to my HP Deskjet 697c....(circa 1998 )

I'd rather not switch between OS's just to print...besides, it's upstairs on my server(the HP deskjet 697c), and I can't be bothered to go upstairs everytime I print..

---

### Post by Old Pink on 2006-09-25
BUMP. 

Months on, anyone got any ideas yet? :(

---

### Post by pod25 on 2006-09-25
> **Joedude said:**
> That's not very encouraging....

Back to my HP Deskjet 697c....(circa 1998 )

I'd rather not switch between OS's just to print...besides, it's upstairs on my server(the HP deskjet 697c), and I can't be bothered to go upstairs everytime I print..

I made a post last week about my perfect work around for using Lexmark on linux.
My solution was to install vmware, then install xp into vmware, then installed my printer onto xp.
It all sounds a bit much just to run a Lexmark printer, but it was pretty painless and works a treat, my printer not only works now, but is networked on my local network.

---

### Post by zelluloidtraum on 2006-12-05
Can you tell me how to do this or show me where to go to find out how to do it....sorry....I'm n00btacular.

---

### Post by Tobster on 2006-12-05
I got the same problem.  with Linux it best to buy an **HP branded printer** because HP actively support Linux and so should be just plug and play because the drivers should be already install in a Linux distro.  I would go far as 'will be,' 'but I say should be' just to be safe.

You have to remember that the three main business that support the Linux Kernal are:

IBM
HP
Red Hat

so it best to get hardware from them **BUT** saying that Red Hat is losing the market to Ubuntu and SUSE big time so it prob best to stick with what IBM and HP say because I would think that Red Hat would actively start to limit there work with Fedora Core and Red Hat Enterprise (there own distros

Thanks

Toby

---

### Post by Sef on 2006-12-05
[LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-x2350") says it is a paperweight.  Therefore I would follow pod25's suggestion in post #5.

---

### Post by dirken on 2007-01-06
It seems that lexmark is offering some kind of support for linux printing.

On the following link you can download a driver for the scanner function of the All In One printers but does anybody know how to do so?
[http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668517_0_en,00.html](http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668517_0_en,00.html)

Greetz..
Dirken

---

### Post by zeifertstc on 2007-02-09
That driver is only actively supported by Linux Distros running an RPM system. It also does NOT include support for the printer in question by first post. I've been trying to find a work-around but have been largely unsuccessful. How 'bout that VMware solution? I've heard about VMware but haven't had any luck finding out how to get it.

---

### Post by DanielH on 2007-02-12
I'm also an unlucky owner of a Dell AIO 922 printer/scanner. I used to go the vmware route, as pod25 described in post #5.

It was quite cumbersome, but at least it worked - until I upgraded to Ubuntu 6.10 Edgy. For some stupid reason, Ubuntu grabs the device before VMWare can do so, although it does not support the hardware :(

I tried to configure udev to ignore the device, but I could not get it working again.

---

### Post by Tanker Bob on 2007-02-12
FWIW, Brother and Epson also actively support Linux.  I just bought a new Brother laser printer yesterday to replace my old HP laser.  While evaluating printers, I explicitly checked for active Linux support.  I also have an Epson CX7800 inkjet all-in-one for which Epson provides Linux drivers, but not on their primary US website.  

There are some good HOWTOs on this site that explain how to get scanners recognized in ubuntu.  It's not all that straight forward.

---

### Post by Guitar John on 2007-02-12
I haven't tried it yet, but [this How To]("http://www.ubuntuforums.org/showthread.php?t=49714") claims that many Lexmark Printers including my Dell AIO920 (reportedly a rebranded Lexmark) can be made to work.

YMMV,
-John

---

