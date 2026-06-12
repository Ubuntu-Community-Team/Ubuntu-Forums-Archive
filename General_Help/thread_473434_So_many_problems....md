---
title: "So many problems..."
date: 2007-06-14
forum: General Help
---

### Post by stevenziggy on 2007-06-14
I'm new to Ubuntu and so far I've hit nothing but problems...

1.) My computer keeps randomly freezing, so that all i can do is unplug the computer and reboot.

2.) This happened last night while i was updating Ubuntu, and now the only way I can sign on is using a GNOME only session.

3.) I tried to use my LiveCD to reinstall Ubuntu, but when I try to open the CD-ROM drive it gives me an error message saying "Unable to mount selected volume"

4.) I don't know exactly what i can and can't download online because of error messages.

Can someone help me?

---

### Post by southernman on 2007-06-14
With what little info you give, I'd say a reinstall may be best... Read as practice makes perfect. ;)

When the livecd is through booting click on the little icon thingy that says "install" and continue to follow the prompts as your move through the six steps..

Good luck and Welcome to Ubuntu. :)

---

### Post by stevenziggy on 2007-06-14
I have trouble accessing LiveCD though...

---

### Post by southernman on 2007-06-14
*scratches head*

If you put it in your cd tray and reboot? That's how you'll need to do it.

---

### Post by stevenziggy on 2007-06-14
okay i just tried it... it still just boots into the ubuntu log in screen.

I don't think it is reading the disk

I went to setup and made the cd-rom drive the boot priority...  but it still won't go to it.

Is there anything I have to do during the boot to get to it?

---

### Post by southernman on 2007-06-14
If you setup your BIOS to boot from the cd first, then you have a problem with a cable, power connector, or the cd drive itself.

---

### Post by stevenziggy on 2007-06-14
okay i'll check the connections

---

### Post by trippinnik on 2007-06-14
As long as the CD-rom is the device the computer tries to boot to before the hard drive no.  Some bios will let you hit a key to select a boot source too.  The disk you have may be bad too.  
You said your hard drive couldn't be mounted?  Have you had a lot of problems in Windows as well?  When you don't shut down the computer cleanly Linux will run fsck on the drive if there are serious errors it won't mount the drive.  You also mentioned a 'Gnome only session' what do you mean by this?  Gnome is the default Desktop environment for Ubuntu.  If you give us a little more info, we may  be able to help.

---

### Post by simonn on 2007-06-14
Don't reinstall. That is sooooooooooooooooooooo windows!

It sounds like you have duff memory. Reboot, or maybe using the live CD boot, into memtest86+ or whatever it is called - there will  be some sort of test memory or memory test option in the boot menu - and test your memory.

Linux (and other unixes) do not really have the concept of free/unused memory like windows (pre vista) does. Linux will use most of memory not required by applications and the kernel (what would be free memory in windows)  to speed up the system by caching and buffering stuff. However, this means that when using linux you are almost definitely going to be affected by knackered memory, and quickly at that, with the resulting freezes. In windows (pre vista) it might only manifest itself in a crash once a month or so.

---

### Post by stevenziggy on 2007-06-14
does duff memory mean bad memory?

thats possible, i took some memory out of an old computer and put it into this one. Now i have 384 MB RAM... one slot has 256 and the other has the added 128. maybe that messed it  up.

Will the memory test allow me to get back onto Ubuntu?



What I meant by "GNOME only session"...

When it goes to the log in page, you can chose between five sessions in the options menu... last, default, GNOME, Failsafe GNOME, and Failsafe Terminal. GNOME is the only one I could get to work for me.

---

### Post by simonn on 2007-06-14
> **stevenziggy said:**
> does duff memory mean bad memory?

Yes.

> Will the memory test allow me to get back onto Ubuntu?

Basically, memtest is it's own tiny tiny OS which only runs and runs only memtest automatically.

You will see the option on the boot menu when you try to boot Ubuntu.

Boot into it and leave it running the tests for a while.

---

### Post by stevenziggy on 2007-06-15
I ran memtest 86+ v1.65

When i stopped it... these were the results

can somebody interpret this for me?

Pentium III 1196 MHz
L1 Cache: 32K 11725 MB/s
L2 Cache: 256K 5315 MB/s
Memory: 382M 194 MB/s
Chipset: Intel i810e

Wall Time = 11:05:45 (hr,min,s)
Cached = 382 M
RsvdMem = 1712 K
MemMap = e820-Std
Cache = on
ECC = off
Test =std
Pass = 11
Errors = 4096
ECC errors = 0

I have no idea what to make of these numbers...

someone help?

---

### Post by shifty_powers on 2007-06-15
> **stevenziggy said:**
> I ran memtest 86+ v1.65

When i stopped it... these were the results

can somebody interpret this for me?

Pentium III 1196 MHz
L1 Cache: 32K 11725 MB/s
L2 Cache: 256K 5315 MB/s
Memory: 382M 194 MB/s
Chipset: Intel i810e

Wall Time = 11:05:45 (hr,min,s)
Cached = 382 M
RsvdMem = 1712 K
MemMap = e820-Std
Cache = on
ECC = off
Test =std
Pass = 11
_**Errors = 4096**_
ECC errors = 0

I have no idea what to make of these numbers...

someone help?

I would think it is safe to say that your memory is fairly buggered there.

Course it might not be both modules. Try running memtest86 on each module in turn. see if they both return errors or just one of the memory modules....

---

