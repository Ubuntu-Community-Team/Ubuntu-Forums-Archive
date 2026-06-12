---
title: "Panels and windows disappear"
date: 2007-10-20
forum: General Help
---

### Post by Enishiru on 2007-10-20
Hi,

I've been using Feisty Fawn for a month or so and last night I updated to Gutsy Gibbon.

In both versions I have been having this problem:

When I attempt to switch workspaces, by using ctrl+alt+arrow or clicking on the workspace switcher or some other method, the panels and windows disappear. The only thing I can see is my desktop background.

Sometimes I am able to bring them back by using alt+tab, but usually there's nothing I can do but log out or restart.

Is there any way to fix this? Or at least some way to bring back the panels and windows every time this problem occurs?

Any help would be greatly appreciated.

---

### Post by seventyeights on 2007-10-20
I dunno, but I'd try [_resetting your desktop settings to defaults._]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

Just copy .gnome .gnome2 .gconf .gconfd and .metacity folders to a temp folder and log in again. (If this doesn't help, you can put them back.)

---

### Post by HermanAB on 2007-10-20
This is a known problem with Xfce, but Gnome should be stable.  Try KDE - it works.

Cheers,

Herman

---

### Post by seventyeights on 2007-10-20
> **HermanAB said:**
> Try KDE - it works.

Yeah. Thanks.

---

### Post by Enishiru on 2007-10-20
Am I supposed to replace GNOME with KDE? Or switch to Kubuntu?

Would I still have my data and settings?

Sorry, I'm fairly new at this.

---

### Post by seventyeights on 2007-10-20
It's generally unhelpful to tell someone to use a different program, instead of trying to fix the one currently used. Hence the wisecrack.

If you want to try resetting the gnome desktop, just do this...
1.Open your "home" folder.
2. Right click your mouse, and create a new folder.
3. Rename the folder "olddesktopfolders"
4. In the View menu, select "Show Hidden Files"
5. Move the folders .gnome .gnome2 .gconf .gconfd and .metacity into "olddesktopfolders"
6. Logout, and log back in. Or even reboot.

When gnome doesn't see any settings folders, it will automatically create new ones. 

If this doesn't work, just put the folders back (overwrite) and log in again, you should be back to where you were.

Hope it helps....

---

### Post by ulli.winter on 2007-11-06
worked for me
thanks seventyeights!

---

