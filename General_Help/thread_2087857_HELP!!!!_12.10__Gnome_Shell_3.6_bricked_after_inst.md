---
title: "HELP!!!! 12.10 / Gnome Shell 3.6 bricked after installing ibus"
date: 2012-11-24
forum: General Help
---

### Post by The Bright Side on 2012-11-24
Hey guys!

I just installed the updated iBus packages from the [https://launchpad.net/~jbicha/+archive/ibus](https://launchpad.net/~jbicha/+archive/ibus) ppa (ppa:jbicha/ibus) to bring back the keyboard indicator.

Now, my system is completely bricked. When I boot into the graphical interface, I see my wallpaper and the spinning "busy" mouse cursor.

I purged the jbicha PPA from tty6, resetting all the packages to their previous versions, but it seems like they did some deeper damage somewhere else in my system that just removing them cannot solve.

Problem is, a "busy" mouse cursor won't tell me what's going on inside the system. I really want my OS back :-(

Can anybody help me? Do you have any troubleshooting tips?

EDIT: I'm on 12.10, 64 bit, Gnome Shell, using the Gnome PPA to have all Gnome components up to date. When I get stuck on the wallpaper with the "busy" cursor, none of the usual shortcuts (e.g. CTRL-ALT-T to bring up terminal) work.

---

### Post by The Bright Side on 2012-11-24
I typed "unity" into the command line in tty1 and got the following segfault after a long list of compiz (core) messages:

(compiz:2810): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz:2810): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

When I type "gnome-shell", I get this:

Window manager error: Unable to open X display.

I will re-install nvidia-current-update now.

---

### Post by The Bright Side on 2012-11-24
After typing "unity", it now gets stuck on:

compiz (core) - Info: Loading plugin: opengl

And gnome-shell still has the same as before (cannot start X server).

I don't even think the graphics drivers are my problem here. I think something else is badly messed up. Please... Anybody?

---

### Post by Mr. Picklesworth on 2012-11-24
You definitely removed everything that was installed from the ibus PPA, right? I'm asking because there was an update in the GNOME 3 PPA which caused this just now on all of my systems. It's probably just funny timing that you happened to be trying that other PPA at the same time. As long as the GNOME 3 PPA's new version of gnome-settings-daemon 3.6 is running, it seems GTK apps all crash. I managed to rescue my system by using "DISPLAY=:0 sudo fluxbox" in a terminal, then using Synaptic to revert everything to do with gnome-control-center and gnome-settings-daemon. It's fiddly, though.

---

### Post by The Bright Side on 2012-11-24
Oh wow.

Yeah, I used ppa-purge to revert everything from that ibus PPA. It's true though: when I updated the packages from the ibus PPA to begin with, there were a few other new updates downloaded along with it. Thanks for your tip, I will try this first thing tomorrow (about to leave the house).

How do you revert packages selectively in Synaptic? I'm thinking I'll just purge the whole Gnome PPA for a week or so until they have this resolved.

Thanks!

---

### Post by Phred on 2012-11-25
There is an update in Gnome3 PPA for GTK+ that solve that problem.

---

### Post by The Bright Side on 2012-11-25
Thanks Phred. I was suspecting they'd have one quickly.

I ran

sudo apt-get update

Then

sudo apt-get upgrade

It installed the following updated packages:

gir1.2-gtk-3.0
gnome-accessibility-themes
gnome-themes-standard
libgail-3-0
libgtk-3-0
libgtk-3-bin
libgtk-3-common
libva-x11-1
libva1

When I logged back in, the Gnome Shell UI launched properly. But now, when I move my mouse up to the "Activities" corner or press the Super key, the system freezes. I can access everything else (all the options from the user menu, network menu, sound menu, clock).

Other observations:

The weather extension I had in my top panel (neroth's alternate weather) is gone.

From my laptop, I also went back to the jbicha PPA for the ibus that fixes the broken keyboard indicator for Gnome Shell. There's a note on the PPA's page now:

Update: If all you need is the keyboard indicator in GNOME Shell for Ubuntu 12.10, please just use the GNOME3 PPA. It is safer and better.

But even after the latest update from this morning, there's no keyboard indicator to be seen.

This is a sad, sad state of affairs. :cry: I'll dump the Gnome PPA now and will never touch it again.

Do you guys know anything else I don't know?

---

### Post by The Bright Side on 2012-11-25
Okay so I purged the Gnome PPA and now everything is completely broken. My PC boots into a black screen with a blinking command line cursor in the top left corner.

I'll reinstall everything some time this week and switch to Unity. It's a real shame. I loved Gnome Shell, but I've had so many problems with it in 12.10, even before this disaster, while Unity works just great on my laptop, that I don't think there's any more point to it.

Thanks for your help, fellas.

---

### Post by Phred on 2012-11-25
Earlier when I made the update, the only upgradable packages were:
gir1.2-gtk-3.0
libgail-3-0
libgtk-3-0
libgtk-3-bin
libgtk-3-common

And so far, everything works fine.

Now I can also upgrade gnome-accessibility-themes and gnome-themes-standard, but I don't dare to do so :-(

---

### Post by The Bright Side on 2012-11-25
Though it doesn't matter to me anymore, do you guys know if there's a bug report regarding this? I guess there has to be, but I couldn't find any other info anywhere about this issue. I would have thought the community would go crazy about Gnome updates breaking people's systems.

I actually ended up going back to 12.04 and Unity. Just finished setting it up. Love how smooth and stable it is.

---

### Post by Phred on 2012-11-26
> **The Bright Side said:**
> Though it doesn't matter to me anymore, do you guys know if there's a bug report regarding this? I guess there has to be, but I couldn't find any other info anywhere about this issue. I would have thought the community would go crazy about Gnome updates breaking people's systems.

I actually ended up going back to 12.04 and Unity. Just finished setting it up. Love how smooth and stable it is.

I think the good place to report this is the gug page of Gnome3 team :
[https://bugs.launchpad.net/~gnome3-team](https://bugs.launchpad.net/~gnome3-team)

---

