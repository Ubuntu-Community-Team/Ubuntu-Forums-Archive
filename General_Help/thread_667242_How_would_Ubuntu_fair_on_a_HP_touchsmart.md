---
title: "How would Ubuntu fair on a HP touchsmart?"
date: 2008-01-14
forum: General Help
---

### Post by Sick_of_present_tech on 2008-01-14
I ask this question because I love The latest version of Ubuntu with its integrated graphics and various plug ins, However, since I am a complete futurist, I hate being restrained to having to sit down with a mouse and keyboard and not having direct interactivity with the screen itself. I am kind of in love with HP's touch smart PC but it comes with Windows Vista preinstalled. I am wondering what degree, if any, compatibility would the latest version of Ubuntu have with this computer and its touch screen features? Also, in the event that it didn't work with touch screen, if I bought the computer and installed Ubuntu alongside Vista in a partition set up, would it work with the keyboard and mouse? I hope these questions aren't too lame, but I really do ponder the degree of compatibility of the latest version of Ubunu with the most advanced hardware, I'm just trying to support advances in both hardware and software, and I am into the concept of actually standing up at my computer some of the time and using a touch screen, as sitting down becomes somewhat cramped. Here's a link to a video of this computer in working form. 
[http://www.youtube.com/watch?v=e1_CcXLnjxE&feature=related](http://www.youtube.com/watch?v=e1_CcXLnjxE&feature=related)

---

### Post by Nexusx6 on 2008-01-14
[http://www.linux-on-laptops.com/hp.html](http://www.linux-on-laptops.com/hp.html)

The site contains personal accounts of people who've gotten Linux in one flavor or another to work on a laptop. If what you're looking at isn't listed, it doesn't necessarily mean it won't work, it could also be that someone has posted their success.

**EDIT:**
Wow.. sorry man. I don't know why but for some reason I automatically assumed it was a laptop you were talking about, and only saw the link in your post after the fact. 
Anyway, yeah I couldn't even guess how well that'd work out, damn nifty system though.

---

### Post by Sick_of_present_tech on 2008-01-14
Is there a list of computer manufacturers whos hardware Ubuntu wouldn't run on? Also, is there a list of compatible touch monitor manufacturers? It may have been a dream, but I could have sworn I recently saw a video of someone demonstrating ubuntu on a touch screen monitor. There has to be some native compatibility with the system and touch screens.

---

### Post by Sick_of_present_tech on 2008-01-15
Hello again!

---

### Post by geirha on 2008-01-15
Get a hold of the latest ubuntu CD, boot it up and see what works and what doesn't. If it is successful, you should be looking at a ubuntu desktop running from the CD. (double-clicking the install icon on the desktop will start the installation, so don't do that. Not yet at least ;) you just want to see if things are working for now) 

Run some commands and see what hardware it has 
```
sudo lspci -v
sudo lshw
```
Identify the touchscreen in the lspci output, and google it. See if maybe the evtouch driver has support for it. There are also some drivers in the ubuntu repository. Try installing those (then restart the xserver by hitting Ctrl+Alt+backspace). You'll find a list of input-drivers with ```
aptitude search xserver-xorg-input
``` then install with ```
sudo aptitude install xserver-xorg-input-*something*
```

Anything you install while running from the ubuntu CD will only be stored in RAM. When you reboot, all changes you have done will be lost (so nothing will happen with the windows vista allready installed, unless you mount the harddrive partitions and start deleting stuff, of course)

---

### Post by Nexusx6 on 2008-01-15
> **Sick_of_present_tech said:**
> Is there a list of computer manufacturers whos hardware Ubuntu wouldn't run on? Also, is there a list of compatible touch monitor manufacturers? It may have been a dream, but I could have sworn I recently saw a video of someone demonstrating ubuntu on a touch screen monitor. There has to be some native compatibility with the system and touch screens.

Its all about the drivers. Manufactures like HP build there systems from a grab bag of parts made by other companies, and it can sometimes be a toss up of whether that part just happens to have been reverse engineered or had a driver written for it by the community or the company itself. So really, it's got nothing to do with the hardware most of the time, a touch screen system from HP might work in Linux, while a touch screen from Sony might not if they bought the screen and drivers from different companies.

So to answer your question, there is a list of hardware that Ubuntu wont run on because of drivers, yes. But there is no blacklist of an entire manufacture I believe. Least, not one I've ever seen.

---

