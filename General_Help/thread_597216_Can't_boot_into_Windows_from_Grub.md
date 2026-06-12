---
title: "Can't boot into Windows from Grub"
date: 2007-10-30
forum: General Help
---

### Post by benlacy2112 on 2007-10-30
So I've seen that some other people have had a similar problem, but I can't seem to get any of the solutions to work. I used Wubi to try out Ubuntu for a couple months and decided I wanted to install Ubuntu onto my hard disk.  I had an existing Windows XP installation on a single 250GB hard drive.  I defragged multiple times until I had all data on the hard drive down to the front of the disk (in about the first 1/4 of the disk).  

Then, I put my Ubuntu Gutsy disk in and booted from it.  I used the utilities on the disk to resize my Windows partition down to 150GB.  I then created the three partitions for Linux...root, shared fat32, and swap (twice the size of my RAM).  Next, I installed Ubuntu. I let it do everything automatically, and at some point it installed Grub.  When I rebooted after the install, I got to the Grub menu.  I had several Linux options, and then Windows XP under "Other operating systems".  Clicking on XP takes me to a screen that says "Starting up..." and it hangs there.  I've tried several times and let it hang there for five minutes or so, before rebooting into Linux.  

I edited my grub menu.lst file and added the makeactive line to the code that was already there for Windows.  After saving this, I still get hung up on the "Starting up..." screen.  At this point I'm at a loss, and I figured I should ask around for some more advanced advice before I go blowing up my computer even more.  

Having said all that, Gutsy works perfectly, and I couldn't be happier with it.  Any help with the Windows issue would be greatly appreciated, and I thank you in advance!

Cheers,
Ben Lacy

---

### Post by dayvy on 2007-10-30
I suspect it's not an issue with grub but with windows. It looks like grub is doing its job if you're getting to the "Starting up..." part. Running checkdsk on windows may solve your problem. Of course, getting into windows to run it is the problem. Two options: 1. Boot with your windows cd and go to a recovery console and run checkdsk from there. 2. Boot with UBCD for windows and attempt a repair from it.

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

Good luck.

d.

---

### Post by benlacy2112 on 2007-10-30
Thanks for the advice dayvy!  I'll try that when I get home.

Cheers,
Ben

---

### Post by benlacy2112 on 2007-10-30
I just got home and ran chkdsk on my c:\ drive (windows).  it said it found 1 or more errors.  what should I do from here?

Thanks!

---

### Post by FXEF on 2007-10-30
> **benlacy2112 said:**
> I just got home and ran chkdsk on my c:\ drive (windows).  it said it found 1 or more errors.  what should I do from here?

Thanks!

 Use the /r switch with chkdsk. This locates bad sectors and recovers readable information.

---

### Post by benlacy2112 on 2007-10-30
Thanks FXEF!  I'm on it...I"ll post again with some results, hopefully good ones :)

Cheers,
Ben

---

### Post by benlacy2112 on 2007-10-30
Hmm..I'm watching the chkdsk /r run on my computer, and it got to 50% really quickly.  Then it crawled to 70%, then went straight back to 50%.  Weird.  Is this an indication of anything?  Should I just let it keep going and see if it jumps back to 50%?

Thanks!

---

### Post by dayvy on 2007-10-31
I'd let it go for a while and see if it finishes. If not, abort it and try again. If that fails then you may have to try another tool to repair it. I'd download ubcd4win and try some of the tools that come with it. It won't cost you anything but a bit of time.

d.

---

### Post by benlacy2112 on 2007-10-31
Thanks dayvy.  The chkdsk /r just completed a while ago.  It didn't say anything about any errors, but when I try to boot to windows from grub, I get the same "Starting up..." screen where it just hangs.  I'll try the ubcd4win when I get home and see if that works. 

Thanks!
Ben

---

### Post by dayvy on 2007-10-31
Have you tried booting into safe mode?
d.

---

### Post by benlacy2112 on 2007-10-31
You know what, I haven't even tried that.  I can't believe I didn't think of that one already!  I'll try that before I use the restore CD when I get home.

Thanks!
Ben

---

### Post by benlacy2112 on 2007-11-01
Couldn't get the Ultimate Boot CD to work either.  I appreciate everyone's help that posted, but I think I'm just going to re-install.  A clean install of an OS is always a nice thing :)

Cheers,
Ben

---

