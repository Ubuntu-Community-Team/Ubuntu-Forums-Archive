---
title: "XMMS without an interent connection"
date: 2005-07-06
forum: General Help
---

### Post by 6line on 2005-07-06
I've been using linux for less than a week, but I've got one major problem thats stopping me from leaving Windows behind entirely.

- The interent connection

I have a conexant modem and the only place I can download drivers for it (linuxant) charges.

I've been trying to install XMMS (and a couple of other programs) but all of them require the 'apt-get' command  which requires an internet connection right?
So this is all I get...
**Example:**
[I]root@ubuntu:/home/ozymandius # sudo apt-get install xmms
Reading Package Lists... Done
Building Dependency Tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
[/I]

Is there anyway to download these packages from another computer and transfer them onto my own laptop or do I **have** to be connected to the internet?

Changing my modem is not an option I'm afraid, but I can download a 14.4Kbps  driver for my modem for free. If I'm forced to use the 14.4Kbps driver, does anyone know how long it will take to download?

---

### Post by varunus on 2005-07-06
You can download the packages manually if you have to.  Go to [http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/) and you can download everything from there.  You can also look at dependencies and get the ones you need from there too.  However, this will be an annoyance; I would recommend using the 14.4 drivers if you can.

However, aren't linuxant's drivers free (as in beer)?  If you go to [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/) and click download at the left, you can download them by choosing I AGREE at the bottom...

---

### Post by 6line on 2005-07-06
Thanks a lot  :grin: 

No they charge for the full 56K version but they offer a free 14K version.
I feel a bit cheated but there's nothing I can really do

[QUOTE="Linux Ant"]Linuxant on the other hand doesn't sell any hardware, and depends on contributions from users and other licensing revenues to develop adequate Linux drivers for very widespread proprietary hardware. This cannot be effectively done by the open-source community because a significant portion of such drivers is technology protected by trade secrets, patents, or other restrictions, and it requires a NDA (Non-Disclosure Agreement) which most open-source developers are not willing or not able to sign without getting into a difficult position. 

Nonetheless we did initially try the purely free approach (in the beta stage) and unfortunately it didn't work in this case. Because legal restrictions prevent the software from being entirely open-source, free-software programmers couldn't get involved. Instead, our personal mailboxes got constantly flooded with requests for improvements from users and we ended up having to do the bulk of development ourselves, with professional staff working full-time (and deserving a minimum salary). 
[/QUOTE] 

 ](*,)

---

