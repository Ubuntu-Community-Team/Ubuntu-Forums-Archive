---
title: "Compiz-Fusion vs Hardy: Emerald Themer now does nothing after upgrade! How to fix??"
date: 2008-05-04
forum: General Help
---

### Post by OzzyFrank on 2008-05-04
Yet another woe after upgrading to Hardy: I can't apply any Emerald themes to my windows/desktop effects. It took some mucking around with my nVidia 8600 drivers (which Hardy totally mangled... I rebooted into 640x480!) just to get Compiz-Fusion happening again. CF now works, albeit with some slightly anomalous behaviour (title bars/borders only show on active window, and even then sometimes only after clicking on it and really bringing it into focus). However, while Emerald Themer loads fine, and I can import new themes into it, I cannot change themes from within it. I just have windows using my metacity/gtk+ themes but with desktop effects, like the wobbly windows. Any ideas on how to fix this situation?? Cheers

---

### Post by spudratic on 2008-05-04
mine started to work after a reboot or I installed the compiz fusion icon and that got it working.You know I updated ounce and installed it twice and can't really remember what I did to get it going but i,m pretty sure it was the compiz icon.After you install it start it so it's in the top panel and right click and open emerald from there and you can also turn off compiz with this icon.

---

### Post by OzzyFrank on 2008-05-04
Hmmm... well the Compiz icon makes things worse, actually. I deselected the option to use the Metacity theme and got this:

**[COLOR="DarkRed"]An error occurred while loading or saving configuration information for gnome-compiz-preferences. Some of your configuration settings may not work properly.[/COLOR]**
(and from the Details button):
**[COLOR="#8b0000"]Type mismatch: Expected list, got string[/COLOR]**

The Emerald themes are working, however the other effects like wobbly windows aren't. What makes this worse is that everything has now crawled to almost a halt, like bringing a window to the front via taskbar buttons takes a few seconds... dragging windows around is a slow and laborious exercise, and is very jerky... text is about 5 characters behind, if I type somewhat slowly... menus take between 3-10 seconds to show... some context menus won't even show at all... and this still persists even after shutting down the Compiz icon and rebooting. I think this qualifies for "what a bloody mess!" hehe.

In case it makes a difference, my video drivers were installed by EnvyNG, after upgrading to Hardy and getting no better than 640x480 and 800x600 as my reward, hehe. Compiz wouldn't initiate before this, but things still are a long way off from the flawless video and desktop effects I had before the upgrade! Now it looks like I will have to start the Compiz icons again and choose Metacity, as this lagging in everything I am doing is really starting to drive me nuts!

---

### Post by OzzyFrank on 2008-05-04
OK, changing it back to Metacity didn't resolve all that lagging, jerkiness, and lack of response, even after a reboot. What finally did work was going into **Appearance** and turning off desktop effects, then turning them on again. Then with **GL Desktop** (or the Preferences from **compiz-tray-icon** - which still results in that error message box) I deselected **Use Metacity Theme** and I now have Emerald themes again with the desktop effects and now slowed-down system.

Hope this helps someone else experiencing this. Cheers

---

### Post by OzzyFrank on 2008-05-04
PS: With **compiz-tray-icon**, should I be getting more than a couple of options in its context-menu, being Enable GL Desktop and Preferences? I thought I could remember it being more like the one for Beryl, being it had all sorts of sub-menus, like Window Manager where you could select Metacity or Emerald etc. Am I missing something, or am I purely thinking of the Beryl taskbar button/tray icon?

---

### Post by OzzyFrank on 2008-05-05
Spoke too soon. I didn't actually check that I could change themes in Emerald, which it seems I can't. It's just using the last one I had active. Any ideas what to do now anybody? Cheers

---

### Post by czechman86 on 2008-05-05
> **OzzyFrank said:**
> Spoke too soon. I didn't actually check that I could change themes in Emerald, which it seems I can't. It's just using the last one I had active. Any ideas what to do now anybody? Cheers

i had this problem too, however, the solution is rather simple. go to system - preferences - advanced desktop effects settings. when you are there, go to the window decoration option and under the command field, fill in the following:

```
emerald --replace
```

this should get you up and going after a reboot. it did with me. i have attached a screen shot in case there is any confusion. good luck!!

---

### Post by OzzyFrank on 2008-05-05
Hi and thanks. **emerald --replace** does indeed fix that, and I can now choose different themes. Tried that command and a couple variations in terminal previously with mixed results (usually made things worse) but putting it in the Compiz settings did better. Only one thing wrong with it now, and that is all of a sudden I can no longer import new themes with a double-click! I can import them via the Import button, which is the main thing. Would like to know why I suddenly lost that feature though!

---

### Post by BLTicklemonster on 2009-02-20
I can't believe that after all this time there's not a button scripted into it to resolve this. It's like somebody doesn't want people using Emerald or just don't care or something.

---

