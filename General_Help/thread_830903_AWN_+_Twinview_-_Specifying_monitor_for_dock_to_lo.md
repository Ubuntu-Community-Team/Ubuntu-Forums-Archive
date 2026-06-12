---
title: "AWN + Twinview - Specifying monitor for dock to load in?"
date: 2008-06-16
forum: General Help
---

### Post by khughitt on 2008-06-16
Hi all,

I recently setup a second monitor on ubuntu 8.04 using Twinview. Almost everything is working great now except that I have not been able to get AWN to appear on the right screen. I would like it to load on the right monitor, but it defaults to the left one instead, and so far I have not had any luck changing that.

Any suggestions?

Thanks,

---

### Post by lxme on 2010-02-09
Hello

This is an old topic but ho well...

Using nvidia twinview on Karmic and having the same problem.
With two monitors I can't find a way to make my AWN dock to sit on my right monitor. It insists on appearing on my left screen which annoys me to no ends.
Any ideas on how to fix that?

Thanks

---

### Post by scouser73 on 2010-02-09
You need to make the monitor on the right the Primary monitor. 

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

---

### Post by lxme on 2010-02-09
Thank you for trying to help.

Unfortunately, AWN doesn't seem to care about this box being checked or not.
The login window as well as gnome-panel on the other hand do. They both appear on my primary display meaning my right screen.

I believe it might be a AWN bug, and my research about it seem to prove me right so far.
Playing with AWN advanced settings I found a "Force monitor mode" checkbox that enabled me to manually move AWN dock from my left monitor to the right one adjusting "Monitor X-offset" and "Monitor Y-offset" 
It seems to be a dirty workaround but so far it worked.

---

### Post by SnappyU on 2010-05-19
Thanks for the tip!
Finally got my awn to work properly with the multimonitor setup.

This is one crazy tweak, but it works as advertised. :)

Thanks!

> **lxme said:**
> Thank you for trying to help.

Unfortunately, AWN doesn't seem to care about this box being checked or not.
The login window as well as gnome-panel on the other hand do. They both appear on my primary display meaning my right screen.

I believe it might be a AWN bug, and my research about it seem to prove me right so far.
Playing with AWN advanced settings I found a "Force monitor mode" checkbox that enabled me to manually move AWN dock from my left monitor to the right one adjusting "Monitor X-offset" and "Monitor Y-offset" 
It seems to be a dirty workaround but so far it worked.

---

### Post by svtdragon on 2010-07-06
I just spent a few hours looking for a real solution to this problem, which doesn't require using AWN's force monitor setting or changing the primary monitor, even digging through the code; it turns out it's out there, but counterintuitive:

(For the record, I'm using the latest 0.4.0 build from the awn-testing PPA.)

Go into the preferences dialog, and go to the list of applets.  Add the "AWN Preferences" applet.  Drag it to whichever edge of whichever monitor you want AWN to be on, and it should automatically move there.

---

### Post by Flobbes on 2010-10-11
Thank you so much, was struggeling with the offset hack for a while, this is so much better!

---

### Post by Adrastus on 2011-05-26
Svtdragon, you're my hero!

---

### Post by apos on 2011-09-18
It also can be achieved with gconf-tools, e.g.:

```
gconftool-2 --type bool --set /apps/instances/avant-window-navigator/panel-1/panel/monitor_force true
gconftool-2 --type int --set /apps/instances/avant-window-navigator/panel-1/panel/monitor_x_offset 1280
```

This is scriptable, and applies at once.

Be aware, that there might be different gconf-paths for awn. Mine is in */apps/instances* and *panel-1/panel*.

Put the following script into your path and it will be accessible via Alt-F2:

Moves  awn to the current desktop:
```
move_awn
```

Moves  awn around:
```
move_awn X_OFFSET
```

```

sudo touch /usr/local/bin/move_awn
sudo chmod 755 /usr/local/bin/move_awn
sudo vim /usr/local/bin/move_awn
```

```
#!/bin/bash

XOFFSET="${1}"

[ "${XOFFSET}"="" ] && XOFFSET="0"

if [ "${XOFFSET}"="0" ]
then
        gconftool-2 --type bool --set /apps/instances/avant-window-navigator/panel-1/panel/monitor_force false
else
        gconftool-2 --type bool --set /apps/instances/avant-window-navigator/panel-1/panel/monitor_force true
fi

gconftool-2 --type int --set /apps/instances/avant-window-navigator/panel-1/panel/monitor_x_offset ${XOFFSET}
```

Hope this helps someone ):P

---

### Post by kneeki on 2011-11-08
> **svtdragon said:**
> I just spent a few hours looking for a real solution to this problem, which doesn't require using AWN's force monitor setting or changing the primary monitor, even digging through the code; it turns out it's out there, but counterintuitive:

(For the record, I'm using the latest 0.4.0 build from the awn-testing PPA.)

Go into the preferences dialog, and go to the list of applets.  Add the "AWN Preferences" applet.  Drag it to whichever edge of whichever monitor you want AWN to be on, and it should automatically move there.I wish there were an upvote or something to make this thread more noticeable. This solved my problem!

---

