---
title: "Computer locking up while browsing the internet"
date: 2008-01-22
forum: General Help
---

### Post by Omni-X on 2008-01-22
When I right click some Java or Flash applet in ANY web browser, and then click elsewhere, my computer locks up for like 5 minutes, and it's starting to get annoying. It didn't do this before, this started recently, and I don't know why. Can anyone help?

---

### Post by davarino on 2008-01-23
I suggest that you check to make sure that your system is completely updated. Open Synaptic, click on Mark All Upgrades, wait, then click on Apply.

This is the very first step when you have a problem like this.

Then, make sure you have a system monitoring utility running (for example, Gnome's System Monitor panel).

Assuming that you have System Monitor running, click on the System Monitor icon on the panel. You will see a new window open up. Click on the Processes tab, then click on the % CPU column twice to get a listing of the memory-intensive programs on your machine.

Now, try to reproduce the problem (using a resized window on your browser, so that you can see what's going on with System Monitor). You will quite possibly see some interesting things happening with your % CPU column. For example, I have seen "Opera pluginwrap" start sucking up loads of CPU when certain plugins are called.

Also, I would suggest that you open only tabs with your browser, rather than opening new windows. (Less CPU usage.)

Another suggestion is (and it may sound frivolous) to make sure that you click on links *only once*. Remember, this is not a Windows OS that requires double-clicking. Running two instances of a plugin will have a temporary but instant and deathly effect on your computer's processing capabilities.

At least this is a start.

---

### Post by Omni-X on 2008-01-23
No, you don't understand. The whole display locks up for several minutes when I right click some animation, or ad. (Also, the context menu is different than normal. Instead of matching the system theme, it's just a boring gray which reminds me of Windows 98, except a bit darker.) Also, I use the Gnome Update Manager to install updates, so I think my computer has been updated properly.

Edit: I just checked with Synaptic, and there are no updates available.

---

### Post by Whiffle on 2008-01-23
Does the num lock button work (can you turn off/on the light?) ?   Can you switch to another terminal (Ctrl + alt + f2)?   This might give us some idea as to what exactly is locking up.  If you can ctrl+alt+f2 to another terminal, login there and run top, it might let us know what program is having issues.

---

