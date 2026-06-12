---
title: "can't see window titlebar on inactive windows"
date: 2008-04-25
forum: General Help
---

### Post by natirips on 2008-04-25
I just installed Ubuntu 8.04 (upgraded from 7.10 using alternate CD) and now I can't see titlebars on my inactive windows. :( I'm using "Human" intefrace looks (desktop environment is Gnome), and have both Widged Layer and Window Decoration options switched on in Compiz.

Any help appriciated.

---

### Post by paulisdead on 2008-04-25
I've got the same problem when I upgraded from 7.10 to 8.04, both 64bit.  

I've tried changing my titlebar theme, so it's not that.

If you figure out first I'd love to hear how you fixed it.

Another oddity is when I have xine running, and have the controls showing, the controls window keeps stealing window focus every few seconds, and causes parts of text to randomly highlight in the gnome-terminal.

---

### Post by Fuse314 on 2008-04-26
I have the same behavior.

The inactive titlebar is not drawn, sometimes there are artifacts in the area of the inactive titlebar.

Updated from 7.10 to 8.04.
Dell M1330, nVidia GeForce 8400M GS

Also after the Upgrade I had the cubecaps/skydome settings reset after the upgrade (the configuration manager showed my correct config, but the cube/skydome showed different (default?) settings).
I solved this by resetting the profile (push "settings" after opening the compizconfig-settings-manager to bring up the CCSM Settings, under "Profile & Backend" push the "reset" button.)
This solved the wrong displayed settings for me, but the issue with the inactive titlebar still remains the same.

---

### Post by Zorael on 2008-04-26
Does this happen with the Emerald window decorator, too? (package name **emerald** if you don't have it installed)

Compiz's KDE decorator (kde-window-decorator) has similar bugs with artifacts and missing titlebars on some windows, but Emerald seems more stable. If it works, there should be Emerald themes that look like the standard Metacity "Human" theme you're likely using now, if you want to keep the looks.

---

### Post by supersuckers on 2008-04-26
I just upgraded from gutsy to hardy as well.  I am runing amd64 with an nvidia geforce 8300 gs.  I'm using the restricted nvidia drivers.  Same issue, inactive windows lose their window decorations.  What's interesting is that another user on this computer does NOT have the same issue, so I think it is something in my settings that have carried over.  What's weird is I've exported her settings from compizconfig settings manager and imported them on my profile, but it did not fix the issue.  I'd like to somehow get my profile 'fixed' but can't figure out how to do it. Choosing reset to defaults in compiz config settings manager did not fix it either.

edit: wanted to add, I do not have emerald installed.

---

### Post by Zorael on 2008-04-26
You can delete the .compiz directory in your home dir if you want to make sure you've gotten rid of the settings.

As for Emerald, in my experience it's worked better than (gtk/kde)-window-decorator, so I'd suggest you at least try it and see if it works better (if the delete-settings strategy fails, naturally).

---

### Post by natirips on 2008-04-26
I noticed that the window borders and close/minimize/maximize buttons and everythis else is still there, they just aren't drawn for some reason, but I cand use the invisible buttons...
However, I'd still like to fix this somehow...

---

### Post by Fuse314 on 2008-04-26
It does display correctly with emerald, but I did not manage to install it correctly.
I changed the windows decoration command to /usr/bin/emerald and restarted - no change.
When I start "emerald --replace" in the console it displays emerald but I have to leave the console open to keep emerald running.
After a reboot, the compitz decoration plugin is back in action with the disabled window issue...

I will try to delete the .compiz directory from my home directory and report if anything changes.

Update: I just deleted the .compiz directory (/home/user/.compiz) and did a restart.
Interestingly it didn't even reset my settings, the active plugins, skydome settings etc are still in place...  It seems as if the .compiz directory does not hold the users settings.
(plus the titlebar issue is still there)

---

### Post by supersuckers on 2008-04-26
Deleting .compiz,  and .config/compiz did not fix it for me.  I see the settings in the Default.ini when I have it set to use a flat file.  I really can't wrap my head around why I'm having this issue when the other user of this machine isn't.

---

### Post by natirips on 2008-04-26
One stupid question... here I go: what is emerald? Is it:
1) a compiz plugin
2) a compiz-independant plugin which can be used by compiz
3) an application which can be run parallel with compiz
4) something compiz-alike
5) something that raplaces compiz
6) something else?

---

### Post by Urik on 2008-04-26
The same problem with titlebars of inactive windows, after 7.10 -> 8.04.


 If I'm turning off the "window decoration" option (but compiz is still running) - the titlebars just dissapear from all the windows.

Video card: Nvidia 8500GT, last nVidia driver version.

---

### Post by Fuse314 on 2008-04-26
I just did a quick reinstall of the system, it works perfectly with the installation from CD, using the same nVidia driver and compiz version.
So it is definitely a configuration issue.

I will roll-back the system to the previous state.
Maybe someone can point out all the locations where compiz stores the settings (system-wide and per-user). I hope that we will be able to find the cause in these files.

---

### Post by natirips on 2008-04-27
I installed emerald, and put the following in the decorator command (in compiz's window decorator settings): "/usr/bin/emerald --replace" (without the quotes), then logged out and in a few times, and it works (for now at least, I will report back here should it stop working - if I don't report back, it most likely means it works).

---

### Post by Zorael on 2008-04-27
Compiz is a window compositioner and basically enables GL effects in your desktop, which your enabled Compiz plugins use to display effects. It also manages basic window management; keeping track of which window has focus (so keypresses are sent to the correct one), etc.

