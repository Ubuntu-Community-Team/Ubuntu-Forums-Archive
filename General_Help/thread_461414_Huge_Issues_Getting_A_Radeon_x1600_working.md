---
title: "Huge Issues Getting A Radeon x1600 working"
date: 2007-06-01
forum: General Help
---

### Post by The Creator on 2007-06-01
Hi fellow Ubuntu fans,

I could start with a huge introduction but i will cut to the chase. I am having troubles getting my Radeon X1600 to power on with the new feisty kernel. I am currently using the old kernel with the drivers from ati's website but it isnt working. I got catalyst working running the old kernel and when i go on the new kernel my screan doesnt turn on after the bootup process. It just goes blank.  I did tell it to use fglrx using sudo dpkg-reconfigure xserver-xorg and it is supposed to use the drivers. 

here is the output for my 3d capabilities.
john@john-desktop:~$ glxinfo | grep direct
\direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
 it isnt picking up direct rendering. I just really want to run beryl and cedega. Any help would be great. I would like to get direct rendering enabled, it is an awesome card. 


Thanks in advance,

The Creator

---

### Post by The Creator on 2007-06-01
bump

---

### Post by digitalpure on 2007-06-01
I am also looking for major help on this... I have been searching the forums (and still will) to try and figure this out...

---

### Post by The Creator on 2007-06-01
Is your card agp as well?

---

### Post by The Creator on 2007-06-01
bump

---

### Post by rbmorse on 2007-06-01
Take a look in the Apple section. The MacBookPro and Core2Duo MacBook Pro use the X1600 chip. There may be something there.

---

### Post by The Creator on 2007-06-01
this is an agp card though. the macs use pci ex.

---

### Post by RedSquirrel on 2007-06-01
This might help:

[ Installing Ubuntu 7.04: ATI X**** Cards]("http://ubuntuforums.org/showthread.php?t=414194")

---

### Post by The Creator on 2007-06-01
It isnt fixing it. I still cant launch beryl. I am still not getting direct rendering. It is a good card, i know that much and i get acceleration in windows and mac os x.

---

### Post by sabin126 on 2007-06-07
I'm having the same issue as well with the same card.  I've tried many different guides.  Any help would be great.

---

### Post by Stanko on 2007-07-09
i have RadeonX1600 and it's working with open gl support, but the beryl is not working
i'm working on it (it works on PCLinuxOS)...

but just go MAIN MENu -> SYSTEM -> ADMINISTRATION -> Restricted Driver Manager and enable driver for your ati card, it will download fglrx driver, and that's it

good luck

---

