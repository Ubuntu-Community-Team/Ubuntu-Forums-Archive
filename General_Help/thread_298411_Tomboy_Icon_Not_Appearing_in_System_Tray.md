---
title: "Tomboy Icon Not Appearing in System Tray"
date: 2006-11-12
forum: General Help
---

### Post by detuneyourradio on 2006-11-12
I searched for a while on this problem, and couldn't find a thing. 

I'm running Edgy, and Tomboy will run, but the icon doesn't appear in the system tray, just a tiny little space.  Alt-F12 produces the menu, and I can use it normally otherwise, I just have a tiny space in the system tray as opposed to an icon.  I assume an icon is missing somewhere, but i've removed/purged/reinstalled and same problem, and can't find where the icon should be ... 

any ideas?  

thanks.  

PS - i thought this might be a problem local to me, but a friend of mine who just upgraded to Edgy has the exact same problem.

---

### Post by detuneyourradio on 2006-11-12
I'm an idiot.  Maybe that's why this is my second post.  I didn't realize it works in the panel and not the system tray.  D'oh.

---

### Post by DJiNN on 2006-11-15
> **detuneyourradio said:**
> I'm an idiot.  Maybe that's why this is my second post.  I didn't realize it works in the panel and not the system tray.  D'oh.

No, i think you're correct..... :) I've just upgraded to Edgy, from Dapper, and my Tomboy icon is also missing. The only way that i can access it is ALT-F12 as you mentioned. 

It's probably something to do with the upgrade, but i don't know what yet. :)  I'm sure that it will get sorted soon. (Fingers crossed!) :)

---

### Post by odin1965 on 2006-11-19
Tp put it on Panel in Edgy. Rigt click on panel, pick 'add to panel'. Pick 'Tomboy Notes' under accessories.

---

### Post by helliewm on 2006-11-19
I don't have Tomboy in Accessories yet its marked as installed under ADD/REMOVE Programs. I am using 6.10.

Helen

---

### Post by odin1965 on 2006-11-22
Make sure you are not looking in 'accessories' in the menu. you have to right click on the panel. That is the area at the top that has the menus at the left. Right click on the grey area betwwen the menus and the clock, which is at the upper right of your screen. You should now see a menu and the top item should be 'add to panel'. Left click it and you should have a menu of items you can add to the panel. The first category is accessories and Tomboy should be under there.

---

### Post by Storyteller on 2006-11-25
> **odin1965 said:**
> Make sure you are not looking in 'accessories' in the menu. you have to right click on the panel. That is the area at the top that has the menus at the left. Right click on the grey area betwwen the menus and the clock, which is at the upper right of your screen. You should now see a menu and the top item should be 'add to panel'. Left click it and you should have a menu of items you can add to the panel. The first category is accessories and Tomboy should be under there.

I'm seeing a similar problem, and in my case the problem is not in adding Tomboy to the menu. I can do that just fine. The problem is, when I go to "Add to panel," then look in "accessories," there is no icon for Tomboy Notes. There is also no icon for:

Clock
Fish
Drawer
Force Quit
Window List
Window Selector
Workspace Switcher
Notification Area
Separator

I am guessing these are all related. My upgrade to Edgy was somewhat painful and I have not yet completely recovered.

---

### Post by meist3r on 2008-04-24
I had the same issue after updating to Hardy this morning. I fixed it like this:


1. Add a Tomboy shortcut to your panel
2. Start Tomboy through the panel
3. Choose "File / Close"
4. Hit the panel icon again so the same instance you just hid reappears
5. Choose "File / Quit"
6. Restart Tomboy

After the restart it loaded the icon normally into the systray. Don't know where it's coming from. Probably some flag in the old tomboy configs before the upgrade.

---

