---
title: "Lubuntu Custom ISO Live Session Autostart and other Config issues"
date: 2018-05-11
forum: General Help
---

### Post by maceaferrer on 2018-05-11
Hi, I've been customizing a Lubuntu 18.04 ISO, with Cubic in a command-only enviroment, for my girlfriend. I'm almost finished but with the following issues:


[LIST]
[*][minor issue] Installed and "properly" configured a custom icon set but some icons may or may not load every time I boot the live USB. One in particular is the battery icon in lxpanel.
[*][FIXED] [s]Can't make several programs to load after logging into the live session, specially Compton.[/s] Edited autostart file located inside /etc/xdg/openbox/ and added the commands needed
[*][Also a huge issue] Can't change the color of the mouse's cursor selection area in desktop. Already done in PCMANFM. It's refered as foreground in the .conf files of pcmanfm
[/LIST]

Things I tried so far:
[LIST]
[*][icons issue] modify the live session in one pc and copy configuration files to the  other pc I'm using to customize the iso file. Seems to work for some icons, but the lxpanel still suffers the issue with also some buttons not showing properly (ie, no borders around them).
[*][s][Autostart issues] Added .desktop files in every autostart folder I could find and modified every autostart file I coud find.[/s]
[*][Cursor selection area in desktop] Nothing, as I can't find the configuration file for it.
[LIST]
[*]config files modified:
[LIST]
[*]/usr/share/lubuntu/openbox/rc.xml (for themes and fonts specially)
[*]/usr/share/lxpanel/profile/Lubuntu/panel/panel (custom layout and colors)
[*][s]/etc/xdg/autostart/compton.desktop | I created this file with this content:[/s]
[/LIST]
[/LIST]
[/LIST]
[s][INDENT=5]```
[Desktop Entry]
Name=Compton
Comment=Composite Manager
Exec=compton --config /usr/share/compton/compton.conf
Terminal=false
```[/INDENT]
[/s]
[LIST=|INDENT=3]
[*]/etc/xdg/lxpanel/default/panel/panel (custom layout and colors)
[*][s]/etc/xdg/lxsession/Lubuntu/autostart | To which I added ```
 compton --config /usr/share/compton/compton.conf 
```
[*]/etc/xdg/lxsession/Lubuntu-Notebook/autostart | To which I added ```
 compton --config /usr/share/compton/compton.conf 
```[/s]
[*]/etc/xdg/pcman/default/pcmanf.conf
[*]/etc/xdg/pcman/lubuntu/pcmanf.conf
[*]/etc/xdg/pcman/lubuntu/desktop-items-0.conf
[*]/etc/xdg/xdg-Lubuntu/openbox/lxqt-rc.xml (themes and fonts)
[*]/etc/xdg/xdg-QLubuntu/openbox/lxqt-rc.xml (themes and fonts)
[/LIST]

Any help regarding this issues will be very welcomed. I've been with this project for the last ~50 hours (2 [SUP]1/2[/SUP] days for the time I'm writing this). I'm out of ideas about the possible locations of the config files I need to edit for everything. I will gladly provide any extra information regarding file contents, directories or whatever is asked if needed.

I'm trying to achieve a good-looking and aesthetic environment for her with the performance of a lightweight distro.
Yes, this is more of a show-off but also, the laptop I'm deploying this into runs with an AMD C-60 with 4GB of DDR3 (maybe, I haven't checked really) and it runs uncomfortably slow with Windows 7 and I want to give her something special with the laptop and I though a custom OS created for her taking in mind her needs would do perfect.
Thank you, to anyone who stops by and helps me.

---

