---
title: "Reverting to Nautilus as the default filemanager"
date: 2015-08-08
forum: General Help
---

### Post by James_Wood on 2015-08-08
I'm having an issue reverting back to Nautilus after testing Nemo and  Dolphin as alternate File Managers using Trusty Tahr.

I initially installed Dolphin and set it as the default manager according to the steps laid out here:

[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

initially by editing **defaults.list** in **~/.local/share/applications**

then by editing **defaults.list** in **/usr/share/applications**

as changing the filemanager at the local level still left Nautilus functional in certain places.

After some testing I decided to switch to Nemo, so firstly I reversed the above mentioned steps and removed Dolphin.  At this stage I was not thorough enough in my testing to ensure that things had been properly reverted, which it seems they weren't.

I then installed Nemo and set it as default according to these steps:

[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

After testing this, I changed my mind again and decided to go back to Dolphin, so I reversed the procedure again removing Nemo from the system.

At this point it became apparent that traces of Dolphin were still present on the system, yielding this error:

Failed to execute default File Manager.

Failed to execute child process "Dolphin" (No such file or directory)

I have managed to fix the situation by editing every file that I know pertains to the filemanager, but I am left with one instance of the error when I try to open an article in RSSOwl.

Does anyone have idea what file(s) need to be edited to tackle this issue?

---

### Post by v3.xx on 2015-08-08
For testing, no real need to add and remove file managers one at a time.  I have ran 3 or 4 without conflict, you should be able to do the same.

Also if you just want to play with different file managers without setting them as default, just install without any configuration.  example:
```
sudo apt-get install nemo
```
This will add nemo to my menu and if I wish, create a launcher.  Leaving the default configuration untouched.  The same command works with other file managers.

About your current problem with dolphin.  Try purging it then reinstall.  This will remove the configuration files.  You will need to manually remove any configure files (hidden file .config or other?) in your home directory. and reinstall, as said for testing purpose you can just install it like any other package.
```
sudo apt-get remove --purge dolphin && sudo apt-get install dolphin
```
This will hopefully get you back on track.

And welcome to the forums :)

---

### Post by James_Wood on 2015-08-08
I was aware multiple file managers could be installed at once, there were specific reasons I wanted them set as default.

Do you have any idea what folders are should look for specifically to remove the config files?  I'm still getting to grips with the file structure.

I'm not particularly bothered about returning to Dolphin as I've found out how to edit the Nautilus source code to achieve what I want.

Through further use I've found another couple of applications throw up the error, in Deluge for instance it occurs when I try to open a containing folder, though this doesn't occur in the Launcher or VLC, which makes me think it may be application specific.  I've checked the respective .desktop files but can find no clue.

Thanks for your speedy reply, I'll try using the --purge command, and see where I get.  Also for the welcome, I doubt this will be final post as I'm nothing if not a tinkerer.

---

### Post by v3.xx on 2015-08-08
> Do you have any idea what folders are should look for specifically to remove the config files? I'm still getting to grips with the file structure.
No, not really.  I do not have it installed.  The only config files (hidden file) not removed by the purge command are located in your home directory.
This may help you with the file structure(home not listed).
[http://packages.ubuntu.com/trusty/amd64/dolphin/filelist](http://packages.ubuntu.com/trusty/amd64/dolphin/filelist)
Good luck :)

---

### Post by CantankRus on 2015-08-08
Check default file manager....
```
xdg-mime query default inode/directory
```

To set as nautilus...
```
xdg-mime default **nautilus.desktop** inode/directory application/x-gnome-saved-search
```
**xdg-mime** appears to work with the **~/.local/share/applications/mimeapps.list** file. Search for "inode/directory".

Also check **/etc/gnome/defaults.list** for system defaults and
**/usr/share/applications/mimeinfo.cache** for "Open With" items.

**~/.local/share/applications/mimeapps.list** overrides **/etc/gnome/defaults.list** for the user.
ie if you move or rename **~/.local/share/applications/mimeapps.list** you should revert to using  **/etc/gnome/defaults.list**

---

### Post by James_Wood on 2015-08-13
Okay so the **--pu****rge **command didn't work as I've already uninstalled dolphin, the problem seems to be a trace of something that's been left somewhere on account of me being a noob.  I'm going to check through the link you sent for the file structure details.

---

