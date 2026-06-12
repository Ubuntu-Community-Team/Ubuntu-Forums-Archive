---
title: "problems installing Nvidia drivers Kubuntu 13.10"
date: 2014-04-08
forum: General Help
---

### Post by silver nekode on 2014-04-08
Hey guys, so I just built a new computer and tried to do a fresh install of Kubuntu 13.10 from live DVD. Upon booting to the dvd I ended up getting a black screen with a blinking cursor. By searching around I found a solution of booting with NOMODESET and was able to complete the install. 

The info I found pointed to this being an issue with the noveau drivers for my EVGA 750ti and I made the foolish mistake of thinking I was familiar enough with console to handle the install myself. :p After following several different guides I think I've made the problem worse. I think I have installed two sets of nvidia drivers, 304 and 334, neither of which is working.
 Under the additional drivers window it only shows nvidia_334 and says the driver is activated but not in use. Further, if I go to KInfoCenter and check the OpenGL tab, it says could not initialize OpenGL. At this point I'm afraid to keep messing with it for fear I'll just make things worse. Could you guys offer any guidance or should I just wipe and do a fresh install? Any input would be greatly appreciated.

Specs:
MSI H87-G43 Mobo
Intel Core I5
EVGA 750 ti superclocked

If you need any more info on comp please just ask. Thanks in advance.

---

### Post by hardkhora on 2014-04-08
Wow, you have almost a thousand views and no one has responded. Reading through your problem I can see a solution within my abilities, but I would recommend a > [COLOR=#000000]wipe and do a fresh install[/COLOR] And see if you can get it working with the GUI install, if so, then go back and see what you need to do to handle it all yourself through the console...if I mistook the idea that you only used the console for the driver install and not the OS, sorry.

---

### Post by silver nekode on 2014-04-08
I did a GUI install, console was only for trying to get the video drivers installed. However, I gave up messing with it and went through and installed a couple apps and restricted codecs which required a reboot, and the nvidia drivers started working. I have no idea why, I restarted several times while messing with them and it never worked but It appears that the drivers kicked in. I can't be sure though because now the font size for everything is so small that if I push my nose up against the screen I can almost read it. I think this is Linux's way of telling me to go RTFM :p I have to get some sleep for work now, but when I get back tomorrow I'll get the font size figured out and post whether I actually have things fixed or not. Thanks for your time hardkhora and everyone who read my post.

---

### Post by hardkhora on 2014-04-08
Glad you got it figured out, It sounds like there was a problem with a codec and you video card? Although, that is strange, since unless you were trying to watch videos I don't see why it was a problem at boot.

---

### Post by silver nekode on 2014-04-09
Sorry, I guess my initial post did a poor job of explaining what was happening. According to what I've read, the initial boot issue is a known problem with some nvidia cards (something to do with certain video processing tasks being moved to kernel to allow for fancy graphics during boot, I don't remember the specifics), booting with the option NOMODESET bypasses this issue by turning the process back over to standard VGA, which fixes the problem until you can install drivers. I got that figured out and had the boot problem taken care of, just couldn't get the drivers installed which I'm pretty sure was a completely seperate problem. I only included the info about the boot problems in case I was wrong and the two were linked.

As for the rest, I am now sure that the nvidia drivers are running (still have no idea why they started/why they didn't work earlier) because the text size is a common issue with the proprietary nvidia drivers and has an easy fix. 
So, after all that, I'm gonna call it problem solved. I'm posting from a phone now, but when I get to a computer I'll post a link to the instructions I found on these issues just in case someone with the same problem(s) finds this thread. Thanks.

---

### Post by silver nekode on 2014-04-09
Now that I'm back at my computer here are the links that I used to figure these out:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)
The top answer explaining how to boot with NOMODESET fixed the black screen with blinking cursor while I was booting from live DVD for the install.

[http://ubuntuforums.org/showthread.php?t=2150662](http://ubuntuforums.org/showthread.php?t=2150662)
I used this method to fix the text being too small after nvidia drivers installed adding option "DPI" "100 x 100" to the monitor section. I found this same advice in a few places some listing it as options and some as option, it worked for me without the s.

I won't post the threads I used for the driver install because it went horribly wrong and I don't know what all happened there.

---

### Post by oldrocker99 on 2014-04-09
I had some similar problems with the 331 and the 334 drivers I downloaded from nVidia, and finally wiped the drive, reinstalled, and installed the 331 drivers from the Ubuntu repos, and all is well.

---

### Post by hardkhora on 2014-04-09
[COLOR=#DD4814][COLOR=#000000][silver nekode]("http://ubuntuforums.org/member.php?u=1733197"), thank you for the links and follow-up. Hopefully it helps someone with a similar problem.[/COLOR][/COLOR]

---

