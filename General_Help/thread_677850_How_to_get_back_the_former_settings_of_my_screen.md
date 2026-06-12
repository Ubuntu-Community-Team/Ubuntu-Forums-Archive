---
title: "How to get back the former settings of my screen?"
date: 2008-01-25
forum: General Help
---

### Post by LarsRoan on 2008-01-25
Some days ago I succeded to install ubuntu for the first time.  I have an WinXP but by Innotek's Virtual Box I managed to start up and get my first experiences with Linux by Ubuntu 6.10.  

But I was not satisfied with the quality of the screen.  By the settings I found a list of producers and selected Eizo (as I have - M1900).  Then I was told that I had to restart to activate the settings.  After that the whole screen is just a mix of lines?  I don't even see the fields for username and password.

Any idea how to jump back to the former settings? I still have the "VM - Devices - Help" - menu as you can see [here]("http://www.virtualbox.org/attachment/wiki/Screenshots/ubuntu-on-xp.png"), but not the Ubuntu screen, just a lot of mixed colours.   I didn't expect this to happend.  Any idea how to get back the standard settings, or is a reinstallation the easiest alternative?

---

### Post by dcstar on 2008-01-25
> **LarsRoan said:**
> Some days ago I succeded to install ubuntu for the first time.  I have an WinXP but by Innotek's Virtual Box I managed to start up and get my first experiences with Linux by Ubuntu 6.10.  

But I was not satisfied with the quality of the screen.  By the settings I found a list of producers and selected Eizo (as I have - M1900).  Then I was told that I had to restart to activate the settings.  After that the whole screen is just a mix of lines?  I don't even see the fields for username and password.

Any idea how to jump back to the former settings? I still have the "VM - Devices - Help" - menu as you can see [here]("http://www.virtualbox.org/attachment/wiki/Screenshots/ubuntu-on-xp.png"), but not the Ubuntu screen, just a lot of mixed colours.   I didn't expect this to happend.  Any idea how to get back the standard settings, or is a reinstallation the easiest alternative?

/etc/X11/xorg.conf is the file that contains the X settings, there may be a backup file in that directory that you can use to replace the bad xorg.conf file.

---

