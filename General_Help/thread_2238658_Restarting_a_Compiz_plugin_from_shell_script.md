---
title: "Restarting a Compiz plugin from shell script"
date: 2014-08-09
forum: General Help
---

### Post by ToTheZeroth on 2014-08-09
I have a bug that has been bothering me, in various shapes, for years: after rebooting, some of my Compiz settings are lost. Actually, at the moment, this behaves quite predictably, and only concerns a minor number of settings. Furthermore, there is a work-around that is consistently working:

After each reboot:
[LIST=1]
[*]Open CCSM 
[*]Stop the **Desktop Wall** plugin 
[*]Restart it 
[*]Stop the **Ubuntu Unity Plugin** 
[*]Restart it 
[*]Close CCSM 
[/LIST]
This is fairly quick, but it would be nice if it could be automated through my startup shell script. Is this possible?

(As for the original bug, the settings I'm losing are mainly the ones in **Desktop Wall > Bindings > Edge flippings**, and **Ubuntu Unity Plugin > Launcher > Key to show the Dash, Launcher and Help Overlay** (which reverts to just tapping <Super>, conflicting with all my other Super shortcuts). They are not lost from CCSM; I don't have to re-enter them. But they are not applied until the plugins are restarted.)

(On a side note, probably unrelated, CCSM keeps disappearing from my launcher, to which it is pinned. This happens intermittently, and not on each reboot. It doesn't happen with other apps, except I think it might have happened once or twice with KeepassX.)

---

### Post by mc4man on 2014-08-09
I don't believe ccsm can be used via cli to enable/disable plugins. It's possible that some script involving gsettings could do that but there could be other solutions to at least the edge flipping issue.
(- I use rotate which hasn't had this issue in quite some time.

1. After setting up your plugins open ccsm > Preferences > Plugin List.
  Disable Automatic plugin sorting
  In the enabled plugins box move wall below unityshell by highlighting then use the down button

or 

2. This may work but  but has to be done exactly..
```
sudo -H gedit  /usr/share/glib-2.0/schemas/org.compiz.wall.gschema.xml
```
In the menu go Edit > Preferences > View & enable Display line numbers
look at or around line 215 . The section you want is  - 
 ```
   
      <key type="b" name="edgeflip-move">
        <default>[COLOR="#FF0000"]false[/COLOR]</default>
        <summary>Edge Flip Move</summary>
        <description>Flip viewport when moving a window to a screen edge</description>
```
Change the false to true - see screen
Save the file, close gedit

Then in a terminal run this, it must run without any comment or error, if you get anything it must be addressed before logging out
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```
This will now set edge-flipping (move) as default enabled which could help it from being disabled/not working

---

### Post by ToTheZeroth on 2014-08-10
Wow, thanks! Your method 1 worked perfectly for the Desktop Wall problem, I had no idea the loading order was customizable.

The other problem turned out to be a problem with my doing a little xmodmap magic in my startup script. Assuring that it gets run *before* the Unity plugin is loaded actually seems to have solved that problem as well. (I hadn't really considered this possibility before, because I would have assumed this only affected my Multikey settings, but in reality Super-A and Super-S also reverted to their defaults. Anyway, all is well now!)

---

