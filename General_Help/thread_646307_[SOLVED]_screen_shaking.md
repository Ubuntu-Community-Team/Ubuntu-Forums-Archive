---
title: "[SOLVED] screen shaking"
date: 2007-12-21
forum: General Help
---

### Post by gishaust on 2007-12-21
hi everyone

i have just apt-get updated my ubuntu machine and then I restarted the computer. Now I can only get 800*600 resolution and nothing higher. It was running a 1000 something, and the screen now has a small shake in it where do i go to fix this issue.

gishaust

---

### Post by FuturePilot on 2007-12-21
What is your graphics card and how did you install the driver for it? This probably has to do with the kernel update and the graphics card driver.

---

### Post by gishaust on 2007-12-21
Thanks for the relpy

To answer your question, I don't know what my graphics card is how do you fine that out? and second I have never installed a graphics driver in ubuntu how do i do that?  

Sorry for that lack of  information.

---

### Post by gishaust on 2007-12-21
I have just did a quick search and found a forum that sayes the following command showed my vga 
card. I think!!! but I don't know how to install a driver. This was the command 'lspci'

This was the outcome.
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

---

### Post by gishaust on 2007-12-22
I have killed it?????

I found a site and tried to  configure xorg oh no! When I resarted the computer: well lets just say it is visual impossible to see the words ubuntu right now. I have tested the screen on other  computers and it works fine.

But how do get the old screen to show.


Please!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


gishaust

---

### Post by gishaust on 2007-12-22
I have pressed Ctl-Alt-F1 to get into a terminal and was able to reconfigure xorg 

This is how I opened xorg, dpkg-reconfigure xserver-xorg. Now I have to work out how to rebuild it so it will work.

---

### Post by gishaust on 2007-12-22
I have been trying for a while now and can get it to work. Does anyone have any information that could help me. I have been going through xorg and it will won't work. i keep get it is configured wrong.

---

### Post by gishaust on 2007-12-23
this is solve re-installed the xorg.conf file restart unbuntu.

---

### Post by remali on 2008-03-27
I have about the same problem. I only can have 800x600, because in 1024x768 it shakes a lot.
I tried many things and every time i crashed it I used
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to reinstall xorg.conf. I also tried it about 20 times setting the resolution 1024x768 and higher. But nothing happened. What exactly did you do???

---

### Post by matogrosso on 2008-03-29
Did solve my problem. Thanks !

---

### Post by gishaust on 2008-03-31
Oh no.

I saw the above fix and gave it a go and now my machines screen is shaking like nothing else. I know it created a backup but because the screen is shaking I can't  get to the xorg file. how do I get ubutnu to go to the terminal before it boots with the vesa drivers so that I make the changes

---

