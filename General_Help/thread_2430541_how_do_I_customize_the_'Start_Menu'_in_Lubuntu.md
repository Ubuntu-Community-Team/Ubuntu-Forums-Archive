---
title: "how do I customize the 'Start Menu' in Lubuntu?"
date: 2019-11-03
forum: General Help
---

### Post by alanralph on 2019-11-03
[FONT=Arial]Hi [/FONT][FONT=Arial]
[/FONT]
[FONT=Arial]I am completely new to Linux, and am using Lubuntu 19.04.  

I've been searching endlessly to figure out how to update the 'start' menu, similar to in Windows. I have searched and searched, and cannot seem to find anything that tells me how to modify (customize) the 'start menu'.

For instance, under "Other", lists "Software" and "MS Office FrontPage" (*which I figured out how to install via Wine*).  How do I get "MS Office FrontPage" listed under "Office"?  (*don't judge, my website is simple enough to still be able to use FrontPage!*)

How do I remove "Software" from this "Other" menu, since the same "Software" is also listed under "Preferences"?


Thanks for your help. If this has already been mentioned elsewhere in this forum, please link me to it...





[/FONT]

---

### Post by guiverc on 2019-11-04
The easiest option for common (or favorite) applications is using the Quick Launch bar on your panel. For details on using this, I'll suggest the Lubuntu manual, ie. [https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html?highlight=quick%20launch](https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html?highlight=quick%20launch)

Currently there isn't a LXQt menu editor, though it's been suggested before ([https://github.com/lxqt/lxqt/issues/255](https://github.com/lxqt/lxqt/issues/255))

When I was new to GNU/Linux I too wanted to make minor changes to the menu system, but have since decided it wasn't worth it (they can get overwritten with added/removed software or updates, and make release-upgrading more of a hassle, esp. significant with your 19.04 since it's more ~70% through it's support cycle).  I forget where the menu is stored, but when/if I remember I'll return...

---

### Post by Holger_Gehrke on 2019-11-04
Is LXQt so different from other desktops used in Ubuntu flavours that it's not generating its menus from .desktop-files ?

There should be system-wide .desktop-files in '/usr/share/applications' and user-specific overrides in '~/.local/share/applications'.

I'd just 'grep' through the files in the latter directory to find the .desktop-file for Frontpage (which might actually be hiding out in a subdirectory 'inspired' by the way windows builds its menus, something like '~/.local/share/applications/wine/Programs/Microsoft Frontpage/' at a guess), open it in an editor (.desktop-files are just text, the format is described on [freedesktop.org]("https://specifications.freedesktop.org/desktop-entry-spec/latest/")) and change the line that starts with 'Categories=' to 'Categories=Office;'. 

For 'Software' things are a bit more complicated since it's probably a system-wide .desktop-file. To override it I'd copy the .desktop-file (should be '/usr/share/application/org.gnome.Software.desktop') to ~/.local/share/applications and again edit the 'Categories='-line.

Holger

---

### Post by oldrocker99 on 2019-11-04
Ubuntu MATE has, in MATE Tweak, a setting called "Redmond," which gives you a Windows 7-like interface. I highly recommend it.

---

### Post by GhX6GZMB on 2019-11-04
[COLOR=#000000]This is unfortunately very difficult in LXQt. There is no program available for customizing the Start Menu.[/COLOR]

[COLOR=#000000]Login as main user and go to [/COLOR]**/etc/xdg/menus **and (sudo) open [B]lxqt-applications.menu

[/B]_***Save a backup ***of the file._

Play around with the file and modify or comment out all items that you want to change (using <!-- xxxxxxx -->). [B][B][B][B][I][B]Do not modify the top level of the file, identifiable from the indents!
[/B]
[/I][/B][/B][/B][/B]Be prepared that changes will not always bring the expected result, or that you need to modify other files in this process.

Logout and login to see if your changes work. You might even have to reboot.

---

### Post by alanralph on 2019-11-05
Thanks for the suggestions. I plan to look through and try some of these things soon.

---

