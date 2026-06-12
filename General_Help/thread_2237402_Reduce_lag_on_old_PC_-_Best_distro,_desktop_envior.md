---
title: "Reduce lag on old PC - Best distro, desktop enviornment, etc..."
date: 2014-08-01
forum: General Help
---

### Post by quadrplax on 2014-08-01
I have my old computer set up as an HTPC - The Dell Dimension 4550 in my signature. Some basic specs: 2.4Ghz single-core CPU, 512MB of RAM, 80GB IDE hard drive, Nvidia GeForce4 MX 420, Ubuntu 12.04.4 LTS (wouldn't boot to a 14.04 LiveCD, never upgraded distro). I have a few purposes I would like to use this computer for:
[LIST]
[*]Forward wireless connection (MWN-USB150N) to wired connection for my Roku that has broken WiFi (Already have this working)
[*]Browse the web, using websites with flash such as Twitch and AddictingGames. (Extremely laggy)
[*]Play Minecraft (I got this working via Oracle Java but it was extremely slow. It took 20 seconds to load the options screen after hitting the button and crashed when trying to go into sub-menus and change their settings).
[/LIST]
I know this computer is capable of doing these things, as I did them before when I had Windows XP. Also notable, in order to use the S-Video out on Ubuntu I had to remove the graphics driver, so it uses the default driver which only offers up to 1024x768, no problem for me. I use xrandr to manually set the screen resolution to 640x480 since I have a CRT TV and otherwise the text is too hard to read. I would like to know any settings to change, desktop environments to switch to, or even another distro or (free) OS to use that would be less laggy, yet fit all my needs. I would also be OK with returning to XP, as long as there is a way to do the Ethernet forwarding and force a 640x480 resolution. Currently, all I have done to try to speed things up is remove all non-essential startup applications. Thanks for the help.

---

### Post by TheFu on 2014-08-01
Don't use Unity. Go for a lighter DE or a pure WM environment. [http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/](http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/)

---

### Post by papibe on 2014-08-01
Hi quadrplax.

A few thoughts:

Since you have every hardware component working, I'd stay with an Ubuntu derivative.

Both [Xubuntu]("http://xubuntu.org/"), and [Lubuntu]("http://lubuntu.net/") will reduce memory usage. You don't necessarily have to reinstall as you can install the respective desktops and make them the default (XFCE and LXDE).

You can even try a leaner desktop like Openbox, or extremely lean as  awesome or xmonad.

Also, adding, for instance, 512Gb would also gets you better performance as you would reduce swapping.

Does the motherboard has SATA ports? you would gain some performance if you use SATA drives instead of IDE.

Regards.

---

### Post by MoebusNet on 2014-08-02
I think the issue that is going to cause you the most trouble is that your video card is no longer supported by NVidia. My old Dell D800 notebook had the NVidia Geforce Go 4200 32Mb video card that used the old 96-series driver. I eventually broke down & spent $30 for an NVidia Geforce Go 5200M 64Mb video card from EBay that is currently supported. Now I run Lubuntu 14.04.1; before that I was stuck with 11.10 until NVidia decided to support the old 96-series driver in 12.04. The 96-series driver doesn't work with anything after 12.04 because it needs an older xorg version. Nouveau open-source video driver works much better with my new video card than it ever did with the old one, too.

---

### Post by quadrplax on 2014-08-04
Ok guys, thanks for the help but things have changed a lot with my setup, and this is no longer what I want to do. I decided it would be best to start a new thread: [http://ubuntuforums.org/showthread.php?t=2237930](http://ubuntuforums.org/showthread.php?t=2237930)

---

