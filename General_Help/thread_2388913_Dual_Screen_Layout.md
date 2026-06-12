---
title: "Dual Screen Layout"
date: 2018-04-09
forum: General Help
---

### Post by electrosteam on 2018-04-09
Dell laptop (2003), Lubuntu 17.10 (.1), LXDE and external monitor.

Installed arandr and now have dual displays working - really chuffed.
My interest is in optimising the layout, if I can.

arandr shows the left hand VGA-1 external monitor as 'Active' and the right hand LVDS-1 as 'Active, Primary'.

But: the taskbar is on the VGA, and all the icons are on both displays.
And, some icons open on a set display, regardless of which display is used to launch it.

Is it possible:
 - move the taskbar to the right hand (laptop) display,
 - remove all the icons from the left hand (VGA) display, so that only the right hand (laptop) display shows icons,
 - launch all applications on the right hand (laptop) display.

The aim is to operate the laptop as it does when operated alone, without the VGA, with the VGA used only to move selected windows to when desired.

John

---

### Post by electrosteam on 2018-04-11
This is just a bump to see if anyone has an interest in this subject.

I posted a virtually enquiry last year and got some great suggestions on how to investigate video drivers etc, but nothing on arranging the screens.
No responses yet on this thread, so must conclude there is little interest.

Note that, although the icons are identical on both displays, they are arranged differently, and the taskbar is only on one display.
So, the kernel uses different interpretations of what to do with the contents of /home/john/Desktop, which shows most of the icons.

No sweat, the system is working well, happy to wait and see what 18.04 LTS brings,
John

---

### Post by kerry_s on 2018-04-11
sounds like the default setup for dual screen which is to stretch/span both screens.

doesn't lxde have display settings manager where you can set a primary display? ie: the laptop

---

### Post by electrosteam on 2018-04-11
Kerry,
LXDE itself doesn't seem to have anything to manage two screens, but I installed ARandR which does.
ARandR allows setting LVDS-1 ( laptop ) as active and primary, and the VGA as active.  Re-booting sets VGA as active and primary, LVDS-1 as active only.
John

---

### Post by kerry_s on 2018-04-11
> LXDE itself doesn't seem to have anything to manage two screens, but I installed ARandR which does.

[https://wiki.lxde.org/en/LXRandR](https://wiki.lxde.org/en/LXRandR)

so not in the menus?
how about -> lxrandr <-from terminal

---

### Post by electrosteam on 2018-04-12
Kerry,
LXRandR is included in the standard LXDE menus, it allows some combinations of where the displays are positioned, but not with the VGA on the LHS, options are:
 - same screen both displays,
 - turn off LCD, external only,
 - turn off external, LCD only,
 - external to right of LCD,
 - external above LCD.
Launching from the terminal is the same.

I have the VGA on LHS, which works fine, but with duplicated icons, and with the taskbar only on the VGA.

The ideal, to me, would be to have the LCD identical, one display or two.
When the VGA was connected, just a blank display onto which I could drag windows as desired.
Probably utopia, but one can dream.

John

---

### Post by kerry_s on 2018-04-12
is it only words or are there thumb nails of the monitors?

in all the distro's i've used, what you do is grab the image with the mouse & drag it where you want it positioned.
in your case to the left

---

### Post by electrosteam on 2018-04-13
Kerry,
Tried dragging, tried all the likely avenues with LXDE, nothing will change the icon population on the two displays.
Moving an icon to trash on one display, removes it from both displays.
Moving icons around on either display is normal.
The first level dip into the terminal was rewarding, much more comfortable with that aspect now.

The system is perfectly usable as is.

Don't sweat this one, happy to get 18.04 LTS running, then have a real go.
On reflection, the thread title should have included 'icon', sorry about that.
John.

---

### Post by kerry_s on 2018-04-13
i meant the display thumbnail, you want it on the left right.
[ATTACH=CONFIG]279267[/ATTACH][ATTACH=CONFIG]279268[/ATTACH][ATTACH=CONFIG]279269[/ATTACH]

---

### Post by electrosteam on 2018-04-13
Kerry,
My system tool that provides the equivalent drag facility for arranging the displays is ARandR.
Tried all the combinations, all have two sets of icons.

With VGA above or below the LVDS-1, or with VGA on RHS, I can change the primary allocation and the system accepts it (ie taskbar on LVDS-1).

With VGA on LHS, no amount of fiddling puts the taskbar on the LVDS-1.

Although I prefer the VGA on the LHS, I could accept the VGA on the RHS, it just means a re-arrangement of the workstation area.

As an aside, I use the mouse on the LHS, and have done so for many years (a standard right-handed mouse).
Hence the convenience of the VGA on LHS.

Also, on one of the up/down display combinations tried, the task bar did not show the forum, or this thread, as running - that is a bit of a worry.

John

---

### Post by weihong-85 on 2019-01-15
Hi,

  I have Lubuntu 18.04 32 bit running on my laptop and I have a similar set up as you.

  My TV is on the left of my laptop, connected via HDMI.

  I managed to get similar to what you wanted to do by the following steps:

1. using Start -> Preferences -> Monitor Settings -> Advanced settings, I set the TV display to be on the left.
2. I right click on the Taskbar -> Panel Settings and changed Monitor from 1 to 2.  My primary display is my laptop screen, but somehow I still need to do this.
3. I had the Trash Icon on both screens.  I went to the TV screen and removed the trash icon by right clicking on the Trash icon -> Remove from Desktop.  
4. I then added the Trash icon on the laptop screen desktop. by right clicking on the laptop screen desktop -> Desktop Preferences -> Desktop Icon -> Show "Trash Can"...

  Hope this helps.

---

