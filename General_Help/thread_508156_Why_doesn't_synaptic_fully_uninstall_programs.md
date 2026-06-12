---
title: "Why doesn't synaptic fully uninstall programs?"
date: 2007-07-23
forum: General Help
---

### Post by Ryzol on 2007-07-23
I've been messing with WINE trying to get it to install this program. I thought that since I was new to WINE maybe I had changed a wrong setting somewhere, so I marked wine for a "complete removal" and clicked apply. I then reinstalled WINE through the synaptic gui, yet WINE has not been reverted to it's default settings. What is going on here?

---

### Post by kevinlyfellow on 2007-07-23
Uninstalling apps via 'complete removal' doesn't touch the user settings.  Usually its easy enough to get rid of, just delete the wine folder in your home directory (or whatever the configuration file(s) you wish to get rid of.

---

### Post by FleetAdmiral74 on 2007-07-24
Hehe, I was wondering this too. I thought the whole point of the package management was it tracked everything for me...but I guess not :(  Back to looking around for obsolete folders taking up space... just reminds me if WIndows...

---

### Post by Ryzol on 2007-07-24
> **kevinlyfellow said:**
> Uninstalling apps via 'complete removal' doesn't touch the user settings.  Usually its easy enough to get rid of, just delete the wine folder in your home directory (or whatever the configuration file(s) you wish to get rid of.
Ahh thanks. Is this considered a feature or a bug? And since it doesn't kill user files what is the difference between "removal" and "complete removal"?

---

### Post by FleetAdmiral74 on 2007-07-24
> **Ryzol said:**
> Ahh thanks. Is this considered a feature or a bug? And since it doesn't kill user files what is the difference between "removal" and "complete removal"?

I think complete removal removes configuration files...it says that if you go and try it, where as just removal I don't think it does. Its up to you to figure out what config files they are talking about though, I'm just a newblet :)

---

### Post by kevinlyfellow on 2007-07-24
> **FleetAdmiral74 said:**
> Hehe, I was wondering this too. I thought the whole point of the package management was it tracked everything for me...but I guess not :(  Back to looking around for obsolete folders taking up space... just reminds me if WIndows...

Fortunately all of the obsolete configuration files usually don't take up much space, and are all located in the home directory.  I think the reason that it doesn't remove files like that are just in case you change your mind, or have some modifications that you made in it that you would like to keep.

Looking in my mess of configs, I have less than 100 megs of configuration (excluding .beagle, .thumbnails, and .mozilla for obvious reasons).  It's always nice to have it organized, but unless you are desperate for memory it won't be a big deal

---

### Post by kevinlyfellow on 2007-07-24
> **Ryzol said:**
> Ahh thanks. Is this considered a feature or a bug? And since it doesn't kill user files what is the difference between "removal" and "complete removal"?

Complete removal gets rid of the configuration files in /etc (the configs for all users).

---

### Post by kerry_s on 2007-07-24
you can't have it both ways, if a application is acting buggy, reinstall might fix it and you won't have to set it up from scratch, but if it did delete the settings imagine how many complaints there would be after updates, an update is just like reinstalling it removes the old app and replaces it with the new one. on like windows though you don't have to hunt down all the settings files, there all in 1 place and usually clearly marked. wine is just ".wine" you don't have to look further than that, all settings are in that 1 folder.

removal= just removes it from use
complete removal= removes the entire application, all parts.

---

### Post by FleetAdmiral74 on 2007-07-24
Well I definitely don't need the space, so I guess I don't mind just keeping em there in /home for now.

---

