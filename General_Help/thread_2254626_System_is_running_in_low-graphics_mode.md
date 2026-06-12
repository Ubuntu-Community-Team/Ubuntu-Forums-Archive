---
title: "System is running in low-graphics mode"
date: 2014-11-28
forum: General Help
---

### Post by michael-piziak on 2014-11-28
I installed Ubuntu 12.x lts on my sisters computer.
After allowing all updates except an operating system upgrade, the up to date screen tells me that new hardware support is available.  
So I click to allow the new hardware support.   Then all of a sudden I get lots of screens telling me that hardware is running low on graphics
or something and I never can recover.

So I'm now reinstalling the 12.x disk again.
What just happened and can I turn this hardware upgrade option off so that my sister doesn't select it later ???

p.s. Perhaps I should let this system upagrade to 14.4 lts and see what happens - her system is an older Intel Core 2 Quad (HP brand).

?

---

### Post by deadflowr on 2014-11-28
What is the complete name on the disk, please.
Which 12.04 version does it list
Versions marked as 12.04, 12.04.1 and 12.04.5 should not ask to install newer hardware support.
But versions for 12.04.2 ,12.04.3, and 12.04.4 would, because those three include hardware stacks that are no longer supported.
So the system is being told to update to a supported version.

My humble suggestion would be to download version 12.04, or 12.04.1 from here
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)
scroll down the page to find the version for the desktop for 12.04, or 12.04.1, preferably 12.04.1 because it has some of the initial bug fixes.
The file name should look like 12.04-desktop-i386.iso, or amd64(for 64-bit).iso.
Either of these, though, will give precise's original hardware stack(which is still supported) 

It is quite possible that the newer hardware stack used in 12.04.5 is not up-to-snuff for your/her machine.
Which is why they still have 12.04(.1) available.

---

### Post by michael-piziak on 2014-11-28
The disk is ubuntu 12.04 (64 bit desktop edition)  Precise Pangolin  LTS  - not much else on the disk but that.

I reinstalled it, now I'm allowing the system to upgrade to 14.04  -   do you think that may solve the problem (and get rid of those hardware stacks)?

The upgrade is taking some time (hours).  I just hope it doesn't offer a hardware update too - :(


p.s. I have never burnt an install disk or downloaded and used an install from a usb thumb drive.  If it comes to this, where are the best instructions for me.

---

### Post by mörgæs on 2014-11-28
Let's see in detail which gear we are talking about. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by michael-piziak on 2014-11-28
Well, I upgraded to 14.04 (via online).
Seems to be running ok, other than it warns of a firmware needing updated.

Do you still want me to run this code to see which gear we are talking about, or does 14.04 make it a moot point

---

### Post by mörgæs on 2014-11-28
If everything works you can just mark the thread 'solved'. Should some problems appear one day you know where and what to post.

---

