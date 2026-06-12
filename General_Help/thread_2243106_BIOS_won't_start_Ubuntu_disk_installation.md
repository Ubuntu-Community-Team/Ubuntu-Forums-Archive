---
title: "BIOS won't start Ubuntu disk installation"
date: 2014-09-06
forum: General Help
---

### Post by rs321 on 2014-09-06
Folks,

HP Pavilion G7
Bios: Insydah 20 (rev. 3.5)
14.04 64 bit

I have spent the last five hours trying to get the bios to recognize and start installation of 14.04 but to no avail.  It's a cheap bios but it worked when I first got the machine 2 1\2 years ago, although when HP found out I'd changed the OS they nullified my warrantee until I changed it back to Win7.  I want to make a dual-boot and feel confident I can do it but I first need to force the bios to boot the dvd before the system boots, and to this end I have crawled all over the bios trying to find any switch left unturned, etc.  (I should mention I don't have the capacity to burn a flash drive so that's not an option.)

I've read everything pertinent here and several other sources and am at a loss; it just isn't that difficult to do but I don't seem to be able to do it.  I can't use any Ubuntu tools because Ubuntu isn't installed, but perhaps there's some "back door" method someone could suggest?  I've made three different dvds to ensure I got one that everybody likes but all of them fail.

I want to install the 64-bit version but will go to 32 if necessary, although I fail to see how that would matter.  Any bright ideas for a stressing dude?

Thanks in advance,

-Randy

---

### Post by yancek on 2014-09-06
On my HP Pavilion Desktop, when I see the HP screen on boot there is a message at the bottom of the screen "Hit F10 to enter setup".  The F10 key is pretty standard with HP.  Are you able to get in to the BIOS?  Do you see a tab at the top for Boot.  There should be an option under that for Boot Priority.  If you don't see this you could try taking a picture and posting the image so we know what you have.

---

### Post by rs321 on 2014-09-06
Yancek,

Thanks for the speedy reply.

Yes, I'm sure I'm in bios.  I reset the pecking order so the dvd is on top and I save the changes before I leave.  One site wanted me put a plus sign by the dvd so it would know it was selected but trying that only got me a beep from the computer.

I don't have the foggiest notion how to take a picture of the screen or what to do with it after I take it but I'm willing to learn.

-Randy

---

### Post by egeezer on 2014-09-06
Are you sure your DVD drive is in good shape?

---

### Post by yancek on 2014-09-06
I don't know of any way to get an image of the BIOS other than using a digital camera and uploading the image.

---

### Post by rs321 on 2014-09-06
Folks,

Thanks again for the timely responses, but I think I figured out what's wrong and I'm not a conspiracy theorist.  When HP found I had switched to Ubuntu they went out of their minds but also sent me three DVDs with a fresh install of Win7 on them, rather than have me use the restoration DVDs they had me originally make.  I thought that was quite generous of them but after today's hassles I wouldn't put it past them to have included a bug on one of those DVDs that prevented Ubuntu (or anything) from loading a new OS.  The DVD works just fine but, simple as the installation is, the installation sequence does not.

One of these days I'll stop short of ripping out my hair and just format the whole HD and start from scratch; the worst that can happen is that I'll have a fresh install of Win7.

Thanks again,

-Randy

---

### Post by dragonfly41 on 2014-09-07
Although you mark this issue as solved I would be curious to know if your HP DVD release of Windows would install as a VM on Virtual Box installed on your Ubuntu 14.04.  But this requires a good amount of RAM for acceptable performance.

---

### Post by rs321 on 2014-09-07
dragonfly41,

I don't pack more than 4G ram and don't want to invest more into this HP POS, but I'm seriously thinking of trying to find a way around it just to screw with HP.  If nothing else I have an old Dell around that I might set up exclusively for this purpose.  I know a hacker who likes this sort of challenge but that will come at a later date.

Good idea, though, thanks.

-Randy

---

### Post by buzzingrobot on 2014-09-07
I think you're being overly paranoid about HP, frankly.  If the BIOS is set to boot first off the DVD, then if the image on the DVD was burned correctly and is actually bootable, not damaged or dirty, it should boot. 

If you have another machine available to you, see if the DVD will boot on it.

If the machine is a UEFI/Secure Boot laptop, perhaps disabling that might help.

---

