---
title: "Some KDE Questions from a newbie in KDE"
date: 2006-10-15
forum: General Help
---

### Post by krypto_wizard on 2006-10-15
How to see the following in KDE

1. Volume Icon in system tray.
2. Network monitor in system tray
3. Battery Monitor for laptop in system tray.


Please help a new KDE newbie.

Thanks

---

### Post by MartinJ on 2006-10-15
3: In KMenu -> System Settings -> Laptops and Power -> Laptop Battery, tick the 'Show Batter Monitor' Option.  You may also need to push the 'Start Battery Monitor' button in the lower right of that window.

---

### Post by skymt on 2006-10-15
1. Hit Alt-F2 and enter "kmix".

Now, can someone help with #2? I don't have KDE installed right now.

---

### Post by ajgreeny on 2006-10-15
I would also like a network monitor in the system tray.  The nearest I have found so far is the network part of siperkaramba, but it isn't quite the same thing as I want, ie, it's not in the system tray but on the desktop.  Anyone know of something?

For the volume control suggestion given by skymt, it requires that the session manager is set to load the previous session.  If you set up your sessions to start an empty session like me, just add a launcher for *kmix -caption "%c" %i %m* to your ~/.kde/Autostart folder.  That will just give you the icon and not open the program on your desktop.

---

### Post by krypto_wizard on 2006-10-15
I have installed only kde-core and not complete kde.

And I don't see the Laptop options.

Is it because of this or othere is any other reason.

Please help me love KDE.

---

### Post by nalmeth on 2006-10-15
knemo for the network monitor

---

### Post by krypto_wizard on 2006-10-16
I installed ubuntu and then installed kde-core as told by aysiu.

I dont see any optin with KMnenu -> System Settings .

What should I do to see KMenu and System Settings ? I don't want to install the while kde since it brings lot of stuff which I dont use.

Please help me.

Thanks

> **MartinJ said:**
> 3: In KMenu -> System Settings -> Laptops and Power -> Laptop Battery, tick the 'Show Batter Monitor' Option.  You may also need to push the 'Start Battery Monitor' button in the lower right of that window.

---

### Post by aysiu on 2006-10-16
Press Alt-F2 and type ```
kcontrol
``` Control Center is what it's called--slightly different in format from System Settings, but it does the same thing.

---

### Post by krypto_wizard on 2006-10-17
Even under kcontrol I dont see the option for hardware and Laptop.

Is it because I didnt install kde completely and just installed kde-core ?

Please guide. I always tried KDE and because I couldd't do some stuff I gave up and went back to gnome. I don't want to install the complete KDE because it brings so much with itsef that its overwhelming.

Every help is appreciated. 

> **aysiu said:**
> Press Alt-F2 and type ```
kcontrol
``` Control Center is what it's called--slightly different in format from System Settings, but it does the same thing.

---

### Post by aysiu on 2006-10-17
I don't know what you mean by *hardware*. There's a peripherals section where your hardware should show up (mouse, keyboard, etc.). Display won't show up unless you install *kde-guidance*.

I don't know much about laptops, but there are two packages in Kubuntu that are not in *kde-core* but have the word *laptop* in them:

*klaptopdaemon* and *laptop-mode-tools*

You can see the full list of packages that are the difference between *kde-core* and *kubuntu-desktop* and try out a few suspects. You don't have to install them all.
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by Zeddicus on 2006-10-17
*Is it because I didnt install kde completely and just installed kde-core ?*

Yes.

Installing klaptopdaemon or kpowersave will get you a battery monitor.

There are, well... a lot of different network monitors.  knetworkmanager is my favorite.

---

### Post by krypto_wizard on 2006-10-17
Thats how my hardware sections looks like.

---

### Post by krypto_wizard on 2006-10-17
But is there anything equivalent of network-monitor of gnoem in KDE. I installed knetworkmanager but its more like showing wireless connections but not wired interfaces. 

> **Zeddicus said:**
> *Is it because I didnt install kde completely and just installed kde-core ?*

Yes.

Installing klaptopdaemon or kpowersave will get you a battery monitor.

There are, well... a lot of different network monitors.  knetworkmanager is my favorite.

---

### Post by Zeddicus on 2006-10-17
As someone already mentioned, knemo fits the bill.

From the look of your kcontrol setup, you may have klaptopdaemon installed -- go under the "Power Control" section.

---

### Post by aysiu on 2006-10-17
> **krypto_wizard said:**
> But is there anything equivalent of network-monitor of gnoem in KDE. I installed knetworkmanager but its more like showing wireless connections but not wired interfaces.
Try KNemo--it's in the Universe repositories.

---

### Post by krypto_wizard on 2006-10-17
Got the laptop battery after klaptopdaemon.

Thanks to both of you.

> **Zeddicus said:**
> As someone already mentioned, knemo fits the bill.

From the look of your kcontrol setup, you may have klaptopdaemon installed -- go under the "Power Control" section.

---

### Post by krypto_wizard on 2006-10-17
I have been bugging you guys with lot of questions. One more question on KDE.

How can I make my fonts in terminal to be like Suse. Right now they are longish vertically and I using font size 8 in all the areas. Even under gnome terminal fonts are not as smooth as they are in gnome.

What do you guys to make fonts smooth. I like to use VI editor and thats why I like to have konsole with nice viewable fonts.

Every help is appreciated.

---

### Post by ajgreeny on 2006-10-17
Open konsole and go to Settings > Font > Select and change to what you want.  Then go to Settings again and save as default.  All done!

---

### Post by krypto_wizard on 2006-10-17
I am using .fonts.conf file posted on ubuntuforums for smoothening my fonts and it kinda makes look differently. I have used KDe once on Suse and I kinda liked those fonts. I tried what you said but I guess I couldnt get to those settings as I found on Suse.

---

### Post by ajgreeny on 2006-10-18
Perhaps you do not have all the fonts I have on my machine, which I just copied over and installed from windows so that some of my older windows word processor files can be displayed as they were written rather thanuse alternative fonts.

The font I use in konsole is *dejavu sans mono*, and it looks great, rather like *arial.*

---

