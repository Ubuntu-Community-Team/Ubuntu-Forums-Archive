---
title: "A plethora of problems"
date: 2007-08-25
forum: General Help
---

### Post by Jiran on 2007-08-25
Well, I have a number of problems with Ubuntu, so I thought I would make a single thread to try to cover them all! If anyone can help with any of these, that would be just swell. Here is what's up:

1) My wireless appears to suck. I can connect, and get on the Internet, but the speed is atrocious. It's not necessarily the router or anything, since I can achieve good speeds when I'm running Vista (same laptop). I tried the whole IPv6 thing with Firefox, but to no avail.

2) Some applications won't open when I launch them. Now, I can't for sure say this, but it appears to be limited to KDE applications. This namely happens when I try to run Amarok, Deluge, or even Konqueror. I'll launch the application in a number of ways (using AWN, the Applications menu, the terminal, or a right-click launch on a music file for Amarok), the mouse cursor will turn into the spinning thing, then it will turn back to an arrow without the application being launched.

3) Some applications crash (seemingly) randomly. I'm not sure if this is related to problem 2, but I'll be running something and it will just close. No error, no warnings, just close. I'll check the System Monitor and the process will have stopped. This has happened with Firefox and Rhythmbox that I can recall, though it may have happened with others as well.

Well, that's it for now. Again, if anyone can think of what I can do for any of these, that would be awesome. Thanks a bunch!

---

### Post by oldos2er on 2007-08-25
I'll try to help with #2. Are you running Gnome, or KDE? If you're running Amarok or Konqueror under Gnome, how did you install them? I just wonder if you're missing some dependency these programs need.

---

### Post by Jiran on 2007-08-25
Well, the weird thing is that I installed these applications a while ago (I tried out KDE but I prefer Gnome over it, so I got Konqueror that way) and they were working fine until about a week ago. Then Deluge stopped launching, then Amarok, and now Konqueror.

I ran apt-get install amarok but it said that I had the latest version, so I think I'm fine for dependencies.

---

### Post by Tom B on 2007-08-26
> **Jiran said:**
> 

1) My wireless appears to suck. I can connect, and get on the Internet, but the speed is atrocious. It's not necessarily the router or anything, since I can achieve good speeds when I'm running Vista (same laptop). I tried the whole IPv6 thing with Firefox, but to no avail.



It might not be your wireless- it might be Firefox. The Firefox that comes with Ubuntu seemed really slow for me as well. I switched to [Swiftfox]("http://getswiftfox.com/") and it is much faster. Note: although it is open-source, it is "non-free" in the sense that you can't redistribute it. It doesn't matter to me, although it might to you.

---

