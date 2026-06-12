---
title: "Emergancy!!!!!!!"
date: 2007-07-30
forum: General Help
---

### Post by RevolutionMaster on 2007-07-30
My Ubuntu GUI won't load and when I boot it up, I get this screen after a little bit of text![IMG]http://i11.tinypic.com/6bd6emr.jpg[/IMG][IMG]http://i10.tinypic.com/6gwd9c7.jpg[/IMG] (I'm posting on windows. O.O >.>.

---

### Post by merlinus on 2007-07-30
May be your video card.  Post specs, and for your computer as well.

-merlin

---

### Post by Instigator on 2007-07-30
Indeed. I had this same problem except it was caused from messing with the video card driver. I accidentally uninstalled the proper drivers which screwed up the xorg.conf. So I rebuild xorg and then booted up enough to install the drivers and replace the xorg.conf file.

---

### Post by RevolutionMaster on 2007-07-30
ATI All in wonder 9000
120 gig and 80 gig maxtor drives
aah lemme just post the windows hardware manager picture.
[IMG]http://i15.tinypic.com/4v5h20p.jpg[/IMG]

---

### Post by b3y0nd on 2007-07-30
I just had the same problem. When i installed ubuntu I had a 128MB Nvidia card (TI 4200), after the install I figured I would put in a 256MB ATI (9600)... had same error when i rebooted. Took out Nvidia and put the ATI back in...boots fine now.

Im REALLY new to ubuntu and for the most part linux itsself, I believe you need to download the current driver for the video card you want to run, dont install just check mark the box for "download only".

Reboot

I believe it will fail again, at which time you should install the program from the shell. Write down the command(s)  prior to rebooting.

**** If I am wrong then someone PLEASE post the correct way, I am about to try and get my 256MB installed....doing the above.******

 Easier way?

---

### Post by Sayers on 2007-07-30
sudo su
dpkg-reconfigure xorg 
dpkg-reconfigure xserver-xorg ##if the top didn't work.

---

### Post by merlinus on 2007-07-30
It is mostr likely your ATI card.  Have you already installed ubuntu?  If so, this may work:

Ctrl-Alt-F1 to get to prompt

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

or reboot.

-merlin

---

### Post by RevolutionMaster on 2007-07-30
I'm going to try these tips now. Ty.

---

### Post by kens8 on 2007-07-30
I rand across [this]("http://ubuntuforums.org/showthread.php?t=414194") earlier.  Hope it helps

---

