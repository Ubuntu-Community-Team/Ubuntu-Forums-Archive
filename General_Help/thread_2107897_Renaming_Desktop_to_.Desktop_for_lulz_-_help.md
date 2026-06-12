---
title: "Renaming Desktop to .Desktop for lulz - help"
date: 2013-01-23
forum: General Help
---

### Post by Ninjex on 2013-01-23
I recently thought it would be a good idea to start hiding files and folders and encrypting things. All was going well until curiosity struck me. I wondered while I was staring at my Desktop and I was in my Desktop directory in the terminal looking at the files on my Desktop. What I was wondering was: "Hhmmm, what if I just cd to the home directory one directory back and run a sudo mv Desktop .Desktop command" So I ran: sudo ../Desktop .Desktop Making my Desktop a hidden file.

Sure enough, my Desktop disappeared right in front of me and my new desktop became my home directory. I didn't like this, as I was not excepting my home directory to be my Desktop as a result. I tried to name it back. sudo .Desktop Desktop. Unfortunately for me, it doesn't bring my Desktop back to my Desktop if that makes sense. The directory is there the way it should be, but my actual workspace is still the home directory. This is weird. Does anyone know how to fix this?
#Facepalm

---

### Post by omeomi on 2013-01-23
Open the file ```
~/.config/user-dirs.dirs
``` and edit the following line to look like this:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

After that run ```
killall nautilus
``` to restart nautilus and it should be back to the normal desktop.

---

### Post by Ninjex on 2013-01-23
> **omeomi said:**
> Open the file ```
~/.config/user-dirs.dirs
``` and edit the following line to look like this:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
```After that run ```
killall nautilus
``` to restart nautilus and it should be back to the normal desktop.

Thanks, worked like a charm!

---

### Post by mcduck on 2013-01-23
You don't need to rename files to hide them, at least if you only want to hide them in the graphical file managers.

You can instead create a text file called ".hidden", and list every file & directory you want to hide in that file, one per each line. (The .hidden file needs to be in the same location with the things you wan to hide, and doesn't support paths, so you need a separate .hidden file in each directory where you want to hide something).

Things hidden this way will still appear as normal (not hidden) files in command line, and of course some graphical file managers might not support it. But on the other hand it allows you to hide things you simply can't rename without breaking something...

---

