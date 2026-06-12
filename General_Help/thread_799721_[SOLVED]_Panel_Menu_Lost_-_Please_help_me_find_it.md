---
title: "[SOLVED] Panel Menu Lost - Please help me find it"
date: 2008-05-19
forum: General Help
---

### Post by Greasyfingers on 2008-05-19
Using Hardy Heron. I seem to have broken my main Applications menu (the one accessed from the panel). I edited the menu with the menu editor, changed my mind, and clicked on 'Revert' to restore the original layout. Now I have no Applications menu at all, and trying to open the menu editor results in a message saying 'Main Menu closed unexpectedly". Clicking on the 'Restart' button gets a repeat of the same message.

I've tried re-booting, removing the menu from the panel and re-adding it, but still no Applications menu (Places and System menus both work OK).

The menu was heavily customised, so I'd rather not start from scratch if I can avoid it; I've got recent backups of most things. Can anyone help me get the menu back, please.

---

### Post by drs305 on 2008-05-19
Removed - see solution in post4.

---

### Post by Greasyfingers on 2008-05-19
Thanks for the speedy reply.

Unfortunately, replacing ~/.gnome2 didn't get the menu back.

I have a feeling I may have broken the menu program rather than just lost the configuration file. I guess reinstalling something may help, but I've just reinstalled Alacarte and anything else that seemed Gnome menu-related in Synaptic, but to no avail.

Further suggestions appreciated.

---

### Post by drs305 on 2008-05-19
In a similar post, the user indicated:
The corrupted (empty) file was:
/home/affecteduser/.config/menus/applications.menu

Here is the thread/solution to his problem (and maybe yours):
[http://ubuntuforums.org/showthread.php?t=639457](http://ubuntuforums.org/showthread.php?t=639457)
Mostly post #2


Good luck.

I can confirm that /home/username/.config/menus/settings.menu changed when I experimented and changed a couple of menu items.

---

### Post by Cybergod on 2008-05-19
Right click on the panel and choose "Add to Panel".  Locate "Main Menu", click on it and then click "Add".

---

### Post by Greasyfingers on 2008-05-19
> **drs305 said:**
> In a similar post, the user indicated:
The corrupted (empty) file was:
/home/affecteduser/.config/menus/applications.menu


Got it!

Thanks for your help.

---

