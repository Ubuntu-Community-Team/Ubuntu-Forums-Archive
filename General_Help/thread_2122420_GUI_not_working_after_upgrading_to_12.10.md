---
title: "GUI not working after upgrading to 12.10"
date: 2013-03-05
forum: General Help
---

### Post by Roquentina on 2013-03-05
I'm sorry for posting if there is some thread like this one around - so just point me in the direction if there is, and I'll delete this thread, but I just can't seem to find any way to work this out.

I'm not that good with ubuntu, although I've had it since 10.10 and been upgrading ever since. I don't use that many programs, although I use this laptop daily, for browsing, music and video, (all of which has worked perfectly ever since I've switched from Windows in 2010.). Most of the issues I've had I've been able to solve by searching the threads over here, but now my laptop hasn't been working for over a month and I really need it. And none of the similar threads I've read doesn't seem to solve any of these issues.

Now, my laptop's quite old, it's Acer Aspire 5100 series, with an ATI Radeon graphic card - I've read that they are known for causing troubles. After I upgraded through update manager, the login screen worked just fine, but after I logged in, there was a message of something like "compiz closed unexpectedly"... And I don't have any bars, any icons, nothing, just the background picture. I can open the terminal, using ctrl+alt+t, but everything is very slow. A part of the update manager window appears - I see the updates being listed and stuff, but when I try to clik "install now" it takes forever for the option to highlight and actually start updating (the installing itself doesn't take that long, so I believe that graphics is the problem here).

I tried to reinstall ubuntu 12.04 - but something seems to be wrong with the usb installer I've made since it doesn't work on other computers either, and booting from cd/dvd isn't an option. So I was wondering whether there was something I could do using the terminal, to fix this. Please help.

---

### Post by schragge on 2013-03-05
If there's enough space on your hard drive, try to install another DE, e.g.
```

sudo apt-get install xfce4{,-goodies}

``` Login into XFCE session, and see if that will help your problem.

---

### Post by Roquentina on 2013-03-05
(Thank you!) Well - I installed xfce the way you said. But I can't seem to login into it. I guess it doesn't work the way I tought it would. How do I do that?

---

### Post by schragge on 2013-03-05
Have you got a round icon appear next to your username on the login screen? Click on it and select XFCE session.

---

### Post by kuifje09 on 2013-03-05
Maybe you need to go to the classic style?

Then you need to install 

sudo apt-get install gnome-session-fallback
Then login using the falback mode.

This will make your old video card usable, without all the fancy gnome features.
I needed it too for my riva-tnt card

---

### Post by ibjsb4 on 2013-03-05
USB not working?  Have you tried Unetbootin?  Xubuntu can be installed this way.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Roquentina on 2013-03-05
Wow. Thank you, guys.

@shragge - clicking the round icon on the login screen, done that, nothing happens. No new options, nothing. 
And as kuifje said, I tried to reinstall gnome, so I did that also. And also nothing happened. I also tried to install or run at least xubuntu's desktop, but that didn't work either - only after booting, the screen was no longer purple like ubuntu, but blue like xubuntu - but no way I could start it.
[COLOR=#000000][/COLOR]
Thanks for the tip about the usb - I did try, unetbootin and LiLi, and Universal Usb Creator... (This is already going offtopic) - but none of them works. Neither is my usb protected with that u3 thing. Don't know anymore.

---

### Post by grahammechanical on 2013-03-05
Do you get a Grub boot menu? If Ubuntu is the only OS you will not see the Grub menu but it is there. Press Shift repeated during the boot. When you see the Grub menu select Recovery Mode. As this is 12.10 you will find Recovery Mode under the Advanced Options for Ubuntu submenu. Once you have booted into Recovery mode you will see a menu. You can select Resume. That will load Ubuntu without a video driver. It may get you to a desktop where you can install a video driver. In 12.10 you go to System Settings>Software Sources>Additional Drivers tab. and make a choice from the selection of drivers that are there. Did you upgrade from 12.04? Then your machine will run 12.10. Installing other desktops will not solve your problem if the issue is with the video driver. You may find that the open source video driver (Nouveau) to be more reliable than some of the proprietary video drivers. Regards.

---

### Post by Roquentina on 2013-03-05
Yes, ubuntu is my only OS. I did try to reinstall my video drivers - there was a thread somewhere (or a question on ask.ubuntu) - I wanted to post it already, but can't seem to find it. 
Anyways. I will remember what you've said - since I've given up, and somehow managed to reinstall ubuntu 11.10 using a cd... I've got tons of other issues now, someting's wrong with the grub itself, it won't boot now. But not to go offtopic... Thanks, guys.

---

### Post by kuifje09 on 2013-03-05
Well reading all this, I think this is all very strange.
What could be of help is booting the "life"-cd/dvd  to see if ubuntu 11.10 or 12.04 could run on your hardware.
But I see you cannot use a DVD. And you also have problems with the usb?
This is the kind of problem I would like to see with my own eyes but it is just too far away.
I bet remote login want work.

But, after system has booted, which he does right?  can you type CTRL-ALT-F[1 2 3 4]  That would get you to a big console without the gui.
Then there is a change you can get some info from the logfiles. That must be a starting point I think.

---

### Post by Mark Phelps on 2013-03-05
You said you have a Radeon video card, and from what I could find, that uses an Xpress chipset.  

That's a very old chipset for which AMD restricted drivers haven't worked in a long time -- so if you were using the default Radeon  open-source drivers in 12.04, you should not have suddenly encountered a video driver problem upgrading to 12.10.

So, while it's possible, I suspect that the problem is not the Radeon video drivers.

---

### Post by kuifje09 on 2013-03-06
> **Mark Phelps said:**
> You said you have a Radeon video card, and from what I could find, that uses an Xpress chipset.  

That's a very old chipset for which AMD restricted drivers haven't worked in a long time -- so if you were using the default Radeon  open-source drivers in 12.04, you should not have suddenly encountered a video driver problem upgrading to 12.10.

So, while it's possible, I suspect that the problem is not the Radeon video drivers.

Isn't it when there is a problem with the video driver for a particular card, the system choose some falback mode, as in my case for the Riva-tnt it chooses the vesa driver. But in any case he should be able to get in the console mode. Right ?

---

### Post by Roquentina on 2013-03-06
Well, I managed to get it to read the cd with 11.10 and reinstall it - I even managed to upgrade to 12.04 again. I don't have any problems now. But I'm rather curious what would happen if I upgrade to 12.10 again? Any suggestions? If you need any kind of info I'll happily post it, so we can work this out, if anyone has any ideas.

---

### Post by Roquentina on 2013-03-06
I'm trying to install a different DE, just wondering whether it would speed things up a bit, because something seems to be wrong - everything is very slow? Is Unity too hard on a 256MB graphic card, or what?

---

### Post by ibjsb4 on 2013-03-06
If your still on 12o4 you can try Unity2D and see if its faster or you can install the gnome-classic desktop and try it.  You can choose at boot (login).

gnome classic desktop
```
sudo apt-get install gnome-session-fallback
```

---

