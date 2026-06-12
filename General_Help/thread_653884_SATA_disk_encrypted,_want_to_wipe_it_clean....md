---
title: "SATA disk encrypted, want to wipe it clean..."
date: 2007-12-30
forum: General Help
---

### Post by pangalactic on 2007-12-30
but I can't even get into the bios on my Thinkpad because it's asking for a disk password.

Here's the deal: I pickedup a few surplus Thinkpads. Two of them worked fine, no problems.  The third has the hard drive password. No body at the school knew anything about it, and I've even called almost every lab at the school they could have been used at, but nobody knows anything. I couldn't care less about the data that is on it, I just want to wipe and load fresh. I've looked everywhere I can think to look, and found tons of things on adding encryption,a little bit about cracking and finding forgotten passwords, most of which is very painstakingly delicate, slow, and/or requires soldering and reprograming chips- yikes.

Anybody have any ideas, or even where to look? Maybe I:m not looking for the right keywords? 

Thanks in advance...

James

---

### Post by cmnorton on 2007-12-30
What about booting with a live cd, and the running fsck on the unmounted volume that is password protected? In addition, if you have a USB disk housing or could borrow one, you could keep the PC running and interchange each sata drive in the usb housing.

---

### Post by shad0w_walker on 2007-12-30
Unfortunately to the best of my knowledge hard drive passwords are pretty much a deal breaker with these things. You might be able to lift the chip containing the password from the board and dump its contents then grab the password data from there, but that is way more hassle than its worth. You would probably be best off just getting a new hard drive and either using the old one as a paper weight or selling it on eBay as nonworking or unknown order.

---

### Post by pangalactic on 2007-12-30
That:s what I was afraid of. They're cheap now. It was an 80 gig anyways. 

I understand why the encryption is there, and why there can't be an easy way to decrypt it, but they really should be a way to destroy whatever tokens are there and reset. If a thief steals something, and you:re simply trying to prevent that data being in the wrong hands, which is better: making the disk wipable so nobody can ever get it back or keeping it intact, but encrypted? Given long enough, any encryption can eventually be cracked...

---

### Post by shad0w_walker on 2007-12-30
The wipable thing would be nice but that can be worked around just by not powering the device and extracting the data another way. 

Anyone who get that encryption will never be perfect or always safe should be looking at it as a way to keep the data safe long enough so that it doesn't matter. If it keeps the data safe for 100 years the odds are it won't matter what is on the drive, it won't be useful anymore.

---

### Post by psusi on 2007-12-30
Can you boot the laptop from a cd?  If so, use hdparm to wipe it clean and reinstall without the password.

---

### Post by shad0w_walker on 2007-12-30
I believe you will find his point is the drive itself is passworded, not the contents. As in the drive doesn't even start initialising until it is given the correct password, which makes wiping it impossible, as he said to begin with.

---

### Post by psusi on 2007-12-30
> **shad0w_walker said:**
> I believe you will find his point is the drive itself is passworded, not the contents. As in the drive doesn't even start initialising until it is given the correct password, which makes wiping it impossible, as he said to begin with.

I believe you can use hdparm to command the drive to format itself and throw out the password even though you have not used it to unlock the drive or know the old password.

---

### Post by dcstar on 2007-12-31
> **pangalactic said:**
> but I can't even get into the bios on my Thinkpad because it's asking for a disk password.

Here's the deal: I pickedup a few surplus Thinkpads. Two of them worked fine, no problems.  The third has the hard drive password. No body at the school knew anything about it, and I've even called almost every lab at the school they could have been used at, but nobody knows anything. I couldn't care less about the data that is on it, I just want to wipe and load fresh. I've looked everywhere I can think to look, and found tons of things on adding encryption,a little bit about cracking and finding forgotten passwords, most of which is very painstakingly delicate, slow, and/or requires soldering and reprograming chips- yikes.

Anybody have any ideas, or even where to look? Maybe I:m not looking for the right keywords? 

Thanks in advance...

James

[http://blogs.zdnet.com/storage/?p=148](http://blogs.zdnet.com/storage/?p=148)
or
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by srcharp on 2008-02-19
Are you sure it's a password encrypted hard drive and not a password encrypted bios?

Sounds like the bios for even with an encrypted hard drive you would be able to access the bios...reset the bios, on every laptop there is a key combination that does this, do a search

---

### Post by TheCowGod on 2008-02-19
Read this thread [http://www.hardwareanalysis.com/content/topic/34045/](http://www.hardwareanalysis.com/content/topic/34045/) mainly the last post. I think it may be your solution.

---

