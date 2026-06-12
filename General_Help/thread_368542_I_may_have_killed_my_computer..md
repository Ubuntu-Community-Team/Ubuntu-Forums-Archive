---
title: "I may have killed my computer."
date: 2007-02-23
forum: General Help
---

### Post by barabaskid on 2007-02-23
It's possible, but let's hope not.

I switched to Ubuntu about 3 months ago, and have been running the Edgy Eft 6.10 release without a problem since then. I am a bit of a novice when it comes to the intracies of computers, but through some trial and error I was starting to understand how everything functioned. Having seen a video of beryl on youtube, I decided to take a stab at installing the program, so I could dazzle myself with lovely 3-D interfaces. I found a script here:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI")
and attempted to install it. Half way through downloading the packets it timed out on a particular server and refused to progress, so I closed the terminal.

I did some research and found out my 3D rendering wasn't turned on. As I bought the laptop in question second hand, I wasn't sure exactly what kind of card I had (though I was 99% sure it is an ATI card), so, after again scouring the web, I used: 
> nano /etc/X11/xorg.conf
to find the sepcific device. But I wasn't sure were to look to find out the specific model of the card, so I gave up, shut my computer down, and went to class. When I arrived and started my computer up, it went to the first load/splash screen for Ubuntu without a problem, that lovely orange bar even scrolled to the right as it hummed, but rather then going to my name/password, it flashed to a screen that looked a lot like BIOS. It said:

> 
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server input to diagnose the problem?

Yes    No


I opted for yes and recieved the following data:
> 
(==) Log file: "/var/log/Xorg.0.log", Time: Fri, Feb 23, 10:10:09
(==) Using config file "/etc/X11/Xong.conf" f"
(EE) No devices found

Fatal Server error
No screens found       f"


It then asked:

> Would you like to view the detailed X server output as well

I hit yes, and was shown a good 10 pages of scrolling data, none of which I understood, followed by:

> The X Server is now disabled. Restart GDM when it is configured correctly

So I cannot get my computer to load, and am frankly baffled and what went wrong, what it means, and how to fix it. Any help or advice would be greatly appreciated.

If I didn't provide some salient information that is need I am sorry, and would be happy to do so on request. Just let me know what information is needed and where to find it.


Cheers Much,

BarabasKid

---

### Post by Johnathon on 2007-02-23
To fix it quickly, hit Alt+Crtrl+F1 at the same time. 
Login, and then type 
```
sudo dpkg-reconfigure xserver-xorg
```

enter your sudo password, and go through the process, answering the questions. 

Once you have completed, your system should work. 

You can find out what graphics card  you have, by doing 
```
lspci
```
in a terminal.

HTH

---

### Post by Nythain on 2007-02-23
hmm... id try re-installing the video drivers you used, then a sudo dpkg-reconfigure xserver-xorg and see if that gets things going... after that reboot, and sudo /etc/init.d/gdm start should hopefully do the trick

---

### Post by barabaskid on 2007-02-23
I tried that sudo task, and the first page has a list of video cards but does not have the option for Intel, which, according to the specs for my system, I have. Specifically:

> 	Intel® with 32 MB UMA Video Memory (chipset integrated)

Is there a different option I should select for the video card? Help is again appreciated.

***EDIT*** I'm an idiot, but I fixed it. Thanks much for the help, it was greatly appreciated!

BarabasKid

---

### Post by Johnathon on 2007-02-23
Out of curiosity, what was the problem?

---

