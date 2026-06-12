---
title: "Edgy problem after update: perpetual login."
date: 2007-04-05
forum: General Help
---

### Post by Nachimir on 2007-04-05
Hello.

Since installing system updates this morning (about 01:00 GMT), every time I login, gdm starts, the splash shows, programs begin to load, then the screen goes black and after a while I'm returned to the login screen. The only way I can do anything with my system is by logging in to the failsafe terminal.

The first time this happened, I was shown the message:

> I've detected another panel running, and will now exit.

After searching these forums and many others for similar problems, I've mangled the problem in various ways (detailed below) and managed to retrieve another error message:

> "There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

It usually disappears very fast if I get to see it at all; the above is copy pasted from another thread as I only get a few seconds max with the X server before it bails back to the login screen.

Note that this is not a fresh install, it's one I've been using fairly reliably for a month. Athlon XP3200, and an nVidia 6600 GPU with nonfree drivers. All working fine from installation until today.

Also, I run beryl with AIGLX. However, I hadn't changed any gnome or graphics settings before shutting down my system last night, I only booted, watched a DVD using vlc, installed the Ubuntu updates then shut down (Note: I have universe and multiverse enabled in my sources.list).

After searching for similar problems here and through google, here are all the things I've tried (Not all at once! One at a time ;)):

```
sudo /etc/init.d/gdm restart
```

No joy, but I think this was when I first saw "There was an error starting the GNOME settings daemon" instead of "I've detected another panel running".

Checked /etc/hosts for 127.0.0.1 localhost
then checked /etc/network/interfaces for auto lo

All present and correct.

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Reset gdm to defaults, and IIRC at this point I stopped seeing any error messages at all, it just loads the splash, starts populating the desktop environment, goes to a black screen then back to the login.

```
mv /home/<user>/.gconf/apps/panel /home/<user>.gconf/aps/panelOLD
```

No change.

```
rm -rf recently-used.xbel
```

No change.

```
sudo dpkg-reconfigure gnome-
sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session
```

No change.

```
killall gnome-panel
```

(Then stop and restart gdm)

No change.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

No change.

```
chmod -R 664 ~/.gnome*
```

This caused a different error, saying that my session had lasted less than 10 secs. The output it showed me from xsession-errors ended with:

> could not create gnome accelerators directory `/home/<user>/.gnome2/accels': Permission denied

I fixed that with:

```
chmod -R 764 ~/.gnome*
```

but that sent me straight back to square 1: "I've detected a panel already running, and will now exit".  None of the above, coupled with gdm restarts and system reboots, has fixed the problem, though gdm is now stripped back to the default settings. After changing the file permissions for .gnome* and seeing the message about the other panel running, "killall gnome-panel", gdm stop and restart from the failsafe terminal just gets me back to the perpetual login screen, wherein I see no error messages, just a couple of seconds with the splash and desktop, then black screen, then back to the login screen.

I also tried the solution given in [this post](http://ubuntuforums.org/showpost.php?p=1833052&postcount=7), but to no avail. Black screen and back to login just recurs after I reinstall and reboot.

I'm posting this by running Firefox from the failsafe terminal. Basically, I have a working mouse pointer and can load windowed programs (such as gedit) but none of them have any window decorations, can be moved, switched between, brought to the front, etc. Also, only the middle click clipboard works, right click copy-paste and associated keyboard shortcuts are not functional.

Additionally, I ran gnome-control-center, changed the theme, but of course couldn't exit the window after doing so. CTRL + ALT + F1 got me out, but got me straight back to "I've detected a panel already running" etc.

Beryl is the only tihng that occurs to me now, but I really don't want to go through the hassle of uninstalling then reinstalling and reconfiguring Beryl... but if it's the only option left I will. Is there anything else people can think of that might be at the root of this?

Forgive me, I'm fairly new to Linux and only just learning how the file system is set up, so I don't really know where to look for logs, etc. If I haven't provided enough information it's ignorance, not stupidity, so please point me in the direction of anything else you need me to tell and I'll post it.

---

### Post by jordanmthomas on 2007-04-05
One more thing to try.  I used to have the same problem sometimes and 
```
rm ~/.gtkrc*
``` would fix it.
This has to do with custom gtk settings that can get set through various ways.  Having a .gtkrc-2.0 messes with the gnome-session a lot of the time.
Maybe it will help you too?

---

### Post by fugufish on 2007-04-05
I am having the exact same problem. Hopefully someone can help us...

---

### Post by bapoumba on 2007-04-05
> **twoflush said:**
> 
```
killall gnome-panel
```

Before you restart GDM, does this fix your problem ?
If so, please run: 
```
killall gnome-panel
gnome-session-save
```
and then logout and log back in, see if it helps.

If not, set up a new user (from a recovery session for example)
in recovery (you'll be root:
```
# adduser <new_user_login_here>
reboot

