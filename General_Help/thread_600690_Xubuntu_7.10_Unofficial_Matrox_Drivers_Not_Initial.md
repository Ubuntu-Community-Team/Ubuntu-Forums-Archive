---
title: "Xubuntu 7.10 Unofficial Matrox Drivers Not Initializing"
date: 2007-11-02
forum: General Help
---

### Post by mr_gerbik on 2007-11-02
Hello,
I've tried loading the unofficial matrox drivers ([http://matrox.tuxx-home.at/viewforum.php?f=1](http://matrox.tuxx-home.at/viewforum.php?f=1)) using the installer and the manual method, which install to /usr/lib/xorg/modules/drivers

Now when I try to run the installer script, it outputs that the drivers are already installed.

glxgears gets about 60 fps. on ubuntu 7.04 it got 500+. So it would appear that the drivers have not in fact installed or otherwise detected as such.

Backtracking a bit, at one point in trying to install the drivers, after running the installer for the -first- time, I made the mistake of extracting the unofficial drivers to a dir, renaming each of the files from ex mga_drv.so to mga_dri.o (For all four files). Then I created a dir where none previously existed (/usr/lib/dri/) then placed the renamed files into that directory. I did this because before doing so, xorg.log had (EE) saying that the files in (/usr/lib/dri/) weren't found.
Now I'm getting a different (EE) in the same place in the log file.

Attached files are current.

---

### Post by mr_gerbik on 2007-11-02
$ sudo apt-get install libgl1-mesa-dri

This command seemed to work. glxgears is now 10x what it was. (300FPS).

Is there anyway to improve this further?

---