Emerald, gtk-window-decorator and kde-window-decorator are window decorators that draw borders and titlebars to windows. Compiz needs to have the Window Decoration plugin enabled to start one automatically, else you can just run 'emerald --replace', 'gtk-window-decorator --replace' etc in a run box (Alt+F2).

Emerald seems to be more stable than both the other two, so I'd recommend you migrate to it and find a theme you like over at gnome-look.org, kde-look.org or beryl-themes.org. There are clones of the standard Ubuntu themes over there, too.

As for Compiz settings, opening up ccsm, going to preferences and resetting your profile should clear everything out. Else, your per-user settings *should* be in ~/.compiz. I'm not sure there are any global settings? I'm likely wrong. On a windows box now, too, so can't search.

As for Emerald/Compiz/gedit/Synaptic/anything wrenching terminal control from you, this is normal for processes that don't run in the background. You can "circumvent" this by adding an ampersand (&) after the command, but there's a catch; you must close the terminal window by entering **exit** and not by clicking the X button.

---

### Post by akshar_patel_47 on 2008-04-27
Just go to appeareances-> visual effects. First select None in that and then select extra.
This will bring back your title bars. Then you can configure compiz in any way you want.

---

### Post by paulisdead on 2008-04-27
> **akshar_patel_47 said:**
> Just go to appeareances-> visual effects. First select None in that and then select extra.
This will bring back your title bars. Then you can configure compiz in any way you want.

Tried that, using the GUI option to reset the desktop effects setting.  None of that worked.

---

### Post by natirips on 2008-04-27
> **paulisdead said:**
> Tried that, using the GUI option to reset the desktop effects setting.  None of that worked.

Did you try with emerald (see my post a little above for usage)?

---

### Post by fuag155555 on 2008-05-01
I have the same problem amd-64, nvidia 8600 gts, nvidia-glx-new, also upgrade from 7.10 - 8.04, i cannot reinstall, this is my main machine, has all my school work and a ton of other programs on it i don't have the cd's for right now.

---

### Post by vaxen on 2008-05-14
exactly the same problem. I have this problem on 7.10 and on 8.04. no window border on inactive windows, or really messed up rendering. I'm pretty sure gtk-window-decorator will work, but that defeats the purpose because I'm using KDE and I wanna use kde-window-decorator. And also window shadow in window decorator module does not work in 8.04. All I can think of is there is issues with the driver and also kde-window-decorator. Everything runs fine on my desktop with nvidia and kde.

Dell XPS M1330 8400M GS

---

### Post by grdrahusz on 2008-06-06
I Googled the Internet yesterday and found a set of directions at Pendrivelinux.com that worked for my Dell 8200 with a 64 MB nVidia video card.  

**[http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/](http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/)**

Although my PC is 6+ years old, it is running Ubuntu 8.04 with some decent eye candy.  When I installed Vista it almost chocked and died, even with everything turned off.

---

### Post by LtPitt on 2009-01-06
Emerald works fine instead of gtk graphical glitches...

The only problem I have with it is that when I open a new window it get displayed in the upper left corner of the screen and the title bar is "hidden" under the ubuntu menu panel.

Frustrating :(

---

### Post by natirips on 2009-01-06
> **LtPitt said:**
> Emerald works fine instead of gtk graphical glitches...

The only problem I have with it is that when I open a new window it get displayed in the upper left corner of the screen and the title bar is "hidden" under the ubuntu menu panel.

Frustrating :(
It could possibly be an issue with your menu panel. If you shortened it (i.e. so it's not as wide as the screen), this is normal.

Other problem could be you window placement method.

P.S.: If you need to get the window out of the corner, but cannot access it's titlebar, try holding down ALT and dragging the window with your left mouse button.

---

### Post by Forlong on 2009-01-06
Go the **Place Windows** plugin in ccsm and set **Placement Mode** to **Smart** or **Centered**.

---

### Post by LtPitt on 2009-01-07
Yay! :D

Problem solved using windows placement!

Thanks =D

ps
Forlong, since you look experto on compiz would you mind to read this:
[http://ubuntuforums.org/showthread.php?p=6413487#post6413487](http://ubuntuforums.org/showthread.php?p=6413487#post6413487)

I've read your site instruction and you say to put horizontal and vertical desktop size to 1 and then to 4 virtual desktop but my virtual desktop value is "stuck" to 1 :/

Thanks =)

---

### Post by bookemdanno4 on 2009-01-09
Hi All,

I'm having a similar problem on Ubuntu 8.04! The top & bottom panels have disappeared off the desktop after changing some settings in Compiz. I can't access any applications menus and have to use the 'search' function to find applications instead!

If I can get back to the Compiz settings what do I need to do to get them back?

I spotted someone mention 'rollback' on a previous posting - where is this function? Is it something I need to download as a separate module/application or is it an integral pat of Ubuntu?

Cheers for any feedback.
____________
bookemdanno4

---

### Post by Forlong on 2009-01-09
If you're on GNOME you can reset all Compiz settings with this command in the terminal:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by bookemdanno4 on 2009-01-09
Many thanks

---

### Post by dgtester on 2009-05-21
I fixed the problem of inactive titlebar buttons disappearing as follows:

Go to Emerald-Themer, then Edit-Themes, and then click the Buttons tab. Uncheck "Use Button Halo/Glow for Inactive Windows". Inactive titlebar buttons should appear as expected now. (Or at least, they do on my machine.)

I don't know why it works, but I guess there's a bug in the button glow code somewhere.

---

