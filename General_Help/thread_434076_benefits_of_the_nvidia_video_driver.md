---
title: "benefits of the nvidia video driver"
date: 2007-05-05
forum: General Help
---

### Post by ym4546 on 2007-05-05
Hello everyone,

I have been using Ubuntu for about 8 months now. I have had very few problems with Ubuntu and am overall very satisfied with the experience i've had.

I have a question, however, about the proprietary drivers for video cards. I have been running on whatever Ubuntu, well Kubuntu actually, installed by default. I've never bothered to try installing the proprietary drivers. Just as an experiment, I tried installing Envy (0.9.2 - the "unstable" version from [www.albertomilone.com](www.albertomilone.com)) to install the nvidia driver. However, that caused my x server to stop working, so I used envy to uninstall my nvidia driver and things work just fine again.

I'm wondering what benefits there are to using the proprietary driver. I have an old Nvidia geforce 3 ti200, and i'm wondering if its worth installing the driver at all. Will I notice any kind of performance improvement. (I don't do anything fancy w/ my desktop... no beryl or the like: just productivity stuff such as using Kontact, OpenOffice, Firefox, sometimes Amarok, etc.).

Since my computer is somewhat old (1.7Ghz pentium 4, 256MB ram) I would like whatever would run best.

Thanks in advance for any advice you can give.

---

### Post by kodoku on 2007-05-05
> **ym4546 said:**
> 

Just as an experiment, I tried installing Envy (0.9.2 - the "unstable" version from [www.albertomilone.com](www.albertomilone.com)) to install the nvidia driver. However, that caused my x server to stop working, so I used envy to uninstall my nvidia driver and things work just fine again.


X will very likely break after installing a different video driver.  This was not "abnormal".  You needed to reconfigure X right after installing the new driver.  After using Envy, reboot, and you should be presented with a command line (no X).

Type
> sudo dpkg-reconfigure xserver-xorg
And follow the onscreen instructions, selecting the right drivers and resolutions.  Use Tab, space bar, and Enter to navigate.  

I guess installing it really isn't necessary if you don't plan to use beryl or something graphic intensive.  If its just productivity, then the generic driver would suffice

---

### Post by ym4546 on 2007-05-05
I tried using envy and ransudo  dpkg-reconfigure xserver-xorg, but that didn't seem to help anything

when i use envy, the entry for my graphics card says "nvidia"... if i change this to "nv" it works fine, but if i remember right, "nv" is the default driver, right?

Or am I mixing something up?

---

### Post by jynyl on 2007-05-05
Installing proprietary drivers are good if you want to use advanced graphics features, such as the OpenGL screensavers or games.  They don't make any difference with word processors, email, spreadsheets, etc.

I found envy was not reliable, worked sometimes but not others.  But I found this howto v useful;
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by mjpatey on 2007-05-05
For the moment, go back to the "nv" driver.

Then in Feisty, go to System --> Preferences --> Desktop Effects and enable Desktop Effects.  The system will let you know you'll need the proprietary driver, and ask if you'd like it installed automatically.

In my case, I said yes, and it installed it right then, and has been performing like a champ ever since!

A very easy, hassle-free "back-door" way to get the proprietary driver installed.

---

### Post by dcstar on 2007-05-05
> **ym4546 said:**
> 
........
I'm wondering what benefits there are to using the proprietary driver. I have an old Nvidia geforce 3 ti200, and i'm wondering if its worth installing the driver at all.
.

If it is an "old" Nvidia card, then you may have to install the nvidia-legacy driver.

---

