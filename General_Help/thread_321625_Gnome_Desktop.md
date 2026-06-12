---
title: "Gnome Desktop"
date: 2006-12-19
forum: General Help
---

### Post by kadkad19 on 2006-12-19
hey ,
i would like to add Gagates to my Gnome Desktop.
when using kde there is some programs like ObjectDock and apple wagagates ... or vista panel ... you know ..
something like aiglx but with no desktop 3d and XGL ... something more simple .
there is something that can work in Gnome too ? 
with ubuntu 6.10 ?

tnx .

---

### Post by xyz on 2006-12-19
Hi,
1. How about  [gDesklets]("http://www.gdesklets.org/")
Simple enough...
> Architecture for desktop applets
gDesklets is an architecture for "desklets", which are tiny applets
sitting on your desktop in a symbiotic relationship of eye candy and
usefulness.

You can populate your desktop with status meters, icon bars,
weather sensors, news tickers... whatever you can imagine...
Virtually anything is possible and may even be available some day.


> Applets for gdesklets
gDesklets is an architecture for "desklets", which are tiny desktop applets.

This package provides desklets for the gDesklets application.

This package contains theses desklets :

 * ACPI 0.1              * Battery 0.3           * Bible-desklet 2.0.1
 * BinaryClock 1.2       * Borders               * Boxmail 0.50
 * BSRDG 0.1             * Bubblefishymon 0.1.1  * Bugzilla
 * Calendar 0.21         * CircleButtonBar 0.3   * Clock 0.50
 * Another clock         * CornerXMMS 0.0.5      * Cpuinfo
 * Debian cow            * Deskquotes 1.2        * Desktao 0.3
 * DinoCam 1.0           * DiskIo 0.1            * DiskMount 0.3.2
 * Displayconstraints0.1 * Ebay 0.1.1            * Ebichuclock 0.1.1
 * Ephemeride 1          * ExternIP 0.3.0        * Fortune
 * GnomeBar 2.0.2        * Goodtime 0.2          * Hddtemp 0.1
 * HottieOfTheHour 0.3.1 * I2CTemp 0.12          * IconButton 0.1.4
 * Image 0.1             * Imapmail 0.1          * Imonc 0.6
 * Info                  * Infobar 0.3           * InfodomesticsBar 1.0
 * Irc 1.2               * Juju Countdown2 0.1   * LinuxTag Edition 0.11
 * Lmsensors 0.8         * LT-hddtemp            * LTPager 0.1
 * LTPagerSb 0.1         * LTVSeti 0.2           * LTVariations 0.26
 * LTXmms 0.3            * Memo 0.1.4            * MemoOver 0.1.0
 * Memory 0.2.0          * Mldonkey 0.1.2        * Modified xmms
 * Multitail 0.3.1       * NetworkInfo           * Ping 1.0.0
 * Popmail 0.1.4         * Praytime 0.21         * Psi Battery 0.1
 * Psi Launcher 1.0      * Psi Pager             * Psi Seti 0.2
 * Psi Small 0.5.1       * Psi Small Notify 0.01 * Psi Tasklist
 * Psi Tiny              * Psi Weather           * Psi small
 * Rhythmlet 0.3g-r3     * Rss 0.1               * Rss-grab 0.6.4
 * Seti                  * SideCandy 0.1         * SC-Diskinfo 0.10.2
 * SC-HDDTemp 0.2        * SC-Mount 0.5          * SC-MPC 0.21
 * SC-Popmail 0.1.3      * SC-PrintQueue 0.9     * SC-RAM 0.3.1
 * SC-Sytadin 0.50       * SC-Users 1.4          * ShadowImage 0.2
 * StarterBar 0.31.3     * Stockinfo 0.2         * StickyNotes 0.15
 * SysInfo 0.25          * Sytadin 0.2           * Tasklist 0.10
 * Temperature 0.2       * Themes 0.1.1          * Todo 0.1.1
 * VariableBorder        * Volume                * Weather 0.26
 * WeeklyCalendar 0.31   * Wireless 0.2          * XMLQuotes 2.4
 * Xmms

2. [An Aquatic Desktop by poofyhairguy]("http://ubuntuforums.org/showthread.php?t=112333")
3. [Installation of E17 by TimmyJ]("http://www.ubuntuforums.org/showthread.php?t=97199&highlight=E17+cvs")

---

### Post by kadkad19 on 2006-12-19
oh ...
thnx . 
make it work this exactly what i need .
do you have any solution for Object Dock ? like Mac ? 
the SuperKarambe does not want to work ...

---

### Post by Ozzee on 2006-12-21
I use a large gnome panel as an object dock. You just open the panel properties and set the orientation, the size, untick expand tick autohide and untick show hide buttons. Then if you want the always visible part to be smaller (mine is only 1px) you open gconf-editor from the terminal:
```

gconf-editor

```
go to /apps/panel/toplevels/(the panel you want to edit)
you can find out which of the panels you want to edit by looking at the orientation value, if you want to edit the panel at the bottom you choose the one with the orientation value "bottom"
Now you need to edit the auto_hide_size value, I have it at 1 but you can have it more visible if you want, as far as I know it can't be set to 0.

Here's a screenshot of what mine looks like:
[http://img224.imageshack.us/my.php?image=screenshotkp1.png](http://img224.imageshack.us/my.php?image=screenshotkp1.png)

---

### Post by budhe888 on 2007-01-15
I like your idea here.  Can you tell me how you make the window list in the panel have only large icons and no text?

Thanks!

---

### Post by Ozzee on 2007-01-15
> **budhe888 said:**
> I like your idea here.  Can you tell me how you make the window list in the panel have only large icons and no text?

Thanks!

If you mean the panel at the bottom you just right click it, choose properties and adjust the size value to what you like. If you mean the bar where the names of the applications you have open are displayed, I don't know how to do that, sorry.

Oh yeah and you add launchers to the panel by choosing programs from the menu, right clicking them and choosing "Add this launcher to panel", then move the launcher by dragging it to the bottom panel.

:)

---

