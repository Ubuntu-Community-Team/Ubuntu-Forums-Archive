---
title: "Super Post Installation Script"
date: 2007-11-25
forum: General Help
---

### Post by thinsoldier on 2007-11-25
I heard you can't do certain things in the ubuntu install cd due to legal reasons.
But after installation the user can do whatever they want.
Why not build some sort of web based application that a user can visit and choose features that aren't installed by default and then it generates a massive shell script that does everything necessary to install whatever is needed to enable those features.

Here's what I need:

Ability to connect to Windows & OS X servers (most important)

Ability to open/execute files as root from the context menu (nautilus-gksu) (HUGE time saver)

install archive program (with a GUI) capable of extracting zip, rar and everything else (important)

install something capable of mounting bin/cue, iso files (important)

Install microsoft core web fonts

install codecs for all known audio and video formats

install media players capable of playing everything else

Install zsnes and run a configuration script that asks where on my windows drive my roms and save files are so I don't have to copy everything over to linux to play (**waste of space & duplication of content**)

Configuration script that asks for any video games I have installed in windows that have a linux version and then it downloads the linux executables for those games and sets it up so I don't have to copy all the files from my windows drive to linux to play them (**waste of space & duplication of content**)
* alien arena
* mame
* open arena
* quake
* quake 3
* tremulous
* unreal tournament
* unreal tournament 2004
* unreal tournamen 3
* warsow
* zsnes

Configuration script that asks where on my windows drive my apache webroot folder and mysql database storage folders are and updates apache/mysql so I don't have to copy those files from my windows drive (**waste of space & duplication of content**)

Because I'm probably going to still dual boot windows for the next 2 years and windows can't read linux partitions there should be a step in the installation process that asks me where on my windows drive to use as linux's /home directory.

---

### Post by hikaricore on 2007-11-25
I'm not going to even respond to most of what you posted as it's silly and would only pertain to a niche audience (probably mostly you).  However...

> **thinsoldier said:**
> Because I'm probably going to still dual boot windows for the next 2 years and windows can't read linux partitions there should be a step in the installation process that asks me where on my windows drive to use as linux's /home directory.

First there's a ***dows driver for this. [http://www.fs-driver.org/](http://www.fs-driver.org/)

Second of all, as for using an ntfs/fat32 drive for your home dir.... NO this would be a catastrophe.

---

### Post by PeterJS on 2007-11-25
> **hikaricore said:**
> I'm not going to even respond to most of what you posted as it's silly and would only pertain to a niche audience (probably mostly you).

Yeah pretty much, reading over this the first thing that came to mind was Automatix, which was a good (that's debatable) idea in theory, but in practice was a massive disaster that caused lots of system instability and broke upgrades. There's a reason nobody uses it anymore. That said is there really anything can't be solved with the restricted extras package, medibuntu, and ten minutes worth of work. And to cap it all off, would you expect windows to detect a Linux or Mac OSX and do the same?

---

### Post by hikaricore on 2007-11-25
I'll be really nice just this once and post the best link you could ever hope for.  ^_^

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Enjoy.

---

### Post by aysiu on 2007-11-25
You're probably best off creating your own post-installation script.

Just do a fresh installation, keep track of (by putting inside a text file) every command you enter to tweak things, then make it a bash script by putting ```
#!/bin/bash
``` at the beginning of the text file and then making the file executable: ```
chmod +x nameofscript.sh
```

---

