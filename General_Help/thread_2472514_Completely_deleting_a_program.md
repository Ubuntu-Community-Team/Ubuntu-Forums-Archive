---
title: "Completely deleting a program?"
date: 2022-03-01
forum: General Help
---

### Post by Autodave on 2022-03-01
Recently, I had to reinstall Xubuntu.  No big deal.  Everything was backed up except a couple of games.  Supertuxkart was not backed up.  After getting Xubuntu 20.04 installed and updated fully, I installed STK.  However, I get a message when I open the game telling me that it has no internet access.  I have tried deleting it and reinstalling, but same prob.  I go into Synaptic and choose to completely remove everything including configuration files.  Reboot.  Reinstall game.  Same problem.  However, the configuration files (?) were not removed because my high scores are still there from the previous installation.  How can I remover everything and try a reinstallation?

---

### Post by The Cog on 2022-03-01
Your personal files for the game (settings, preferences, scores etc.) will be stored in your home folder, and not removed by uninstalling the application from the system. Look for a folder with a fitting name, maybe hidden in yoru home folder (~/.supertuxcart for instalnce), or in the hidden config folder (~/.config/supertuxcart for instance). In case you want to bring  those settings back, you could just rename the folder for now.

---

### Post by deadflowr on 2022-03-01
There should be two supertuxkart folders in Home.
One in ~/.config and the other should be in ~/.local/share.
Try deleting those.
apt never removes anything from Home.

---

### Post by Impavidus on 2022-03-01
> **The Cog said:**
> Your personal files for the game (settings, preferences, scores etc.) will be stored in your home folder, 
I don't know about STK, but some games store score files system-wide somewhere in /var in a group-writable file in the games group. The game itself has setGID games, to it can edit the score file for all users. I don't know if such score files are removed by apt purge, although I expect they will.

---

### Post by Autodave on 2022-03-01
Thanks for the help.  I deleted the game and those 2 folders, reinstalled, still same problem though.....game says that I an not connected to the internet or my firewall is blocking the game.  Sigh.

---

### Post by #&amp;thj^% on 2022-03-01
> **Autodave said:**
> Thanks for the help.  I deleted the game and those 2 folders, reinstalled, still same problem though.....game says that I an not connected to the internet or my firewall is blocking the game.  Sigh.

Autodave if your up for it, try: [https://launchpad.net/~stk/+archive/ubuntu/dev?field.series_filter=disco](https://launchpad.net/~stk/+archive/ubuntu/dev?field.series_filter=disco)

---

