---
title: "Ubuntu on screen or blank screen when trying to boot? HELP"
date: 2014-01-21
forum: General Help
---

### Post by adrian13 on 2014-01-21
I have an acer aspire 5336 with 3gb ram and 250gb hard drive space and when i went to install ubuntu which was ubuntu 12.04 LTS the screen would boot the logo or boot the BIOS but wouldnt go to the setup for ubuntu. (I HAVE WINDOWS 7 HOME PREMIUM INSTALLED JUST INCASE IF YOU GUYS WANTED TO KNOW). It would be just a blank screen. Then i connected an external monitor to see if there was anything happening and the ubuntu setup loaded but was not showing the laptop screen but only on the external monitor screen. I know that the laptop screen works because when i boot into windows it loads up fine. Please help i dont know if its a driver problem or an OS problem. I tried other linuxes like Zorin and that didnt load up either.

---

### Post by adrian13 on 2014-01-22
Hey guys can anyone help i really need this ubuntu os. Please

---

### Post by jp734 on 2014-01-22
Was the external monitor using the vga connection? I am not an expert on this one but I would try installing while connected to the external monitor and then use xrandr after to get the screen activated after that.

---

### Post by adrian13 on 2014-01-22
I was using vga as the connection and what happened was that to install Ubuntu i booted into Windows and used wubi to install it. And what do you mean by xrandr to activate the screen?

---

### Post by jp734 on 2014-01-22
xrandr is a utility used to setup screens. someone who has dual screen setup can use it to activate them and setup which one goes on the left and right or simply turn on and off a screen. Also look at the /var/log/Xorg.0.log file for some clues on what's going on. You might have to create a custom xorg.conf file if you don't have one yet, usually stored under **/etc/X11**. Now though, instead of having the "xorg.conf" file, it is broken down into sections and you can find them stored under **/usr/share/X11/xorg.conf.d** folder. But check both to make sure. 

Find out what driver is being used as well. Enter "lspci -k" and look for your card. This is what it shows on mine:
> 
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5430 Series]
	Subsystem: ASUSTeK Computer Inc. Device 3000
	Kernel driver in use: fglrx_pci

---

### Post by adrian13 on 2014-01-22
alright ill see and ill get back to you. Thanks i appreciate it.

---

### Post by adrian13 on 2014-01-23
i cant find the thing you are saying. Like it doesnt show which driver is in use.

---

### Post by jp734 on 2014-01-23
So what video card are you using? Have you tried to install the driver for it? You can also look at the /var/log/Xorg.0.log to see what modules are loaded. Have you looked at it yet to see what the problem is?

---

### Post by adrian13 on 2014-01-24
I dont know like its a laptop. I dont know how to install the drivers for it but i will look it up asap and get back to you.

---

### Post by adrian13 on 2014-01-24
i figured out what the problem is. The problem is that the screen is working like the built in one is working but its very dark. What im trying to say that its not Bright at all like no brightness at all, but i could see like the shadow of the screen and the ubuntu interface. (Sorry if ikm confusing you im trying to describe it to my best of abilities). Like you could see the ubuntu side docky and the graphical user interface. But you have to look very closely. I tried to raise the brightness but that doesnt work.

---

### Post by jp734 on 2014-01-24
Hmm, interesting. Not sure I could help you on that but would love to find out what the solution is when you figure it out :-). Good luck.

---

