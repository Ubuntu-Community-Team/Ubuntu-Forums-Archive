---
title: "Installing from an edited persistent usb: Will changes effect final install?"
date: 2013-04-03
forum: General Help
---

### Post by CaptainMark on 2013-04-03
So it's time for me to install Linux on my mums dying Windows laptop (lets face it, it was literally only a matter of time) I've made a live USB, and I gave it 2GB for file persistence.
If I edit/reconfigure the USB install, say I install copyrighted codecs, install Flash player and Chromium set up the desktop with all the beginner friendly options (like removing Unity and replacing it with Cinnamon :P) will these changes carry over to an installation made from this USB or will I end up with a vanilla install no matter how I change the live USB? Hopefully someone has tried this before and saves me the effort of a test install just to know the answer.

I'm hoping to be able to configure it before hand so I don't have too configure it all in one session next time I see her because I will undoubtedly forget something and get a call asking "Why wont X work?" 

Regards
Mark

EDIT: X being an unknown variable, I'd be bloody impressed if my mum knew what the X window system is.

---

### Post by dabl on 2013-04-03
No, your well-intentioned plan to do the world's most efficient installation is not going to work as you wished.  If she has an internet connection, verified by the Live CD connecting via ethernet, then you would be better off to make a plain text file of all the packages that you want to install, separated only by a single space.  I call this file "List of Useful Packages.txt".  Install her basic system from the Live CD, install any needed firmware or non-free drivers and get the video working correctly, and then paste in the list of packages after "sudo apt-get update && sudo apt-get install", and let it pull them in and install them.

---

### Post by C.S.Cameron on 2013-04-03
If you are using 12.04, you can make a modified Ubuntu installer using Remastersys.

---

### Post by CaptainMark on 2013-04-04
Alright, thanks for the tip, I'll look into to remastersys. I have a post install script for my own install but the things I was more worried about forgetting would be settings like disabling cinnamon's hot corners and things like that. I know there will always be something I'll think about later,

---

