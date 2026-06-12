---
title: "I issue you a CHALLENGE"
date: 2007-12-25
forum: General Help
---

### Post by Ripfox on 2007-12-25
I have an old Gateway Solo:
[http://support.gateway.com/s/Mobile/Solo_Series/p2300_13/p23_13nv.shtml](http://support.gateway.com/s/Mobile/Solo_Series/p2300_13/p23_13nv.shtml)

with no cdrom...but I have one of these:
[http://www.pccables.com/cgi-bin/orders6.cgi?action=Showitem&partno=00508&rsite=f.00508](http://www.pccables.com/cgi-bin/orders6.cgi?action=Showitem&partno=00508&rsite=f.00508)

I have managed to get Puppy on it, by using this floppy called "wakepup" which searches for usb devices then it installed Puppy from the cdrom I hooked up with the adapter. 

Is there an equivalent floppy or method so I can install an Ubuntu server on here instead? It will not boot straight to the cdrom so far without a floppy to "wake" it up. I really want to get a server on here then install fluxbox or something!

Thanks all...

Rip

---

### Post by Ripfox on 2007-12-25
No takers? :(

---

### Post by ugm6hr on 2007-12-25
Do you have another laptop you could use to install on to the HD (and then transfer back)?

Does the laptop have ethernet - if so, can you boot from net?

Does it have USB - if so, can you boot from USB?

The following might help:
[http://ubuntuforums.org/showpost.php?p=3956118&postcount=6](http://ubuntuforums.org/showpost.php?p=3956118&postcount=6)
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)
[http://ubuntuforums.org/showthread.php?t=640086](http://ubuntuforums.org/showthread.php?t=640086)

---

### Post by Ripfox on 2007-12-25
No other laptops that have Ubuntu on them can be taken for parts.

No internet, except hoping to get my usb wireless device to work after server install.

It cannot boot from usb without the help of a "wake" floppy. Is there one for Ubuntu? If so, can I create it from a Ubuntu machine? I have NO windows machines here.

---

### Post by Ripfox on 2007-12-25
> Do you have another laptop you could use to install on to the HD (and then transfer back)?


This is a very old laptop, and the only other one is my GF's new dv5000...I don't think the hdd will be compatible in the first place, and I think she would protest anyway.:lolflag:

---

### Post by skymera on 2007-12-25
USB wireless?

Ubuntu has a tendency to hate usb adaptors.

---

### Post by Ripfox on 2007-12-25
Not in my experience...my Belkin off brand "My Essentials" wireless usb sticks work out of the box.

So, some more info...I pulled out the hdd and it just slides out of the side, as well as the floppy drive. Very accessable.

---

### Post by agurk on 2007-12-25
Very interesting problem, got me googling...
Check this out: [http://ubuntuforums.org/showpost.php?p=408606&postcount=5](http://ubuntuforums.org/showpost.php?p=408606&postcount=5)
(You might need to grab FreeDOS as well, if you don't have any Windows box around)

**Edit:** or this thread: [http://ubuntuforums.org/showthread.php?t=81280](http://ubuntuforums.org/showthread.php?t=81280)

---

### Post by Ripfox on 2007-12-25
Ok, so I plugged the usb wireless stick into puppy, and whammo it recognized it...but it looks like puppy can handle up to wpa, not wpa2 like my connection is. I would consider resetting the router to open just to do a "net install" if it would even be worth it...it may download the neccessary stuff too slow? What do you think? AND, will the net install wipe out puppy for me, because this hdd is only like 2 gigs or so...:)

---

### Post by Ripfox on 2007-12-25
> **agurk said:**
> Very interesting problem, got me googling...
Check this out: [http://ubuntuforums.org/showpost.php?p=408606&postcount=5](http://ubuntuforums.org/showpost.php?p=408606&postcount=5)
(You might need to grab FreeDOS as well, if you don't have any Windows box around)

**Edit:** or this thread: [http://ubuntuforums.org/showthread.php?t=81280](http://ubuntuforums.org/showthread.php?t=81280)

On the first one...would I run raw write or whatever with wine? would that actually write it to the floppy? Also, on the second one...looks more feasible, but same question...wine?

---

### Post by Islington on 2007-12-25
> **ripfox said:**
> Ok, so I plugged the usb wireless stick into puppy, and whammo it recognized it...but it looks like puppy can handle up to wpa, not wpa2 like my connection is. I would consider resetting the router to open just to do a "net install" if it would even be worth it...it may download the neccessary stuff too slow? What do you think? AND, will the net install wipe out puppy for me, because this hdd is only like 2 gigs or so...:)

I had a similar problem to yours, my old gateway. it took up to 14 hours.

I ended up taking out the hardrive, putting it in someone else's computer, installing, and putting it back. Is this an option for you?

---

### Post by Ripfox on 2007-12-25
So did it work? Does it format over puppy? I am only trying to install a command line system at first, so it should be easier...just thought of something. If it installs over puppy, won't it break the wireless connection?

---

### Post by maybeway36 on 2007-12-25
I think instead of WINE you can use DOS to run these, dd might work too.

---

### Post by Ripfox on 2007-12-25
> **Islington said:**
> I had a similar problem to yours, my old gateway. it took up to 14 hours.

I ended up taking out the hardrive, putting it in someone else's computer, installing, and putting it back. Is this an option for you?

See previous post about this issue.

---

### Post by Ripfox on 2007-12-25
> **maybeway36 said:**
> I think instead of WINE you can use DOS to run these, dd might work too.

Sorry, whats dd and how do I run dos from a linux machine?

---

### Post by Islington on 2007-12-25
> **ripfox said:**
> See previous post about this issue.

Ah. well in my case instead of puppy it was warty, I was trying to replace it with dapper. the update went fine, and upon reboot into dapper, my wireless card was no longer recognized.

---

### Post by Ripfox on 2007-12-25
I see. Well, does anyone know if the "net install" would be an option in this situation?

---

### Post by maybeway36 on 2007-12-25
Can you temporarily hook your computer up to an ethernet connection? If so, you could install Ubuntu from DOS with GRUB4DOS and the netboot files.

---

### Post by agurk on 2007-12-25
Hmm, Google tells me Wine doesn't like rawrite2.exe, so instead, I'd grab a boot floppy disk image file ([http://www.fdos.org/bootdisks](http://www.fdos.org/bootdisks)) and write the image to the floppy disk using the 'dd' command (see [http://www.murga-linux.com/puppy/viewtopic.php?t=7979](http://www.murga-linux.com/puppy/viewtopic.php?t=7979)).

---

### Post by Ripfox on 2007-12-25
To clarify, there is NO ethernet. The only means I have to connect is wireless usb. That dd command looks like the answer to the floppy problem, I'll try that and report back. Thank you all.

---

### Post by Ripfox on 2007-12-26
New info...I happend to be able to make the boot floppy mentioned a few posts back, but it just said "no cdroms found at all". I think this is due to the cdrom being hooked up via usb cable. Now my next logical move is to find a floppy image that scans for usb ports maybe? Back to my original post, htis is what "wakepup" does, but it will only detect a puppy install disk in the cdrom. You see it scans ALL removable media for the puppy install files, and even though the cdrom is hooked up via usb adapter, it finds the files when it scans usb ports on the cdrom. Hopefully I am explaining this correctly.

---

### Post by Ripfox on 2007-12-26
bump

---

### Post by agurk on 2007-12-26
I am out of ideas (that don't include hacking the wakepup floppy), except for hooking up the harddisk to another computer.
(Just so you know that I'm not ignoring you :))

---

### Post by Ripfox on 2007-12-27
No problem. Hacking the wakepup floppy...hmmm, this sounds like a good idea. I will post the files it contains, and maybe someone can help me through this one.

---

### Post by maybeway36 on 2007-12-27
How about installing debian, then installing unetbootin, then installing ubuntu?
Sounds weird, but it might just work if you install debian from floppies.

---

### Post by Ripfox on 2007-12-28
How do you install debian from floppies? Do you have a link? I think I tried that a long time ago and got very confused. If I could get debian installed I would be happy with that! :)

---

### Post by Ripfox on 2007-12-29
Well, I got it on there. Server first, then icewm, xdm, synaptic, kazehakase and streamtuner+xmms.

I took out the hdd and just hooked it up to the usb converter thingy and did it from my box. Now comes the real problem...when I tried to boot to the newer kernel, it panics and says the cpu is too old. So I installed linux-generic and put it back in the laptop and that booted fine. BUT, the newer kernel was the one that detects and makes-go the wireless usb device!! Crap, I was almost there...

What do you all suggest I do now? Cusom compile a kernel? Never done it. 

Any help rox.

---

### Post by agurk on 2007-12-29
Make sure you have linux-restricted-modules-2.6.22-14-generic installed, if it's needed for your wireless chipset.

---

### Post by Ripfox on 2008-01-04
Did it, still no go on wireless...

---

