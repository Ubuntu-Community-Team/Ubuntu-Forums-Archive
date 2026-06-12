---
title: "feisty - setting time and date format destroys my panel"
date: 2007-03-08
forum: General Help
---

### Post by kacheng on 2007-03-08
Hi I'm running Feisty.

I tried to change the time and date settings.  I was wondering what internet time was, so I set it to internet time (vs 24hour or 12hour).

Immediately, the panel started to die and restart itself and die over and over.  I'd get messages like 'I've found a panel already running, so I won't start'.  Eventually, I get to a blank desktop.  I can't do anything.

Rebooting does not change the behaviour - it cycles, it dies, I have to reboot.

Is there a way to reset the time and date format setting back to 12hour using the terminal (I'd have to reboot in recovery mode)?
Or can I reinstall a time package?
I'd prefer not to reinstall the entire OS.

Thanks

---

### Post by DagMan on 2007-03-08
You can try 
sudo time-admin
but it doesn't sound like it's what you're after.

---

### Post by cklubi on 2007-03-08
wait until the panel restarts end and you can see yor desktop, launch a terminal window, run gnome configuration editor from there and find your panel configuration and change the clock setting back to 24 hour. logoff and when you log on again you're fine

(this happened also to me the same way :) )

---

### Post by kacheng on 2007-03-08
Thanks for your suggestions.

When everything settles and the error messages are done, I have a resulting screen with nothing on it.  Nothing.

No icons.

No panel.

I can't kill GDM using Ctrl-Alt-Bksp.

I can only get the rudimentary right-click menu to "add a launcher", etc. (What can I do with this?)

So there's no way to run any graphical programs/configuration programs.



I can ssh into the box, and login.  I think I'll need to manually edit some configuration file somewhere or run a configuration wizard in text mode, but I'm not sure what/where/how.

Again, all I want to do is set the time display back to "12hour" from "internet time"

Any ideas?

---

### Post by cklubi on 2007-03-08
ok, when you are at the empty desktop:

ALT+F2 to open Run Application dialog;
run: gconf-editor

find this -> /apps/panel/applets/clock_screen0/prefs/format

change the "format" key value to: "24-hour"

logout / log back on, panel should be working now again



Hope this helps!

---

### Post by kacheng on 2007-03-08
Unfortunately, Alt-F2 does not give me anything, so I can't run gconf-editor.

However since I can ssh into the box, do you know what text config file might contain this setting?

I've looked into:

/etc/adjtime
/etc/localtime
/etc/timezone
/etc/gnome-system-tools/users/profiles
/etc/gconf/*
/etc/gnome/*
/etc/environment
/usr/share/calendar

but no luck so far.

---

### Post by kacheng on 2007-03-08
I just realized that this preference must be set on a user by user basis.
I think I may have found the file at:

```
sudo nano ~/.gconf/apps/panel/applets/clock_screen0/prefs/%gconf.xml

```

I took:
```
        <entry name="format" mtime="1173356153" schema="/schemas/apps/clock_applet/prefs/format" type="string">
                <stringvalue>internet</stringvalue>
        </entry>

``` 

and changed it to 
```
        <entry name="format" mtime="1173356153" schema="/schemas/apps/clock_applet/prefs/format"/>

``` 

Unfortunately, I'll have to wait until I get home tonight to see the results.

UPDATE:
This worked!

---

### Post by cklubi on 2007-03-08
:)   problem solved then

---

