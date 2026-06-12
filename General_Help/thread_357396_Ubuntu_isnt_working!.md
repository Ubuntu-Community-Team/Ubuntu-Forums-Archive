---
title: "Ubuntu isnt working!"
date: 2007-02-09
forum: General Help
---

### Post by cyborg939 on 2007-02-09
i have just installed ubuntu on my machine and the first time i booted it, the loading window came up, then the screen went blank. i pressed the power button briefly and then a command prompt-like windows came up. the ubuntu desktop never showed up. what is the problem?:mad:  i will provide whatever info you need to help me troubleshoot this problem. thanks

---

### Post by lhtown on 2007-02-09
Did the Live-CD work ok?

---

### Post by Sqwishy on 2007-02-09
wait and this is after you login?

---

### Post by nickoli_02 on 2007-02-09
Your description is pretty vague. You say you get a command-like prompt instead of a login screen when ubuntu boots, correct? This is called a terminal in unix. You can enter commands and navigate around. Are you logged in as root automatically at the terminal, or does it prompt you to enter a login/password? Please provide more info :)

---

### Post by cyborg939 on 2007-02-15
live cd doesn't work, no, not terminal, i know what that looks like. my uncle says it is something like xwindows, that having a problem. something to do with the video driver?

---

### Post by nickoli_02 on 2007-02-16
Yea xserver is probably trying to use the wrong drivers. Boot the kernel in recovery mode, and when you get into the terminal type dpkg-reconfigure xserver-xorg. Select "vesa" from the list of drivers, then choose what you want for the rest of the options. When you're done type "startx" in the terminal to start xserver, and you should be good to go. Next you'll want to install a better driver for your video card. If you have an ati card you'll want [fglrx]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide"), and if you have an nvidia card you'll want the [nvidia drivers]("http://www.ubuntuforums.org/showthread.php?t=261162&highlight=nvidia+drivers+howto")

---

### Post by DJNOVA2006 on 2007-02-17
Ive had a similar problem? I used to have a blinking _ after the boot loader was complete. Ended up just using vmware on my machine. But i did manage to install 6.10 on an older machine with no uprated graphics card, just a standard video display. But i can only get 640*480 screen res and this is highly annoying as most of the windows have the bottom's cut of so you cant press the OK or Cancel buttons to progress anywhere. Ive tried the
sudo dpkg-reconfigure xorg-xserver from terminal but it says something like but not exactly that xserver doesnt exist? I can try the command line again if it'll help to get the exact error msg if anybody would like?

---

### Post by cyborg939 on 2007-02-24
I can't even get past the prompt screen with the options that say "Start or install Ubuntu", etc. I can't even get to terminal even through there? If I can, how do I start in recovery mode when the OS isn't even installed? Could you help me with that the Ubuntu install screen would come up and I would be able to install it?

---

### Post by abizdafuzz on 2007-02-24
I had a similar problem when I first installed Edgy. I would login and the screen would go blank. I'm using a laptop with an ATI Radeon 9000 video card. I found out that if you unplug the power supply before you log in it boots up just fine. Anyone know why that is?

---

