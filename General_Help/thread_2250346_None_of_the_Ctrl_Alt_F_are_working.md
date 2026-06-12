---
title: "None of the Ctrl Alt F* are working"
date: 2014-10-28
forum: General Help
---

### Post by Joseph_Hamer on 2014-10-28
Hello, I'm new to ubuntu and I am trying to install my NVIDIA Driver. I've been looking on the forums for two days to find a sultion but no luck has come apon me. The closest thing that has resolved it is by closing the x-server, and to do so I have to press ctrl alt F1, but for some reason it just comes up with a black screen, this happens with all the F*'s appart from ctrl alt F7 which successfully takes me back to the main gui. So if someone could help me that would be great :)

---

### Post by coffeecat on 2014-10-28
Welcome to the forum.

It sounds as though you are trying to do it the hard way. Advice for newcomers: as an initial strategy, do not attempt to download and install the driver from the nvidia website.

You don't say which version of Ubuntu you are using, but if you are running either the 14.04 or 14.10 release of Ubuntu with the Unity desktop, click on the cogwheel top right of screen. Click on System Settings -> Software and Updates -> Additional Drivers tab. It should prompt you for the most appropriate version of the proprietary driver and you can install it from that GUI utility.

Is the default open-source nouveau driver not suitable for you?

I can't explain the black screen with ctrl-alt-F1. Is it completely black, or is there some text at the top?

---

### Post by Joseph_Hamer on 2014-10-28
It is completly black. No text can be put into it. Also I've just tried doing the automatic driver search and it has come up with "No additional drivers avalible" and yes. I am using that version of Ubuntu

---

### Post by coffeecat on 2014-10-28
You seem to have two problems. Your virtual terminals are not displaying properly and additional drivers is not prompting for drivers for your hardware. The VT (virtual terminal) should display two lines of text - an identifier for which version of Ubuntu you are using together with tty*n* where n is a number, and the second line is a login prompt. I don't have any ideas about the VT failure to display at the moment - perhaps others will come in.

Let's look at your video driver problem to be going on with. I think we need to confirm what GPU you have. Open a terminal on the desktop - the quick way is with the keyboard shortcut ctrl-alt-t - and run this command:

```
lspci | grep -i VGA
```

Post the output - you can copy text in the terminal by highlighting it with the mouse, right-click -> copy - and we can take it from there.

---

### Post by Joseph_Hamer on 2014-10-30
Here is what the output was
02:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)

---

### Post by C@mM! on 2014-12-08
Not trying to thread jack, but running into the same problem with no console output as the OP. Funny thing is, its not a lock, as ctrl alt f7 gets you back to unity fine.

Ubuntu 14.10, NVidia 970 (which is Maxwell generation same as the 750 Ti) - apparently we don't get driver support thru the "additional drivers tab" until the next major patch due to February? And running edgers ppa just to get a driver working is a little gross for my liking so getting to console in order to install the binary driver is kind of a must.

As for Noveau, it has no support for Maxwell generation cards (750 Ti + 900), and besides that, barely works anyway.

My suspicion is that maybe the resolution is part of the problem (stuck at 1024x768 without any drivers).

Edit: I don't have a fix for the console not working (drivers don't fix this), but you can get the driver installed by booting in recovery mode and bring a console up there.

---

