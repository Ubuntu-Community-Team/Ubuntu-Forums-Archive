---
title: "[SOLVED] LiquidWeather/SuperKaramba locks up, what now?"
date: 2008-05-21
forum: General Help
---

### Post by HousieMousie2 on 2008-05-21
Hi all,

    I love LiquidWeather, so it is bugging me to no end that it works fine for a while then goes bonkers, I need some help on this one.

    Seems like after I have put an application window over the top of it and then remove it or go to an uncluttered desktop, the part of the app window that was atop LiquidWeather gets stuck there.  If I refresh the desktop the graphics for the other window go away and the LiquidWeather area turns a nice ugly shade of gray.  (It may very well be getting stuck long before this, but I just don't notice it.)[It gets stuck the first time I switch desktops too.]

    Once LW gets stuck, no amount of clicking on it with any button has any effect.

    If I then try to open SuperKaramba it will think about it for a while, then the taskbar (with hour glass) bit for SK and the bouncing blue ball will simply vanish, without opening the program.

    I have previously uninstalled and reinstalled both LW and SK with no luck.

    I am very new to Linux and don't know how to more effectively get rid of a program than to use Adept/Synaptic/Kpackage... I certainly don't know how to take a peek under the hood and see what is happening in there... I mean, aside from popping the side off of the box and watching the fans spin.

Anyone feel like walking me through this one?  I promise I will do my best to do as I am told, and I would happily RTFM if I could find one.  :lolflag:

Thank you for your time, help or no help!:)

HousieMousie2

---

### Post by HousieMousie2 on 2008-05-23
Bump

---

### Post by HousieMousie2 on 2008-09-15
I never figured out how to fix it, but since that was in Gutsy and I did a clean install of Hardy, and it now works...

I am going to mark this thread as Solved.

My apologies if you came to this thread for an answer to your own SuperKaramba/LiquidWeather issue.  I wish you the very best of luck... as you can see by the lack of replies, I did not have any.

---

### Post by tarahmarie on 2008-09-21
Did you actually get LiquidWeather and Superkaramba to work?  I'm using KDE 4.1.1 and Hardy 8.04; I get an error message when I try to add LiquidWeather from the desktop widget add menu that looks like this:

SuperKaramba cannot continue to run this theme.One or more of the required components of the Kross scripting architecture is not installed. Please consult this theme's documentation and install the necessary Kross components.

Does anyone know why this is happening?

---

### Post by HousieMousie2 on 2008-09-22
> **tarahmarie said:**
> Did you actually get LiquidWeather and Superkaramba to work?  I'm using KDE 4.1.1 and Hardy 8.04; I get an error message when I try to add LiquidWeather from the desktop widget add menu that looks like this:

SuperKaramba cannot continue to run this theme.One or more of the required components of the Kross scripting architecture is not installed. Please consult this theme's documentation and install the necessary Kross components.

Does anyone know why this is happening?

Sorry I can not help you, I am using KDE 3.5.9, works without issues.

I am planning to make a second install of Kubuntu for the express purpose of having the latest KDE.  My intention is to play around with Plasma, but I am sure I will try to set up LiquidWeather/SuperKaramba... when I do, if I find a solution I will add it to this thread, please do likewise.

Do you know if 'libkrosspython0' is installed by default with KDE4 flavors?  I believe that SuperKaramba/LiquidWeather uses Python scripts, in which case Kross would need the right plug-in.

That's all I could find at this time.

Best of luck!

---

### Post by tarahmarie on 2008-09-22
> **HousieMousie2 said:**
> Sorry I can not help you, I am using KDE 3.5.9, works without issues.

Do you know if 'libkrosspython0' is installed by default with KDE4 flavors?  I believe that SuperKaramba/LiquidWeather uses Python scripts, in which case Kross would need the right plug-in.



No, libkrosspython0 is NOT installed by default.  Also, I've gotten it working in the last few hours, by installing libkrosspython0 AND kdeplasma-addons.  It turns out that as soon as I installed the extra Plasmoids in development, that Liquid Weather started to work.  I don't know if there's a broken dependency in there or something, but at least it's working now.

Also, it required that I edit and repackage the skz file as found here (it's just deleting a couple of lines of code that keep throwing that pyqt error):

[http://www.kubuntuforums.net/forums/index.php?topic=3093549](http://www.kubuntuforums.net/forums/index.php?topic=3093549)

---

### Post by HousieMousie2 on 2008-09-22
Thank you, tarahmarie.  I am sure this will come in handy for me and others who want LW/SK, as we upgrade to the newest KDE versions.

Thanks again!

---

### Post by hemna on 2009-01-15
I just tried to get superkaramba to load up liquid weather in Intrepid and I'm getting the dreaded missing Kross components error.  I have installed libkrosspython0 as well as kdesdk, but it still doesn't work.

---

### Post by tarahmarie on 2009-01-15
> **hemna said:**
> I just tried to get superkaramba to load up liquid weather in Intrepid and I'm getting the dreaded missing Kross components error.  I have installed libkrosspython0 as well as kdesdk, but it still doesn't work.

Did you try installing kdeplasma-addons?

---

### Post by hemna on 2009-01-16
yah kdeplasma-addons is installed.  still no joy.

---

