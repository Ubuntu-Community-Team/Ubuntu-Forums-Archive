---
title: "Forcing PAE does not work"
date: 2016-02-04
forum: General Help
---

### Post by LUser104 on 2016-02-04
Hello,

I wanted to try Lubuntu on my Toshiba SM30-154. It has a Pentium M 1.4GHz and 1.25GB RAM. I used a bootable USB and followed the instructions on how to force PAE. After hitting 'try Lubuntu', it first seemed to work normally. I was warned about PAE being forced. After a few seconds, the screen started to fill with ^[[3~ . After another few seconds, these would go away and the Lubuntu logo would show up. However, the display started to flicker. It would stay on for a fraction of a second and then turn off for a second or two. The backlight turned off when the image turns off. This did not happen back at the screen where you can choose to install of try Lubuntu, so it is not hardware-related. The computer does seem to make some progress at first, since the on-screen text changes every time the screen turned on, but after a while it got stuck, or at least I think so (I can't really see that well what it is saying...). I do not know what is causing this.

I tried multiple USB's and also tried this with a CD, and also tried Ubuntu. I included a picture I took from the screen.

Som time ago, I also tried to install the last version of Lubuntu that did not require PAE and then upgrade to a newer version, which gave me the same result.

Thanks in advance.

[IMG]http://i.imgur.com/m4wo0yT.jpg[/IMG]

---

### Post by sudodus on 2016-02-04
Welcome to the Ubuntu Forums :-)

I'm not sure that your problem is due to PAE. It might also be due to problems with a driver, for example for the graphics chip or wifi chip. Please tell us about the graphics chip and wifi chip (they might be different from what we see, if we browse the internet for Toshiba SM30-154). All current Lubuntu versions work in my IBM Thinkpad T42 with Pentium M 1.7 GHz and 1.25 GB RAM. Even the developing version Xenial Xerus works.

If it is this Graphics Controller: NVIDIA GeForce FX Go5200 - 64 MB, you might have problems with the driver. Maybe it works with the built in driver, maybe you need the boot option **nomodeset**, and can install a proprietary nvidia driver. I think other people know better than I how this graphics card works with linux. Maybe an older linux version is more likely to work with this old card.

You enter the boot option nomodeset near forcepae (with a blank character between them)

-o-

Which version of Lubuntu did you try (14.04.1 LTS, 14.04.2, 14.04.3 or 15.10)?

You can also try a light-weight community re-spin based on Ubuntu 12.04 LTS, for example Bento, Bodhi, LXLE. These promise support until April 2017.

Other options are Knoppix, and some Puppy linux flavours: Wary Puppy and TahrPup.

See this link for more details: [Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by LUser104 on 2016-02-04
Thank you for your fast reply.

I tried version 15.10.

The GPU is indeed a FX Go5200. I tried to use nomodeset and - it worked! The weird signs while starting up were still there and after that the screen flickered (however this time it did stay on, it was another kind of flickering) but after a few minutes I was on the desktop (instead of waiting for hours without any result...) 

Thanks a lot!

---

### Post by sudodus on 2016-02-04
I'm glad it works now :-)

If you have a related problem, you can continue in this thread. Otherwise, if you have another problem (or question), please start a new thread with a good descriptive title. That way you have the best chance to get attention by people who can help.

If/when you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by LUser104 on 2016-02-04
Ok, thank you for your help :)

---

