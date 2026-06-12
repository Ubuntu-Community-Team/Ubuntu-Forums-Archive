---
title: "Uninstallation Help"
date: 2007-06-01
forum: General Help
---

### Post by Coyu3 on 2007-06-01
Here's my situation:

I had a PC running on Windows XP Media Center. Formatted the main HDD entirely, installed Ubuntu in it's place.
After this, I realize that, save for the input devices and the video devices, almost everything I use is incompatible (Hardware as well as software. I expected this, yeah, but it turned out to be more than I expected.) with Ubuntu.

The PC is NOT connected to the internet. My modems and USB adapters are incompatible, and the installation of drivers onto it, by transferring them off this Windows XP PC that I'm writing this on, to the Ubuntu PC on external media, is far too much of a hassle. 

How do I go about wiping the HDD entirely? I want to get Windows XP installed as the main OS, and all traces of Ubuntu removed permanently from the disk.




From what I experienced, though, Ubuntu's a very nice OS. It's light, it's speedy, and it's a great study system with all of it's built-in note-taking tools, and efficient layout.

Unfortunately, it just does not suit me for what I need in a workhorse PC.

-Thanks.

---

### Post by pbw on 2007-06-01
> **Coyu3 said:**
> 
How do I go about wiping the HDD entirely? I want to get Windows XP installed as the main OS, and all traces of Ubuntu removed permanently from the disk.


Just pop the XP install cd in., format/partition the drive and windows'll take care of the rest.

---

### Post by Coyu3 on 2007-06-02
The only CD that seems to be recognizable is the Ubuntu Live CD.

Nothing else. The other discs work fine on the other PC, but not on the Ubuntu one. =\

---

### Post by pbw on 2007-06-02
That's weird what works for one doesn't the other. Can't help ya though if the install cd won't boot.

how about plan B. Specifically what esoteric hardware you got that ubuntu's giving you grief with?

-- pbw

---

### Post by Coyu3 on 2007-06-02
In regards to the uninstallation:

Nevermind, it was only a matter of using DVD-Rs instead of CD-Rs for the Windows discs .ISOs. Guess my combo drive favors the DVDs over the CDs. >.>

Well, I think now I'm gonna do what I should have done in the first place. Use my 250gig HDD for Windows XP, and my little 9gig HDD to get more acquainted with Ubuntu, while still having the Windows drive for the usual stuff. =D



Now, in regards to the unusable hardware:

I have the XP PC that I'm using now hooked to a direct cable-line-to-cable-modem-to-router setup, with a Linksys WRTG54G router. (As I've read, the Linksys stuff is supposed to be very Linux/Unix friendly, but I've used this one since long before I had even heard of Ubuntu.)

The PC that had Ubuntu on it was to be connected through a wireless USB adapter, that receives the connection from the router on this XP PC. The USB adapter is Linksys as well, (WUSB54G) and getting the proper Ubuntu-usable drivers for it is a bitch without an active internet connection.

When I do install Ubuntu on the smaller HDD for a dual-boot, what would be the best way to go about getting the proper drivers for the Linksys USB adapter?

-Thanks

---

### Post by jjacobs2 on 2007-06-02
Use NDISwrapper with the windows drivers if it's not supported in linux.  The packages you need are ndiswrapper-common and ndiswrapper-utils-1.9 I think.  For setup purposes it might be easier to plug the comp in with an ethernet cable while you setup the wireless.  Linksys is somewhat supportive of linux but mostly with the linux firmware like dd-wrt that can be installed to improve their routers.  They aren't necessarily any better than most other companies when it comes to actual wireless cards.

---

