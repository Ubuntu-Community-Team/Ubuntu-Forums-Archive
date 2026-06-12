---
title: "kuula.co webpage not loading for version 20.04"
date: 2021-11-29
forum: General Help
---

### Post by robert-e-1953 on 2021-11-29
NAME="Ubuntu"
VERSION="20.04.3 LTS (Focal Fossa)"

The webpage for :
kuula.co

causes the web browser to hang (not load). I think the problem is a webpage media file not loading. In Windows10 the display which doesn't load is a motion graphics. I tried updating the video codecs. Same problem with windowsFX11.

---

### Post by #&amp;thj^% on 2021-11-29
Pipes clogged maybe, loads just fine here. Try again, also with different browser.
Also you can disable auto video on sites in firefox, Head to 
```
chrome://flags/#autoplay-policy
``` and change the autoplay setting to &#8220;Document user activation is required.&#8221; It&#8217;s much less user friendly than Firefox&#8217;s solution.

---

### Post by ActionParsnip on 2021-11-29
What browser(s) have you tried?

---

### Post by Doug S on 2021-11-29
Works for me also. I used firefox browser (94.0.2 (64-bit)) from a windows 10 computer. And a Ubuntu 22.04 Desktop VM with firefox (94.0.2 (64-bit)). And a Ubuntu Desktop 20.04 VM with firefox 94.0.

---

### Post by robert-e-1953 on 2021-11-29
I think it's a non solvable (too hard for me to solve?) graphics card problem resulting from old hardware choices in a years old reconfigured UbuntuStudio version 11 machine.

When  I use Ubuntu 20.04 'liveSession' on a usb drive on a laptop with its more  recent hardware configuration (intel core i5, etc) the website (kuula.co) works/loads just fine. I assume the graphics card is the  problem for my older (now a) 20.04 machine. The Nvidia driver detected in 'software and updates' on the older hardware configuration machine is the  only driver of two choices that works for installed  Xubuntu 20.04. The second choice results in a 640 resolution.

The  360 files I store at kuula.co display correctly with 20.04 on the old hardaware machine using  provided links embedded into emails and sent from a Windows 10 laptop to  the 20.04 desktop.
[https://kuula.co/share/NY19Q?logo=1&info=1&fs=1&vr=0&sd=1&thumbs=1](https://kuula.co/share/NY19Q?logo=1&info=1&fs=1&vr=0&sd=1&thumbs=1)


Only the kuula.co  face page hangs on Ubuntu 20.04 with the older hardware configuration machine. 

I'd guess I'm stuck with the current  graphics card problem. Using Chrome browser on WindowsFX 11 from usb on  this older machine also hangs on kuula.co at the face page.

---

### Post by robert-e-1953 on 2021-12-11
> **1fallen said:**
> Pipes clogged maybe, loads just fine here. Try again, also with different browser.
Also you can disable auto video on sites in firefox, Head to 
```
chrome://flags/#autoplay-policy
``` and change the autoplay setting to “Document user activation is required.” It’s much less user friendly than Firefox’s solution.


problem solved by running Linux Mint in Compatibility mode.

Linux Mint ver 20.2
[https://linuxmint.com/](https://linuxmint.com/)

When run from a USB stick Linux Mint has a (hardware) 'compatibility mode' boot setting. Without choosing 'compatibility mode' the webpage
kuula.co
hangs like with my Ubuntu installation using these older hardware and graphics parts.

Booted from a USB stick in 'compatibility mode' gives a desktop resolution of 1024 x 768 (max) but the problem webpage loads and displays in less than 15 seconds.

I've read that Ubuntu does not support running in 'compatibility mode'.

'Compatibilty mode' is defined on the Linux Mint forum:
[https://forums.linuxmint.com/viewtopic.php?t=198531](https://forums.linuxmint.com/viewtopic.php?t=198531)

"Compatibility mode blacklists a wifi driver b43 because of some freezing  problems, disables fast graphics mode switching, disables the advanced  configuration and power interface and doesn't load the splash screen."

---

### Post by robert-e-1953 on 2021-12-11
Linux Mint installed and working

My Nividia Geforce 8400 video card (and other older hardware) is working well under an installed copy of Linux Mint version 20.2 at the highest 4:3 screen screen resolution supported (but not 16:10). The recommended Nvidia video driver installed without a problem. At a 16:10 screen resolution the problematic webpage loaded but the screen froze when attempting to click on the website menu. Changing the resolution to the highest 4:3 choice solved the screen freeze problem when clicking on the website menu.

---

