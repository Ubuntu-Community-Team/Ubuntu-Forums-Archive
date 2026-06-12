---
title: "gnome-appearance-properties = runaway process"
date: 2007-11-25
forum: General Help
---

### Post by amadeus266 on 2007-11-25
Whenever I run the Appearance application and make my changes, when I close the program it disappears from the screen but the process continues and consumes the cpu and I have to kill it manually. Any ideas?

---

### Post by posburn on 2008-02-05
Hi!

Just wanted to say I have the exact same problem.  Every time I open gnome-appearance -properites (through GUI or terminal) it maxes out the CPU load (often, but not always, on BOTH CPUs) after I close out the program.  I have to kill the process manually as well.

I'm running Gutsy on a Lenovo Intel Core2 machine with an Intel 945 gfx card, GNOME 2.20.1, compiz, and gtk-window-decorator.

Any help would be much appreciated!

---

### Post by posburn on 2008-02-16
bump

Any suggestions anyone?

---

### Post by BattlePanic on 2008-02-17
I am running into the same problem.  It seems that whenever I launch gnome-appearance-properties it consumes about 95-99% of my cpu power and remains running even after closing the gnome 'appearance' configuration window.  I have to send the process a kill signal.

I don't know whether or not it may be causing the problem, but I happen to have the gtk-theme-switch package installed as well.  I use it to change the gtk theme when I'm using a window manager outside of GNOME.  That's the only thing I can think somehow cause some sort of conflict or problem.  I'd be curious to know if many other people are having the same problem.

---

### Post by Anduu on 2008-02-18
Do you have the GTK qt engines installed?I have heard they causes problems.Remove them if you do.

If that doesn't work try removing all custome themes from your /home/<username>/.themes and /home/<username>/.icons folders....don't delete them, just move them somewhere safe.

If the appearance manager starts behaving it means you have a bad theme in there somewhere.
If so you will have to start moving them back in increments till you find the one that is causing the problem.

---

### Post by BattlePanic on 2008-02-18
> **Anduu said:**
> ...try removing all custome themes from your /home/<username>/.themes and /home/<username>/.icons folders....don't delete them, just move them somewhere safe.


I don't have the gtk qt engine installed.  However, I did try moving all the themes stored under ~/.themes into a backup directory, leaving ~/.themes empty, to no avail.  gnome-appearance-properties was still running away with cpu usage.

I tried removing all of the .gtkrc-* files that existed in my home directory and suddenly gnome-appearance-properties was back to normal.  I'm not completely sure, but I think the culprit is .gtkrc-2.0.  I believe this file was was created when I began using the gtk-theme-switch package mentioned in my previous post.  I had previously installed this package in order to set my gtk themes when running window managers like Openbox and Fluxbox.  This file seems to be involved in specifying which gtk theme to use

Under gnome however, gtk themes seem to be specified elsewhere and this setting is enforced by the gnome-settings-daemon rather than a .gtkrc-2.0 file

Bottom line is that in my case, this file or these files seem to be breaking gnome-appearance-properties.  If this program is spiking cpu usage, try removing or renaming .gtkrc-2.0 and see if it helps.

---

### Post by Anduu on 2008-02-18
> **BattlePanic said:**
> I tried removing all of the .gtkrc-* files that existed in my home directory and suddenly gnome-appearance-properties was back to normal.  I'm not completely sure, but I think the culprit is .gtkrc-2.0.  I believe this file was was created when I began using the gtk-theme-switch package mentioned in my previous post.  I had previously installed this package in order to set my gtk themes when running window managers like Openbox and Fluxbox.  This file seems to be involved in specifying which gtk theme to use

Under gnome however, gtk themes seem to be specified elsewhere and this setting is enforced by the gnome-settings-daemon rather than a .gtkrc-2.0 file

Bottom line is that in my case, this file or these files seem to be breaking gnome-appearance-properties.  If this program is spiking cpu usage, try removing or renaming .gtkrc-2.0 and see if it helps.

Aaaah yes...forgot about that one...I've had to do that before too.Glad to here your good again :)

---

### Post by techrolla on 2008-04-26
Thanks for the hint to delete .gtkrc-2.0, fixed that problem right up.  This could be the problem other people are having with fglrx being slow...their cpu is just being used by the appearance manager.

---

