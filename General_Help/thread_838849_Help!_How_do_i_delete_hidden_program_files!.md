---
title: "Help! How do i delete hidden program files!"
date: 2008-06-23
forum: General Help
---

### Post by eival on 2008-06-23
i have an issue with Ktorrent, i installed the Settings plugin and made 1 change(i put a bunch of 9999999's in one of the colums thinking this would automatically tell the program to set to "max" but obviously this program is stubborn), then it closed automatically and the KDE crash handler poped up, i have know idea what "backtrace" is for, so i closed it and tried to reopen it, it kept closing down, then i uninstalled it via Add/Remove, reinstalled it, an i can use it, but now it crashes when i try to add the plugin.

so that tells me, theres something that was left on my HDD after i uninstalled via Add/remove...i thought i was done with Windows =/


my question is,
how do i find/delete the files that are hidden somewhere in my HDD so i can use a fresh install of Ktorrent?

---

### Post by VMC on 2008-06-23
> **eival said:**
> i have an issue with Ktorrent, i installed the Settings plugin and made 1 change(i put a bunch of 9999999's in one of the colums thinking this would automatically tell the program to set to "max" but obviously this program is stubborn), then it closed automatically and the KDE crash handler poped up, i have know idea what "backtrace" is for, so i closed it and tried to reopen it, it kept closing down, then i uninstalled it via Add/Remove, reinstalled it, an i can use it, but i still want to make changes in the Settings plugin, but it still crashes.

so that tells me, theres something that was left on my HDD after i uninstalled via Add/remove...i thought i was done with Windows =/


my question is,
how do i find/delete the files that are hidden somewhere in my HDD so i can use a fresh install of Ktorrent?

Regarding the question about clearing the hard drive. Boot up using livecd then go to Terminal and type ```
sudo gparted
``` Then delete any and all partitions. Reboot and install kubuntu . You did say you wanted a fresh install, correct?

EDIT: I [COLOR="Red"]was assuming you were NOT dual booting of course! And the only OS that you want on your computer is Kubuntu[/COLOR].

 [I use gdisk from a dos prompt and type "gdisk 1 /del /all". I'm not sure of the Windows fdisk command that does the same]

---

### Post by cwbar_1 on 2008-06-23
I'm not sure if this is exactly correct or not.  (I use gnome)  Open your file browser and go to the "view" tab.  There should be a "Show hidden files" selection.  You would then need to find your file, right click and select properties.  You would then need  change the permissions to allow you to delete it.  (ownership)
Once again, not using KDE, I may not be totally correct, but I hope this helps.

---

### Post by molotov00 on 2008-06-23
I'd try uninstall via command line:

sudo apt-get purge ktorrent #to get rid of ktorrent and delete old package
sudo apt-get autoclean #to delete unused dependencies

Then I'd take a look in the home directory for ktorrent files. Most apps will create a folder preceeded by a period (.). Some file managers hide these, in Xubuntu I need to click 'View' then 'Show hidden files'. Or you can 'ls -a' via command line.

If there's a .ktorrent folder or something similar (that was created by ktorrent obviously) then delete it.

Install ktorrent.

sudo apt-get install ktorrent

EDIT:

I was feeling particularly helpful and downloaded/installed ktorrent. It's temp files are stored in:

~/.kde/share/apps/ktorrent/
~/.kde/share/config/ktorrentrc
~/.ktorrent.lock

So, delete those folders, i.e.:

sudo rm -r ~/.kde/share/apps/ktorrent/ # repeat for other folder/file

Note that rm -r is a dangerous command. It will delete everything in that folder.

Rest of instructions are unchanged. I can also confirm that .kde/share/apps/ktorrent is not deleted even after running apt-get remove. There may be other files left over but I couldn't find any.

---

### Post by eival on 2008-06-24
thanks alot molotov, ill try those steps out an reply back with the results.

---

