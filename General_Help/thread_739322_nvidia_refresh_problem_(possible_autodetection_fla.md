---
title: "nvidia refresh problem (possible autodetection flaw)"
date: 2008-03-29
forum: General Help
---

### Post by Patness on 2008-03-29
edit - Potentially reliable workaround found. However, it's very annoying. It goes away every time you have to reload X. You have to redo this every time you log on. Do them in the exact order. Don't miss a detail - you're working with buggy software, apparently, and it's important you keep track.

first, enter: ```
sudo nvidia-settings
``` and then change the refresh rates and resolutions back and forth until a) you've selected a metamode (under the advanced button) that specifically asks for 75HZ or whatever your desired refresh rate is and b) this forces the screen to update when you click "apply". 

Now that you have your desired refresh rate and resolution, go the Screens and Graphics menu within GNOME and look for other refresh rates besides the ones that are offered. I've found that every time I do this, there's an option for something in the 90-100Hz range for refresh, which lets my desktop resolution actually function at a smooth pace. Now, any application that asks for my desktop resolution (the one offered by Screens and Graphics), gets the new one instead.
===================

edit - Solutions I have also tried:
Changing monitors and resolutions from within the Screen and Graphics menu. However, it asks you to log off to see the changes take effect. When you go back in, the old settings are restored.


=================
Original post follows:
=================
 I just started linux gaming with [Savage 2]("http://savage2.s2games.com/main.php") Its display resolutions are crippled compared to Windows, and I don't know how they get the "Desktop Resolution", which it reports as running at 50-51Hz - in line with Screen and Graphics and Screen Resolution menus.

The Rig:
Intel Core 2 Duo 6320
2GB RAM (reclocked for latency)
Nvidia 8600GT (forgot who the vendor is - e-VGA maybe)
Acer AL1715 LCD
Audigy 2 Platinum

Problem One: Autodetection of my monitor fails. I choose Acer AL1715 in Screens and Graphics, and...

Problem Two: I cannot select refresh settings of 60 or 75Hz.

I have tried editing Xorg in a variety of different ways, specifying horizontal and vertical refresh rates, specifying new display modes in varying combinations of 1280x1024_75 or 1280x1024@75, creating subsections of Screen, and using nvidia-settings. I've enabled and disabled Hsync and Vsync. None actually change the refresh rate reported when you try to change resolution or refresh rate within GNOME. To its credit, a variety of different edits have gotten me to the point of getting 55Hz, but not more.

So, first - how do I monitor the actual refresh rate being used to determine whether or not this is a reporting error (it takes a while for my eyes to relax enough - I have trouble doing it bare)?

Second: How do I get using (and getting GNOME apps to report) a 75Hz refresh?

Interestingly enough, the screens change between the login GDM and the GNOME session, and my monitor auto-adjusts. I'm not sure if this is relevant or how to fix it, because I'm not sure if either are using the right refresh.

---

