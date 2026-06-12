---
title: "Installing Dolphin broke file management"
date: 2024-04-14
forum: General Help
---

### Post by cbiweb on 2024-04-14
[COLOR=#b22222][SIZE=3]**EDIT:  I reinstalled.  Too much was going wrong.**[/SIZE][/COLOR]

I installed Ubuntu months ago but did nothing with it until the past couple days as I've started transitioning from Windows. It is fully updated at this point.

Today I installed Dolphin, and now I can't access these folders:
[LIST]
[*]Desktop 
[*]Music 
[*]Pictures 
[*]Public 
[*]Templates 
[*]Videos 
[/LIST]

I had installed Dropbox a few minutes before that.

The desktop screen is also populated with shortcut icons with an x in the lower right corner, which of course are inaccessible.

A reboot didn't fix it.

So I uninstalled Dolphin, and rebooted again.

No change.

Is there way to fix this, or do I need to reinstall?

My apologies for not including other information that you might need to know, but I don't know what you need to know, lol.

TIA for any help/suggestions.

---

### Post by TheFu on 2024-04-14
Check the system logs for errors and warnings.  It is unlikely that a reinstall is needed, but it may be the fastest way back to a system you expect. If you have done a few installs, you know that is a 10-15 minute effort, then you'll want to put your data and settings back.

You didn't say which version of Ubuntu.  I hope 22.04.x.  Isn't Dolphin a Qt app?  If you want that, perhaps Kubuntu is more to your liking?  It uses the Qt libraries for all the default installed programs, not the GTK+ libraries.

You can google for "ubuntu logs 22.04" to find how to get to the logs if you don't already have a method. Always include the release version in your web searches to avoid old information.

---

### Post by iniyaan-epic on 2024-09-13
Hi everyone,
 

 
 I encountered an error and have found a solution tto revert it for me. Here&#8217;s a step-by-step guide on how to fix it:
 **1.****Uninstall Dolphin: **If Dolphin was installed, remove it.
 **2.****Remove Broken Symlinks: **Clear out any broken symbolic links.
 **3.****Recreate Default Directories: **Use the following command to create the standard user directories:
 	mkdir Desktop Downloads Templates Public Documents Music Pictures Videos
 **4.****Update the user-dirs.dirs Configuration File: **Open the configuration file with nano:
 nano ~/.config/user-dirs.dirs
 Ensure the file contains the following lines:
     # This file is written by xdg-user-dirs-update
     # If you want to change or add directories, just edit the line you're
     # interested in. All local changes will be retained on the next run.
     # Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
     # homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
     # absolute path. No other format is supported.
     #
     XDG_DESKTOP_DIR="$HOME/Desktop"
     XDG_DOWNLOAD_DIR="$HOME/Downloads"
     XDG_TEMPLATES_DIR="$HOME/Templates"
     XDG_PUBLICSHARE_DIR="$HOME/Public"
     XDG_DOCUMENTS_DIR="$HOME/Documents"
     XDG_MUSIC_DIR="$HOME/Music"
     XDG_PICTURES_DIR="$HOME/Pictures"
     XDG_VIDEOS_DIR="$HOME/Videos"
 

 
 **5.****Save and Exit: **Save the changes and exit the editor.
 

 
 **6.****Log Out and Log Back In: **Log out of your session and log back in for the changes to take effect.
 

 
 Following these steps should resolve the issue. I hope this helps!

---

