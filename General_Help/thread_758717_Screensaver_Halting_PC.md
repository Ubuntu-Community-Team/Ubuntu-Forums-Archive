---
title: "Screensaver Halting PC"
date: 2008-04-18
forum: General Help
---

### Post by saythein on 2008-04-18
Hello everyone thanks for taking time to help me out with this. I am running Studio 7.10. Here is what happened. I never changed the screensaver from the default settings. Yesterday I got bored waiting on something to download and I started browsing through them in System-Pref-Screensaver. I clicked on Braid and now Gnome is totally stuck. It for some reason set it as my default screensaver and the kicker, a 1 minute idle time. So, the preview I get of the screensaver when I open the app to change it freezes my pc, if I leave my pc for over 1 minute it freezes. Is there any way I can change the setting without opening the app?

---

### Post by george9233 on 2008-04-18
Maybe you can just go to Synaptic and uninstall gnome-screensaver, and then reinstall it, see what happens. I hope it would help.

---

### Post by saythein on 2008-04-18
Thanks George but I already tried that. I did a complete removal of everything with the word screensaver in it then reinstalled everything except for the gnome screensaver package. I thought that this may somehow cause a different one to be default. In KDE I can switch between screen savers just fine. Could I maybe use the manager in KDE to set a screensaver to be default in both? I didn't see an option for it. I'll keep looking around, can't believe my world has been dumped on its head over a screensaver lol thanks again George if you can think of anything else please let me know

---

### Post by george9233 on 2008-04-18
Sure i will.

---

### Post by george9233 on 2008-04-18
Now I've found a really possible solution for your problem. 
Type in terminal:
```

gedit ~/.gconf/apps/gnome-screensaver/%gconf.xml

```
You should get something like this:
```

<?xml version="1.0"?>
<gconf>
        <entry name="idle_activation_enabled" mtime="1208543248" type="bool" value="true">
        </entry>
        <entry name="lock_enabled" mtime="1208400842" type="bool" value="true">
        </entry>
        <entry name="idle_delay" mtime="1208543247" type="int" value="5">
        </entry>
        <entry name="themes" mtime="1208543271" type="list" ltype="string">
                <li type="string">
                        <stringvalue>screensavers-molecule</stringvalue>
                </li>
        </entry>
        <entry name="mode" mtime="1208543271" type="string">
                <stringvalue>single</stringvalue>
        </entry>
        <entry name="power_management_delay" mtime="1208540756" type="int" value="120">
        </entry>
</gconf>

```
Change the value="true" in the both first and second entry line to value="false".

Then just save the file and exit.

I hope it would work.

---

### Post by sdennie on 2008-04-18
Another thing you could do would be to start the F-Spot photo manager from Applications->Graphics and then go to Edit->Preferences and click the button that says "Make F-Spot your screen saver" (hopefully that option exists in the version of Ubuntu you are using).  That should allow you to safely open the screensaver settings application again.

Edit:

Actually, just running this command will reset it back to blank screen as well:

```

gconftool-2 --type=list --list-type=string --set /apps/gnome-screensaver/themes []

```

---

### Post by george9233 on 2008-04-18
> **vor said:**
> 
```

gconftool-2 --type=list --list-type=string --set /apps/gnome-screensaver/themes []

```

Yes, you should use this method. Mine seems to be not working. But for a more convenient way go to menu Applications->System Tools->Configuration Editor, then Apps->gnome-screensaver, so you can modify other settings at the same time. If you don't see them in the menu, just right click on the menu and "Edit menus" to make them visible.

---

### Post by bunny rabbit on 2008-04-22
Hey, I had this problem too. It must have been because of something that I installed but I don't know what it was. Anyway, I found this thread, followed georges advice above, and it worked like a charm! I learned something about Configuration Editor at the same time too. Excellent. Thanks.

---

### Post by saythein on 2008-05-12
George and Vor, thank you guys so much for your post. The command worked and everything is back to normal. Sorry for the delay in responding I have been using a different comp. and kinda forgot about the problem. I knew that there had to be some way to do it from prompt, luckily there are skilled veterans like you guys to help me out. Thanks again.

---

### Post by trappleye on 2008-05-12
I just had the same problem. Your suggestion worked for me too. Thanks.

---

### Post by morrison1920 on 2008-05-13
I had a similar issue, my computer crashed when I selected a screen saver for the first time.  Changing preferences in F-Spot worked.  I was able to access the screen saver preferences and choose "blank" screen again.

---

