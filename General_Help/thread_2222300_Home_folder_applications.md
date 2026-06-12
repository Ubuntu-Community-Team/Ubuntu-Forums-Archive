---
title: "Home folder applications"
date: 2014-05-05
forum: General Help
---

### Post by mayagrafix on 2014-05-05
Some programs have installed their Folders in my Home directory (such as Lightworks, Python, Virtual Box and X-plane). Can I just create a folder called Applications and move them all in there? or will this cause the applications to stop working?

Thanks for your support.

---

### Post by sudodus on 2014-05-06
The programs will look for the settings in the (often hidden) files and directories in your home directory. It may be possible to change some setting, where a program is installed to make it look somewhere else, but it might be hard to find where to change that setting.

Another method is to move the (often hidden) files and directories from your home directory and replace them with symbolic links. This way you can keep your root partition or home partition small.

For example, I have a symbolic link ***.VirtualBox*** that points to where I have moved the .VirtualBox directory with all the VBox files (in another drive). I have also a symbolic link for ***Photos*** pointing to the Photos directory (in that other drive).

---

### Post by 3rdalbum on 2014-05-06
If the programs are actually sitting in your home directory and are usable there, then you can put them anywhere.

If you are talking about the hidden folders that all programs create in your home directory, no you can't move those. They contain settings files only. If you move them, the program will just create a new hidden settings file in your home directory.

---

### Post by grumblebum2 on 2014-05-06
If you just want to hide a folder or file in your home directory to unclutter,
you can create a **~/.hidden** file with your text editor and list one per line.
eg my **~/.hidden** file...
```
ardesia
Audio
bin
Comic-ID
conky-manager
gPodder
id.txt
libpeerconnection.log
operatransfers
src
Templates
tmp
Examples
```
The files and folders will show when you "show hidden".

---

### Post by mayagrafix on 2014-05-06
Thanks for great answers. The links are a good option and the hidden file trick works great ;<)

Where do you type "show hidden"? to get the hereto files to appear on command?

---

### Post by grumblebum2 on 2014-05-06
They behave the same as files/folders preceded by a dot
so in the browser ctrl+h to show hidden.

---

### Post by buzzingrobot on 2014-05-06
File managers typically have a "Show Hidden Files" in their View menu.  "ls -a" in a terminal will list all files including hidden files.  (Files are only "hidden" because their names begin with a '.' and the apps that deal with them are written to avoid displaying them by default.)


To find where in the filesystem the actual executable for a program resides, use "which <program name>" in a terminal.  E.g., "which firefox" displays "/usr/bin/firefox".  In Linux, more often than not, executables are in /usr/bin.

---

### Post by sudodus on 2014-05-06
Use

```
ls -a
``` or ```
ls -la
```

or select to show hidden files in your file browser.

---

