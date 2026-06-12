---
title: "Can I set permanent icons in Avant bar?"
date: 2008-06-22
forum: General Help
---

### Post by memories on 2008-06-22
I would like to use the Avant OS X-type toolbar. However, I don't want it to show windows I have open. I just want it to display icons that I preset. 

I basically just want a toolbar with big icons of the programs I use often, it doesn't need to be avant, nor pretty, but I would like if it didn't take up the entire width of the screen.

---

### Post by prshah on 2008-06-22
> **memories said:**
> I would like to use the Avant OS X-type toolbar. 
I just want it to display icons that I preset. 


You can drag-n-drop icons of programs that you want from the menu. To remove the behavior of showing running programs, open Avant properties, and remove the "Launcher/TaskManager" Applet.

---

### Post by memories on 2008-06-23
Thank you for the reply!

The problem is, removing the applet doesn't work permanently. It is only removed until I switch my workspace, and then it gets toggled back on. 

I get this at startup: 

```

$ avant-window-navigator 
Screen is composited.
Creating new applet :/usr/lib/awn/applets/taskman.desktop uid:1
LOADED : /usr/share/applications/transmission.desktop
... etc ...

(avant-window-navigator:17185): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `AwnTaskManager' has no property named `orient'

```

Another strange problem is that some links I move to the bar remain, while others don't. Firefox for example, gets removed after I close avant, but Transmission remains on the bar.. ?

---

### Post by prshah on 2008-06-23
> **memories said:**
> 
The problem is, removing the applet doesn't work permanently. It is only removed until I switch my workspace, and then it gets toggled back on. 



In this case, use the AWN manager (System-Preferences-AWN manager) to setup the taskbar to your preference.

You can "deactivate" the tasklist/window manager applet in from the "Applets" section; click on it, then click the "deactivate" button.

You can set up launchers from the "Launchers" section. 

Settings made in this fashion should "stick". Post back if they don't!

---

### Post by memories on 2008-06-23
I was actually using the awn-manager. The main problem is disabling the applet. It is the only applet I have installed and I want to get rid of it. I don't like how everytime I change workspaces, the bar (slowly) resizes.

I removed taskman.desktop and it no longer shows up in the applets window, but it is still being turned on. I was getting the error I posted in my previous reply above, when trying to delete the applet from the awn manager.

I have libawn, libawn-dev, the python bindings, etc.. all up to date. Oh noes :(

---

### Post by retiree on 2008-06-24
I have both AWN and I also have permanent Icons on the taskbar at the top of the screen. I am still learning AWN and how to customize it. There is two ways you can put permanent icons on the top taskbar:
1... You click on applications and scroll to any program you want a permanent icon and right click and add launcher to panel.
2... You can right click on a empty space on the taskbar, click add to panel and a screen will open with selections. You can left click and hold and drag to taskbar any selection you want and they will be permanent.

You can even create a new panel by right clicking on an empty space on the taskbar and select new panel, and it will add one on the right side of the screen. Hope I have explained it satisfactorily. Cheers

PS This works in Gutsy 7.10 as well as Hardy 8.04

---

### Post by prshah on 2008-06-24
> **memories said:**
> I was actually using the awn-manager. The main problem is disabling the applet. 


Did you also uncheck/untick the "Show windows from all viewports" option in General (Preferences)-General Tab?

---

### Post by memories on 2008-06-24
I got the permanent icons to stick, but I'm still having trouble getting rid of the taskmanager applet. well, the main problem is that I don't want Avant showing me what windows I have open. I already use Window List (gnome applet) for that, and only want Avant for permanent icons. 

I don't have show applications from all workspaces checked. 

Where is the applet stored on disk?

---

### Post by moonbeam on 2008-06-24
> **memories said:**
> I got the permanent icons to stick, but I'm still having trouble getting rid of the taskmanager applet. well, the main problem is that I don't want Avant showing me what windows I have open. I already use Window List (gnome applet) for that, and only want Avant for permanent icons. 

I don't have show applications from all workspaces checked. 

Where is the applet stored on disk?

You an remove the Launcher/Taskmanage applet using awn-manager.

However you will also lose you launchers....

If you do not want the taskmanager you need to remove the Launcher/taskmanager applet (awn will probably crash wehn you remove it) and use simple-launcher applet instead.  To get this launcher you need to use the awn-testing ppa (reacocard's ppa does not include vala applets).  

To use simple launcher just add however many launchers you want... it should show an applet with a red x.  Drag and drop the launchers you want into the icon...  and that's it.

This sort of functionality is scheduled to be introduced as standard in version 0.6...  for now this applet will do what you want.

[http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1618](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1618)

[http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

---

### Post by DaymItzJack on 2008-06-24
> **memories said:**
> 
Where is the applet stored on disk?

/usr/lib/awn/applets/

---

