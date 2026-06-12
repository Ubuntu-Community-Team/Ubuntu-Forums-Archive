---
title: "Personal Setup Script"
date: 2008-02-09
forum: General Help
---

### Post by sharpycore on 2008-02-09
Hi,
I have a habit of destroying my Ubuntu installation (7.10 AMD 64) fairly often, just through experimenting (sudo rm -rf whoops!... I'm a newbie). So I want to learn to write a script that will set everything up as I like it each time I reinstall the OS.
I have a list of some things that I haven't been able to figure out how to do myself, if anyone could tell me the files that I need to edit or commands that will do them immediately, I'd be very grateful. As for adding and removing programs, is it acceptable form to simply write the lines into the script such as:

sudo aptitude purge pidgin -y
sudo aptitude install gftp -y
etc
etc

Anyway...  the list of stuff I couldn't figure out how to script for

Set theme, background, taskbar transparency.
Set screensaver and power settings
Import my saved profile into the compiz settings manager.
Remove the icons for Help, Evolution, Switch User, Search from the top bar.
Set nautilus to list files showing name, size, owner and permissions
Turn off Play System Sounds under Sounds
Turn off Sounds under Login Window Preferences
Set terminal keyboard shortcut to  ctrl + space bar
Edit /boot/grub/menu.lst to remove "quiet splash" and "quiet"
Edit settings for apps like soundjuicer and firefox

Any any ideas are appreciated, including links to resources.
Thanks
Tom

---

### Post by pytheas22 on 2008-02-09
Yes, you should be able to write a script containing each command you want to execute, and then simply run it after a reinstall.  You would have to make sure it's executable...right click on it, select Properties, click the Permissions tab, and check the box to make it executable.

I also notice that a lot of the things in your list are related to your personal user settings, not the system configuration.  An easy way to preserve your user settings through reinstalls is to create your /home directory on a separate partition when you next install Ubuntu.  Then you can tell the partition editor to mount the same partition as /home again at the next reinstall, and as long as you don't reformat that partition, all of your settings will be reimported seamlessly.  This includes compiz settings, desktop background, nautilus preferences, Firefox bookmarks, et cetera...basically everything specific to your user account, or in other words everything you can modify without using sudo.  This works because these settings are stored in hidden folders inside your home directory--you can take a look by opening up your home folder in nautilus and pressing control-h.

You could also possibly copy your entire /home directory somewhere and copy it back onto your system after a reinstall, but I'm not sure how well this would work because you would need to overwrite the existing configuration, and I'm not sure if the system will let you do that and be able to plug in to the new configuration without a hassle.  I can attest from my experience that keeping /home on a separate partition works well, however.

The only thing is that you will get errors when you first try to log in to Gnome because some permissions will have to be adjusted, but this is easy to solve if you do a search for the error message that comes up.

I think that this will solve all of the problems in your list, with the exception of the grub modification, which I don't know how to do.

---

### Post by sharpycore on 2008-02-09
I thought about putting home on my second partition where I keep all my media, but I was worried that if I screwed up some settings irreversibly, I'd have to reinstall to overwrite /home and doing that would mean I had to reformat the partition, losing all my media too.
But thanks for the hint for where to look, I'll have a search in the hidden /home files.

---

