---
title: "How to manually remove gnome-panel applets"
date: 2008-04-22
forum: General Help
---

### Post by booyabazooka on 2008-04-22
I recently added a handful of applets to gnome-panel.  Gnome-panel is now not responding, and sits here eating 50% cpu time (one of two cores).  How can I remove applets when gnome-panel isn't working?

---

### Post by booyabazooka on 2008-04-22
Actually, I'm getting pretty desperate here - if there's a way to just restore the default gnome-panel settings, that would be fine too.

---

### Post by booyabazooka on 2008-04-22
Okay, sorry about the premature question-asking, but I was in a bit of a panic.

This did the trick:
  gconftool-2 --recursive-unset /apps/panel

---

### Post by kam.samji on 2008-04-22
Will this restore the original Panel? As i accidentally deleted my panel and had to put one together myself, but not all teh features of teh original are there...and I miss them!!

I have just upgraded to 8.04 hoping it rectify this, but it hasn't!

ps - where do i type the command? I'm not good with the command lint thingy..i prefer a GUI!

Thanks,


Kam

---

### Post by Ub1476 on 2008-04-22
I think this is the original:

TOP (from right)

Shutdown launcher - Clock - Volume - Notification area - User switcher - Applications menu (left)

Bottom (from left)

Show desktop - Window menu - Separator - Trash

---

### Post by kam.samji on 2008-04-22
Ok, just ran that command and...it got rid of the panel completely... What i wanted to do was restore the original panel. Now, i know I can make up a new panel myself and that's what i did last time, but not all of the icons are available to add on. for eg, the battery level indicator is different to the one that comes originally. Also, teh network monitor is different...

Can anyone help please?

---

### Post by kam.samji on 2008-04-22
Sorted...a restart then bought back the original Panel. What a sight for sore eyes that was!

thanks

---

### Post by Nem1976 on 2008-04-22
Wow this fixed my issue.  I did an upgrade from gutsy to hardy and my top panel became uneditable.  After running the command it killed the panel and after I restarted the panel was back to normal now I can edit it.

Thanks
Nem

---

### Post by booyabazooka on 2008-04-23
I'd still like to figure out where exactly the panel config is stored, so I could have fixed this without annihilating the whole panel setup.

My biggest hurdle to solving this was not realizing that it seems to require a full reboot to update.  I don't see why restarting X wouldn't be enough?

---

### Post by JackandJohn on 2008-04-28
I just caused this problem with one of the weird mouse applets; didn't have a right-click menu that I could see for removing it.

Seeing the command above, I learned two things by just looking, and I'm going to run through it:

```
gconftool-2 --recursive-unset /apps/panel
```

gconftool-2: This told me the settings were in gconf - Gnome Config (It's like the windows registry)

/apps/panel: This told me where to look


So, I launched the gconf editor
```
gconf-editor
```

And went through apps, then panel.

Now comes the tricky part: apparently the GUI doesn't like to manipulate the data that much, so I could not figure out how to delete any panel applets manually.

So, being a fluid and enterprising type, I tried changing the type into something else semi-randomly and reloading the panel ( killall gnome-panel )
This caused some odd behaviour, and changed the applet, but did not let me remove it (it acted like it was successful, but just stayed there)

So, I added a bunch of fish to take up any extra slots in the numbering of the panels, and then reopened gconf-editor and copy/pasted everything from a fish to the offending applet.

Reloaded the panel again, and was then able to remove it successfully! :)


So; gconf-editor > change the bad one to a different valid applet > reload the panel > right-click and remove the applet. Tada!


Hope this helps someone, and especially hope that someone else can add what they know and refine this for future searchers.

---

### Post by Dynamic Man on 2011-04-21
> **JackandJohn said:**
> I just caused this problem with one of the weird mouse applets; didn't have a right-click menu that I could see for removing it.

Seeing the command above, I learned two things by just looking, and I'm going to run through it:

```
gconftool-2 --recursive-unset /apps/panel
```

gconftool-2: This told me the settings were in gconf - Gnome Config (It's like the windows registry)

/apps/panel: This told me where to look


So, I launched the gconf editor
```
gconf-editor
```

And went through apps, then panel.

Now comes the tricky part: apparently the GUI doesn't like to manipulate the data that much, so I could not figure out how to delete any panel applets manually.

So, being a fluid and enterprising type, I tried changing the type into something else semi-randomly and reloading the panel ( killall gnome-panel )
This caused some odd behaviour, and changed the applet, but did not let me remove it (it acted like it was successful, but just stayed there)

So, I added a bunch of fish to take up any extra slots in the numbering of the panels, and then reopened gconf-editor and copy/pasted everything from a fish to the offending applet.

Reloaded the panel again, and was then able to remove it successfully! :)


So; gconf-editor > change the bad one to a different valid applet > reload the panel > right-click and remove the applet. Tada!


Hope this helps someone, and especially hope that someone else can add what they know and refine this for future searchers.


This didn't work perfectly for me. Maybe I just misunderstood something in your instructions but some of the applets just refused to be dealt with, it seemed.

Your post (and indeed the rest of this thread) still helped me a lot though!

You can do it like this (at least I did):


**Step 1 - Start gconf-editor** 

```
gconf-editor /apps/panel/applets &
```

The path given is not necessary to start gconf-editor, but it makes it  start in that section right away without you having to click your way there.

The ampersand ("&") that is appended last on the command line is not necessary. It is however pretty useful to make a program (in this case gconf-editor) run in the background, so you can still use the terminal without ending that program first.


**Step 2 - Check what the gconf folder name is for the applet**

Click on a folder to see the keys and settings for that specific applet. There is a key named bonobo_iid where the name of the applet can be found. 

In my case I wanted to remove the Deskbar applet, which for me had the bonobo_iid "OAFIID:Deskbar_Applet" and was found in the gconf folder "applet_3".


**Step 3 - Remove the applet**

```
gconftool-2 --recursive-unset /apps/panel/applets/<gconf folder name>
```

Replace <gconf folder name> with the name you found in the previous step. In my example I typed:

```
gconftool-2 --recursive-unset /apps/panel/applets/applet_3
```


**Step 4 - Restart gnome-panel**

```
killall gnome-panel
```

This will close down your panels and restart them with the new settings. Or you could just wait until next time you restart your computer, I guess.


**Disclaimer**

* There might be better ways to do this, but this worked fine for me. 
* I don't run Ubuntu at the moment, so I did this on Linux Mint Debian Edition (LMDE). I think it should work on both Ubuntu and most other distributions that are based on Debian and Gnome, though.

---

