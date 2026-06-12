---
title: "Minimized windows not in bottom status bar anymore ???"
date: 2013-06-08
forum: General Help
---

### Post by jfl on 2013-06-08
I have been using Ubuntu 12.04 for a year on my Lenovo laptop.
A few weeks ago, doing nothing unusual, I noticed the bottom bar was blank; the minimized windows didn show, even after reboots.
I didn like Unity from the beginning, so I am running **Gnome**.
It is annoying because if I minimize a window, I cannot get it back easily.
Any ideas ???
Thanks

---

### Post by r-senior on 2013-06-08
Could you post a screenshot of your desktop?

---

### Post by CatKiller on 2013-06-08
Right-click on the Panel (or some combination of modifier keys that I can't remember and right-click on the Panel) select Add To Panel and pick Window List.

---

### Post by jfl on 2013-06-08
> **r-senior said:**
> Could you post a screenshot of your desktop?

There it is:
[ATTACH=CONFIG]243649[/ATTACH]

---

### Post by jfl on 2013-06-08
> **CatKiller said:**
> Right-click on the Panel (or some combination of modifier keys that I can't remember and right-click on the Panel) select Add To Panel and pick Window List.

Tried all combinations of clicks and mod. keys; nothing happens.

However when I go to "System tools>Preferences>Display"  I get the Error box:
*Failed to execute child process "gnome-display-properties" (No such file or directory)*

Any ideas ???

---

### Post by CatKiller on 2013-06-08
I believe it's Alt-Windows key and right-click to get the menu. It used to just be right-click, which was quite discoverable, but a new key seems to get piled on with each release since Unity.

---

### Post by jfl on 2013-06-08
> **CatKiller said:**
> I believe it's Alt-Windows key and right-click to get the menu. It used to just be right-click, which was quite discoverable, but a new key seems to get piled on with each release since Unity.

Not working either.
Please note that I am not using Unity, but the Gnome Desktop.
Thanks anyway for taking the time !

---

### Post by CatKiller on 2013-06-08
I'm not either, but I still have to use Alt + Win key to get the Panel's context menu.

---

### Post by jfl on 2013-06-08
> **CatKiller said:**
> I'm not either, but I still have to use Alt + Win key to get the Panel's context menu.

OK.  I think there are other issues here.  I just tried on my other machine which has an identical configuration and the ALT+MENUKEY works.
Also, I notice I am missing the icon on the bottom left: "Hide all windows".

---

### Post by CatKiller on 2013-06-08
So have you removed the whole of the bottom panel?

---

### Post by jfl on 2013-06-08
> **CatKiller said:**
> So have you removed the whole of the bottom panel?

I didn't remove it ;-)) It disappeared a couple weeks ago !!!
Actually not quite, I still have the "Workspaces"

---

### Post by jfl on 2013-06-09
BAD NEWS:  I cannot log-in; I get to the login window, select my account enter my pw, screen goes dark for a few seconds and I am back at the log-in window   !!!
I believe it is better to start a new thread.

---

### Post by jfl on 2013-06-09
Disregard my last post; I can log-in again (permissions on .Xauthority)
But my initial problem remains.
Still no bottom panel.

---

### Post by CatKiller on 2013-06-09
Do the combo we were talking about on the top panel & select New Panel. You should be able to drag the new panel to the bottom. It might be middle-click-and-drag, and you might need to press the buttons for that too. Once it's in place add in the stuff that you want. Or there's a command to just reset your panel to defaults, but I can't remember that off the top of my head.

---

### Post by jfl on 2013-06-09
> **CatKiller said:**
> Do the combo we were talking about on the top panel & select New Panel. You should be able to drag the new panel to the bottom. It might be middle-click-and-drag, and you might need to press the buttons for that too. Once it's in place add in the stuff that you want. Or there's a command to just reset your panel to defaults, but I can't remember that off the top of my head.

Thanks for the time !
However, I cannot get a menu from the top (or the bottom) panel; I can drag icons in them, that's it.
I just upgraded to 12.10 OTA; didn't change a thing !
 Dunno what to do

---

### Post by CatKiller on 2013-06-09
According to a quick search, the process to reset your panel configuration is
```
dconf reset -f /org/gnome/gnome-panel/
killall gnome-panel
```

(two commands)

---

### Post by jfl on 2013-06-10
I just noticed something.
If I log-in as "Guest", Gnome works fine.
If I log-in as myself, the bottom panel is not working, except for the "workplace switcher".

That is driving me nuts, because, if I minimize a window, I cannot get it back.

@Catkiller
I did not try your last suggestion ... yet; I don't want to go through the customization again if I can avoid it.
And now I have a feeling the problem is in a file that is user-dependant.

I have no idea where to look for this kind of config files.

---

### Post by CatKiller on 2013-06-10
It's in ~/.config/dconf. You can look at all the things that are configured with DConf with dconf-editor, which replaces the earlier gconf-editor. How long did you spend customising it compared to how long you've been unable to correct your problem? I would just nuke it.

---

### Post by jfl on 2013-06-10
> **CatKiller said:**
> It's in ~/.config/dconf. You can look at all the things that are configured with DConf with dconf-editor, which replaces the earlier gconf-editor. How long did you spend customising it compared to how long you've been unable to correct your problem? I would just nuke it.

You are absolutely right; it would be over by now ;-))  But then, I wouldn't have learned much !  It is the challenge !!!

Thanks a bunch, though

---

