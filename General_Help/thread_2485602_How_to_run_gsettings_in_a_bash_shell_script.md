---
title: "How to run gsettings in a bash shell script?"
date: 2023-04-03
forum: General Help
---

### Post by stevermann on 2023-04-03
Running this command over SSH: ```
gsettings set org.gnome.desktop.session idle-delay 1800
``` works fine from a terminal window, but I would like to run it in a Bash shell script.

When I do, I get this error:
```
(process:5193): dconf-WARNING **: 14:24:15.645: failed to commit changes to dconf: Error spawning command line “dbus-launch --autolaunch=96547b510247455192a371ee86060d2b --binary-syntax --close-stderr”: Child process exited with code 1

```
I've tried:
```
dbus-launch gsettings set org.gnome.desktop.session idle-delay 1800
```
and
```
DISPLAY=:0 gsettings set org.gnome.desktop.session idle-delay 1800

```But I get the same error.

Any ideas would be appreciated.

---

### Post by Tadaen_Sylvermane on 2023-04-04
Install dbus-x11 package

Had same issue some time ago. Took awhile to track it down

---

### Post by MAFoElffen on 2023-04-04
> **Tadaen_Sylvermane said:**
> [COLOR=#ff0000]Install dbus-x11 package[/COLOR]

Had same issue some time ago. Took awhile to track it down

Could you please explain this answer? They asked for a solution from a bash script.

The reason i ask, is that dconf-launch spawns another instance of dbus, instead of identifying and dealing with the current instance. What I thin is needed is to id the current instance and set "it" via exporting the $DBUS_SESSION_BUS_ADDRESS. (See Below), so any changes without doing that would disappear when that new instance disappeared, which is a challenge when you are connected via ssh or from a script, where you instantiate a new shell instance.

So wouldn't it rather be to do:
```

export DBUS_SESSION_BUS_ADDRESS=$(grep -P -o -a "(?<=DBUS_SESSION_BUS_ADDRESS=).+?(?=\x00)" /proc/"$(pgrep gnome-session | head -1)"/environ)

```
Like this:
```

mafoelffen@Mikes-ThinkPad-T520:~$ echo $(grep -P -o -a "(?<=DBUS_SESSION_BUS_ADDRESS=).+?(?=\x00)" /proc/"$(pgrep gnome-session | head -1)"/environ)
unix:path=/run/user/1000/bus

```

---

### Post by Tadaen_Sylvermane on 2023-04-05
I'd be lying if I said I knew why it worked. I had found that in a forum post somewhere a long time ago. I had the same error when I ran my backup script which ran a few gsettings commands to configure DejaDup to look in a specific place. I don't even know what Dbus is or does to be honest. Not something I've really dug into.

---

### Post by MAFoElffen on 2023-04-05
> **Tadaen_Sylvermane said:**
> I don't even know what Dbus is or does to be honest. Not something I've really dug into.

I've read discussions on it's use and debugging it. It is a type of inter-process communications protocol, kind of like an API styled messaging system, where applications can use it to talk to each other. For example the Update Manager telling the Power Management System to "NOT go to sleep" during an update process. If that kind of messaging didn't go on while trying to do things like that, things could get ugly. In debugging sessions, most of the messages I see going on are related to wifi and XServer. I can filter on errors and see where there are problems...

I relooked up one of the things I read, that this thread reminded me of:
> 
One of the issues dbus does address is to separate the X resource database portion of the X server (which still exists) from the X server. This is not necessarily a bad thing, but it does force yet another authentication and authorization problem with X applications working remotely (the "can't contact dbus" is due to the addressing failure between a remote application and the local resource definitions...), which makes some gnome tools act odd.


---

