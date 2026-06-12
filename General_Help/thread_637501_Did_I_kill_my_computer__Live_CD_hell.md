---
title: "Did I kill my computer???  Live CD hell"
date: 2007-12-11
forum: General Help
---

### Post by Greensound on 2007-12-11
Hi,

I'm very new to linux.  Out of sheer curiosity, I downloaded ubuntu, burned the image to a cd, and decided to give the live cd a whirl.  I use an IBM Thinkcentre 818956U computer.  

I put the cd in, restarted my machine, pressed f1 to get the BIOS screen, and modified the start sequence from

Removable
Hard Disk 0
CD/DVD
Network

to

Removable
CD/DVD
Hard Disk 0
Network

I pressed saved and exit ......then my computer just shut off.

I tried it again, with the cd in another cd drive - it just shut off.

Then the unthinkable happened.


I removed the cd, went into BIOS, and changed the startup sequence back to it's original form - save and exit - the computer shuts off

I tried turning it on again, it shuts off.  I don't even get the welcome screen, it shuts off right before it usually boots.

I tried other variants of start up sequence, failure every time.


I'm very concerned, I have a lot of my files back up, but there are a few (including a piece of production that has been in the works for over a year) that I can't afford to lose.  I know, this was stupid, I should have backed up everything, but for some reason I was confident nothing like this would happen.

Can anyone help?  I'm desperate.

Thanks

---

### Post by matthewcraig on 2007-12-11
Your BIOS is completely separate from the Ubuntu boot CDROM or even your Windows hard disk installation.  It sounds like your BIOS is failing.  If so, this problem has nothing to do with the Ubuntu software or the Windows software.  You should call the technical support line for your computer manufacturer and get the problem resolved.  Most likely, all your data is safe on the hard drive, it's just that the BIOS on the computer cannot figure out how to start the system and boot an operating system.  Call the hardware technical support people.

Oh, and good for you for trying out Ubuntu.  Too bad you had this bad experience when you were ready to try it.

---

### Post by Thanoulis on 2007-12-11
It is BIOS fault...did you get any beeps before your PC shuts down?(Just to know, beeps represent the kind of problem your computer-motherboard faces)
It is surely not fault of ANY LiveCD....
Ah!Do not panic!Your HDD is 99% safe!

---

### Post by amugofcoffee on 2007-12-11
Calmly remove your hard drive, place it into another computer and boot from it. If it works, then your BIOS is screwed.

---

### Post by njaneardude on 2007-12-11
Boot up, press the Pause/Break button.  Your Bios info should be displayed.  Do a Google search and usually you will find a flash utility that will fit on a floppy (If your pc has a floppy drive)

Boot from the floppy, there will be some scary messages but pretty much select the defaults and your bios should be back in business.

:guitar:

Just wanted to use the guitar dude

---

### Post by Greensound on 2007-12-11
Ok, so I attempted to turn on my computer this morning...... and amazingly windows booted up.  I did nothing different than before in terms of turning the computer on, except this time I crossed my fingers.

Weird.

I just updated my BIOS - I think I'll give the live CD another shot tomorrow - however I feel a bit hesitant now.  

Hmm, I hope my BIOS is ok

Thanks everyone for the speedy and detailed help!

---

