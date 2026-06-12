---
title: "Getting the updater to leave me alone? Running an older Wine."
date: 2006-10-29
forum: General Help
---

### Post by Kalinda on 2006-10-29
Hello,

I'm running an older version of Wine so I can use IE6 with the WMP plugin to watch streaming .asx videos flawlessly for my history class, since they don't work properly in anything else (I've tried). IE is broken on the newest Wine and I'm not sure if there's a way to fix it.. there doesn't seem to be, since everyone keeps saying to just use IE4Linux.

However, Adept Updater won't stop bugging me to update Wine and it sits down there in the system tray glowering at me with its lil' orange box icon and big exclamation mark. I don't want it there all the time because I will eventually get used to it and miss out when real updates are ready to be installed.

Yesturday I tried, with the help of someone on the IRC channel, to fool the system with some hacking. I edited the /var/lib/dpkg/status and told it the version I had was the latest.. but it didn't believe me and Adept is still there. What I did didn't appear to have any lasting effects, either. Maybe I should change it back to be safe?

I also tried locking the version in Synaptic, since that's what I use, but that wasn't helpful.

Is there a way I can make it leave me alone, tell it I don't want to install a newer Wine so it'll stop trying to make me update?

---

### Post by beerfan on 2006-10-29
The ability to select packages which aren't desired and hide or disable them would be nice. Windows Update has this capability with optional updates. Maybe you should submit a bug/enhancement request for it.

I'm sorry that I don't have any tips for solving your immediate problem.

---

### Post by Kalinda on 2006-10-30
Alright, I'll do that :) Thanks.. I'm probably going to have to update it anyway, seeing as how it seems to have stopped working with the videos.. and I wanna get Photoshop to run, but my version is too old.

Thanks for the advice, though.

---

### Post by cmost on 2006-10-30
Pin the package version you want to keep in /etc/apt/preferences.

Here's a brief howto; checkout Google or the Man pages for Apt for more information:

preferences

The next step is to create/edit your /etc/apt/preferences file. preferences is where the apt-pinning takes place. Normally, the highest version of an available package wins, but we will override that.

A simple preferences file may look like this:

Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650

Package: *
Pin: release a=unstable
Pin-Priority: 600

Note the decending values. Since Stable has the highest pin-priority, it will be installed preferentially over Testing or Unstable (you can set this for any repository, this example assumes pure Debian.)

---

