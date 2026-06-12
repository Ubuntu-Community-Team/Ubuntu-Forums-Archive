---
title: "Ubuntu 12.04 LTS fan control not working"
date: 2013-03-14
forum: General Help
---

### Post by packetpenguin on 2013-03-14
I have been an Ubuntu user for the past 3 years - using Ubuntu 10.04 LTS, and I switched to Ubuntu 12.04 LTS a few days ago. I have to say this is the buggiest piece of **** operating system I have ever used and I have lost hope for Ubuntu becoming a mainstream operating system with the current deadline model.  My current head ache is with my fan control. I just booted into Windows XP Professional to play some Total Annihilation and noticed the room went silent, then realised Ubuntu 12.04 LTS fan control isn't working.  I installed the 'lm-sensors' and 'fancontrol' packages, but this did nothing.  Can someone please give me an idea what could be going on?

---

### Post by 3rdalbum on 2013-03-14
The manufacturer or assembler of your computer installed some software on Windows to control the fan, instead of the more logical way of doing it: Tell the computer's BIOS to handle fan control.

You just need to go into the BIOS and set it up to control the fans itself.

12.04 is no more buggy than 10.04; the main problem is that too few people test Ubuntu development releases and file bugs. You can help; install 13.04 before beta and report any bugs you find. Just because you're having problems, doesn't mean that everyone is (or that the problems you're having are widespread).

---

### Post by krishna.988 on 2013-03-14
Simple as 3rdAlbum says it is a bug and in general hardware manufacturers doesn't release the exact specification to create the driver for Linux. And many developers don't bother to do one as it doesn't pay.. So most drivers are either reverse engineered from Windows driver or written with available specification. This is no one's fault.. No one is to blame..

---

### Post by schragge on 2013-03-14
Without you giving any information about chipset on your mainboard it's impossible to help. You said you installed *fancontrol*. Have you run [pwmconfig](http://manpages.ubuntu.com/manpages/precise/en/man8/pwmconfig.8.html) then?

---