```
and see if the new user has the same problem.


Congrats on all the research you have been doing here.
I really hope you can get out of this :)

edit: do you save your session on exit ? Try to uncheck that in **gnome-session-properties**

---

### Post by cmost on 2007-04-05
You guys are making this MUCH harder than it needs to be.  The solution is simple.  You can reinstall your nvidia or ATI driver, or, follow the steps presented by 'bazcor' in this thread.  You DO NOT need to create a new user account!!!

[http://ubuntuforums.org/showthread.php?t=400989](http://ubuntuforums.org/showthread.php?t=400989)

---

### Post by Nachimir on 2007-04-05
jordanmthomas and bapoumba, thanks for pointing me to other possibilities. rm ~/.gtkrc* and gnome-session-save didn't help, though I didn't know how to add and edit users from the command line until today, and that revelaed it was specific to my account.

cmost, thank you very much. Reinstalling the nvidia driver has fixed it.

[size=1](I was preparing to have nightmares about kernel mismatches when I remembered I could get nvidia drivers from the repos, and just installed them the hard way out of stubbornness last time ;))[/size]

---

### Post by emarcellus on 2007-04-05
I did a reinstall of the NVIDIA drivers via envy and Gnome was still broken for me.
I ended up installing KDE

sudo apt-get install KDE

After a reboot I could choose KDE and then I ran the Synaptic Package manager and Forced xorg back to the previous level. After another reboot then Gnome was working again.

Ed

---

### Post by holomorph on 2007-04-06
Having the same problem; tried deleding all the .gnom* and .gconf* and .gtkrc* files in my home directory, but no luck.  I created a new user, and don't have the problem.  For some reason though when I log in (as myself, which is broken) it still looks like it's loading beryl.  Now why would that be? obviously there are some configuration session settings that I am missing; where are they hiding?

I'm going to try re-installing my Nvidia drivers, but I still want to know where those setting are hidden.

---

### Post by jordanmthomas on 2007-04-06
```
/etc/xdg/autostart
```
is a directory with applications that start with gnome.  Perhaps you have a beryl entry in there.

---

### Post by holomorph on 2007-04-06
it would be in my home directory somewhere, since the problem does not occur w/ other user accounts (doesn't try to load beryl)

on the up side, re-installing my nvidia driver has cleared up the issue.  too bad I managed to lose a bunch of my launchers from my panel, but I can add those back. :p

---

### Post by Nachimir on 2007-04-06
Well at least the damage is largely aesthetic, eh? Still, an extremely annoying update.

This post may be useful for anyone who's fixed the problem but is still having trouble with Beryl.

After reinstalling the nvidia driver I found myself back in a proper desktop environment and beryl loaded just fine, but it could only use metacity for window decorations. Here's how I just fixed it.

GLX was failing to load, here's the relevant excerpt of my Xorg.0.log:

> (II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000040gl
(EE) Failed to load /usr/lib/xorg/modules/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

[size=1]( Attention fellow newbies: it's located in /var/log/ )[/size]

My first thought was to remove the repo nvidia driver and reinstall using Envy. Envy is brilliant, but the problem remained. GLX was failing to load because the relevant files and links were messed up.

Here's what I found:
in /usr/lib/xorg/modules, there was a symlink entitled libglx.so, pointing to libglx.so.1.0.8776, located in the same directory. In /usr/lib/xorg/modules/extensions, there was libglx.so and libglx.so.1.0.9755.

I changed the symlink to point to /usr/lib/xorg/modules/extensions/libglx.so.1.0.9755 then rebooted, and now everything works as it should.

---

### Post by Kunstar on 2007-04-09
hey, 

I had the same problem....I've been using ubuntu for a week now and this happened!

If you type:

sudo killall gdm

and then 

sudo gdm restart

seems to solve the problem. You are automatically logged out. As soon as you sign in again everything is back to normal.

Hope this works!

---

### Post by vhof on 2007-06-12
Thanks. I have this problem in Feisty.

sudo dpkg-reconfigure gnome-
sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session

solved the problem.

But middle mouse button *scrolling*  doesn't work :)

---

