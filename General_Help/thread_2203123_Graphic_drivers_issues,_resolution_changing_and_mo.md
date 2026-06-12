---
title: "Graphic drivers issues, resolution changing and more!"
date: 2014-02-01
forum: General Help
---

### Post by Jonathan_Boklund on 2014-02-01
Hello! Linux is completely new to me and I seem to be running into more trouble the more i try to fix it, I have several issues that may or not be connected, I'll try to keep the post coherent.

Last week I installed ubuntu 12.04 from a usb stick, the computer is an Acer aspire 5742G, the graphics card nvidia GT 540M. 

On the second day of using the computer it started to freeze incessantly, forcing me to reboot each time. This problem stopped when i deactivated the nvidia drivers that were listed as recommended in "additional drivers" I believe they were 319. I settled for using integrated graphics during the week. 

I was also inconvenienced in that i couldn't change the brightness of my screen, I solved that by using the method posted here:  [http://askubuntu.com/questions/128463/how-to-control-brightness](http://askubuntu.com/questions/128463/how-to-control-brightness)

After that I decided to try and get my nvidia card running, the drivers that were showing up in additional drivers was now 331_updates, it says these drivers are activated but not currently in use. 

Googling for a bit somehow led me to creating a file called xorg.conf, after doing that i restarted the computer and was greeted by the log in screen with a resolution of x640 something, which was quite annoying as I couldn't change it through the display options as the window wouldnt fit on my screen. I googled and tried a command containing xrandr but that didn't work. Somehow though I managed to change it back while fiddling with the brightness function keys.

When i hold down fn and press the left arrow key the screen gets darker, when it hits its minimum and I hit left once more the screen goes black for a moment and then returns to where I was. If i hit left again the screen will go black but this time the resolution goes down to ultra low again. This is solved by hitting fn+left arrow again... This didn't happen before i messed around with the xorg.conf file. 
The log in screen is now at normal resolution but when I log in it changes to x640 after hitting a black screen.

I believe I have deleted the xorg. file, but with my limited experience I can't really tell.
To sum up the issue:
- The fn brightness control changes my resolution sometimes, after I have logged I get a black screen and then the resolution gets messed up.
- What drivers should I be using for my graphics card?

I apologize if my post appears as the ramblings of a madman (might be turning into one with these problems), I tried to give a timeline as I have no idea what could have affected what. 

Thank you for reading the thread and for any help offered!
 /A confused novice

---

