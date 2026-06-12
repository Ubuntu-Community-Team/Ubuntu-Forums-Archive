---
title: "Making keyboard modifications stick"
date: 2024-02-16
forum: General Help
---

### Post by alfeberlin2 on 2024-02-16
I have created an own *.kbd file which modifies my keyboard slightly.  This works as expected, but I have to load it explicitly using xkbcomp.  Also, when loaded, from time to time something unknown triggers loading the default again, then I have to redo the call of xkbcomp.

I have searched through the Internet for advice on this, and there is a lot, but all I found was either outdated or way to vague to be useful (“have a look at udev” or similar).

I could imagine to place my .kbd file somewhere in the system (/lib/… or such) so that my file simply replaces the default which is normally loaded.  I also can imagine to install a special trigger using some udev magic (but I only vaguely know what it’s good for, not how it’s used).

I am using Ubuntu 22.04 with xorg on Thinkpad laptops.  Hints on how to modify the keyboard under Wayland are also welcome, but not my direct goal.

---

### Post by dragonfly41 on 2024-02-16
Not answering your question directly .. but if your aim is to assign keys to some bespoke actions then there are several tools you might exploit: Albert (launcher) and Actiona (UI emulator). Both can be setup to look for keys and then run actions. These do not modify keyboard actions, they listen for keys. Also look at xdotool.

---

### Post by dragonfly41 on 2024-02-16
To answer your question directly I asked a local ChatGPT agent I use occasionally when stumped and this was the answer given .. 

[COLOR=#1B1642][FONT=&amp]To place a custom *.kbd file in Ubuntu and avoid it being reset, you should place it in the /usr/share/kbd/keymaps/ directory. This directory is used to store keymap files, and placing your custom file here will ensure that it is not overwritten by system updates or package installations [2]("https://wiki.archlinux.org/title/Linux_console/Keyboard_configuration").
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]Here are the steps to place your custom *.kbd file:
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]
[LIST]
[*]Create a backup of your current keymap configuration, just in case you need to revert back to it.
[*]Copy your custom *.kbd file to /usr/share/kbd/keymaps/.
[*]Ensure that the file has the correct permissions and ownership to be readable by the system.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]To apply the new keymap, you may need to update the keyboard configuration using the setupcon command or by rebooting the system.
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]Keep in mind that any system updates or package installations could potentially overwrite the files in /usr/share/kbd/keymaps/, so it's a good practice to periodically check for updates to your custom keymap file. 
[/FONT][/COLOR]

---

### Post by alfeberlin2 on 2024-02-19
Hi Dragonfly,

Thanks for your efforts, but the problem is that something somewhere in the system (Gnome, Xorg, &#8230;) chooses to reload some defaults from time to time (e.&#8239;g. after suspend or so).  And these defaults still seem to be the original `us` keyboard settings.  I have created a file called `alfe` in `/usr/share/X11/xkb/symbols` containing all my changes.  When I now execute `setxkbmap alfe` this works.  I also set the dconf `/org/gnome/desktop/input-sources/sources` to `[('xkb', 'alfe')]` (or to `us+alfe`), but that does not have the desired effect.  After login, the original `us` setting is active, and something else still seems to load the `us` settings from time to time.  I still need to find out how to override this hidden default.

---

