---
title: "Purge Font, Extra Special Problem"
date: 2015-04-05
forum: General Help
---

### Post by cathect2 on 2015-04-05
I have a font I want to remove.

I went into /home/.fonts and deleted the font file. Rebooted. But it was still a in the system. 

So I went into usr/share/fonts and deleted it there. Rebooted. But it was still in the system.

So I looked into usr/local/share/fonts and nothing was there.

Searched in nautilus for the font by name. Nothing.

Where is this font?

---

### Post by deadflowr on 2015-04-05
What's the font?
Perhaps it is part of a font package.
What it pre-installed, or did you add it yourself?

---

### Post by ajgreeny on 2015-04-05
Run command **sudo fc-cache -f -v** in terminal to update the font cache database; that might do it for you.

---

### Post by cathect2 on 2015-04-05
Well, the command was not successful. I did get an "invalid cache file" error at the end of the process, however. 

The font is Andada.

I'm stumped.

---

### Post by buzzingrobot on 2015-04-05
Is there a '.local/share/fonts' folder in your home directory?

---

### Post by cathect2 on 2015-04-05
YES! Buzzingrobot, you are the man! (or woman!). Good call on that location. 

My question: why are there so many locations were fonts are stored? It makes sense to me to have system fonts separate from user ones. But why are there so many locations? I thought I'd found all of them until you mentioned .local/share/fonts. Should be much easier to nuke a font that is causing you problems...

---

### Post by buzzingrobot on 2015-04-05
Believe the standard location for font files, and where their configuration tools expect to find them, has changed over the years.  It can take a long time for existing software to catch up, so the other locations work until someone finally pulls the plug. As far as I know, any font package installed with the package manager (apt-get, Synaptic, Software Center, etc.) deposits the files in /usr/share/fonts. 

If fonts are in the user's home directory, they won't be available to other users on the same system.  And some folks maintain their home directory on a separate partition.  This allows them to install to a new distro release version (say, 14.10 to 15.04) and preserve their home folder and all the configuration tweaks, etc. in it by telling the installer's partitioner to avoid repartitioning and formatting it. So, any fonts they've installed in home would be retained.  That would not be the case for anything in /usr/share/fonts. 


If I manually add fonts, I add them to /usr/share/fonts, and add the names to the list of 'add-ons' I keep. If I do a re-install or a new install, I can quickly re-install those packages.  Things from places like Google Fonts that aren't in the repos I stash on Dropbox.

---

### Post by ian-weisser on 2015-04-05
> **cathect2 said:**
> I went into /home/.fonts and deleted the font file. Rebooted. But it was still a in the system. 

> **cathect2 said:**
> why are there so many locations were fonts are stored? It makes sense to me to have system fonts separate from user ones.

Buzzingrobot is right. The location for user fonts changed a while back.
~/.fonts is the old location
~/.local/share/fonts is the new(er) location. The hierarchy matches /usr/share/fonts.

You'll find all kinds of interesting stuff if you wander through ~/.local

---

