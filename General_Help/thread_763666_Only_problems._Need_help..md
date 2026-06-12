---
title: "Only problems. Need help."
date: 2008-04-23
forum: General Help
---

### Post by artti on 2008-04-23
Last wednesday i got new computer with Vista Basic. On sunday when restarting computer i got always blue screen. I don't like Windows at all. I didn't have even oportinuty to backup my data. Ubuntu LiveCD helped me out(again). Now i have installed it on that new computer. 

Here are my current problems:
[LIST=1]
[*]How i know that i have installed correctly graphic card drivers?
[*]I installed games like Open Arena, Tremolous, Sauerbraten. None of theme won't run. First two games gives me black screen and message that i have to change screen resolution. Only way to exit is to make restart. Running Sauerbraten in terminal shows me only "init: sdl".
[*]Watching Flash videos will crash my browser. Have to force firefox to quit.
[*]When i save password in firefox browser then it is saved under another user too.
[*]And tiny problem. My id-card won't work.
[/LIST]

Computer specification:
OS: Ubuntu 7.10
Graphic card: ATI Radeon X1200
Processor: AMD Athlon 64 4000+, 2.4 GHz
RAM: 1024MB
Computer: Fujitsu Siemens SCALEO La2609
Monitor: Fujitsu Siemens 19'' LCD monitor L19-8

All these problems give me headache. I appreciate any help.

---

### Post by overdrank on 2008-04-23
> **artti said:**
> Last wednesday i got new computer with Vista Basic. On sunday when restarting computer i got always blue screen. I don't like Windows at all. I didn't have even oportinuty to backup my data. Ubuntu LiveCD helped me out(again). Now i have installed it on that new computer. 

Here are my current problems:
[LIST=1]
[*]How i know that i have installed correctly graphic card drivers?
[*]I installed games like Open Arena, Tremolous, Sauerbraten. None of theme won't run. First two games gives me black screen and message that i have to change screen resolution. Only way to exit is to make restart. Running Sauerbraten in terminal shows me only "init: sdl".
[*]Watching Flash videos will crash my browser. Have to force firefox to quit.
[*]When i save password in firefox browser then it is saved under another user too.
[*]And tiny problem. My id-card won't work.
[/LIST]

Computer specification:
OS: Ubuntu 7.10
Graphic card: ATI Radeon X1200
Processor: AMD Athlon 64 4000+, 2.4 GHz
RAM: 1024MB
Computer: Fujitsu Siemens SCALEO La2609
Monitor: Fujitsu Siemens 19'' LCD monitor L19-8

All these problems give me headache. I appreciate any help.
HI and you may look at [[COLOR="Green"]Envy[/COLOR]](http://albertomilone.com/nvidia_scripts1.html) to help with the drivers

---

### Post by artti on 2008-04-23
Well i installed Envy. It did something without errors. Now when running Openarena or Tremulous then there is just black screen.

---

### Post by artti on 2008-04-24
I just found that Flash don't work properly on 64-bit system. Most things won't work under 64-bit system. :(

---

### Post by Tatty on 2008-04-24
> **artti said:**
> I just found that Flash don't work properly on 64-bit system. Most things won't work under 64-bit system. :(

Really?  Flash seems to work fine on my 64-bit install.  whats up with it?

and to check if your graphics card driver is installed properly, have a look in /etc/X11/xorg.conf - if under the section "Device" it says that the driver is fglrx then it has installed correctly.  If it says ATI or Radeon then it has not.

You may also want to open a terminal and run glxgears.  This will output a fps every 5 seconds into the terminal.  If the fps is in the 1000's then it is fine.  If it is in the 100's then it may not be so fine.

---

### Post by artti on 2008-04-24
xorg.conf says that i have graphics card driver installed properly.

Running glxgears in terminal gives me result 2740 frames in 5.0 seconds = 547.984 FPS

But is it possible that i have problems because i have installed Ubuntu that is for using on standard computers but not for computers with AMD64 processor?

---

