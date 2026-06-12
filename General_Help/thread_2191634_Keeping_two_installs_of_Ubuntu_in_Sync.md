---
title: "Keeping two installs of Ubuntu in Sync?"
date: 2013-12-03
forum: General Help
---

### Post by gregory12 on 2013-12-03
I would like to keep my desktop and laptop install in sync as much as possible.
I saw that the app center can keep the installed apps in sync.
But what about everything else? Ideally I would like to setup the desktop, clone the install on the laptop and then whatever I change on each to sync to the anoher, that would be not only apps and files but settings and so on.

Is it possible and is it a good idea actually? Potential problems?
How much of my changes actually are saved outside of my home folder?
what if I export a backup on the desktop and import it on the laptop, would that be a good idea? :)

Many questions I know, but i'm totally new.

---

### Post by gregory12 on 2013-12-04
the title should be "Keeping two installs..."

---

### Post by philinux on 2013-12-04
Moved to general help forum.

It's the oneconf service that does syncing but I've not used it.

Title fixed too.

---

### Post by gregory12 on 2013-12-06
yeah that seems to be what i need, lets see if someone has used it and can share his experience :)

---

### Post by ian-weisser on 2013-12-06
If you just want to keep your data uniform between two machines, there are many services that do syncing:
Ubuntu One and Google Drive are two common ways.

If you want to roll-your-own script, there is good old rsync and ssh: [http://stackoverflow.com/questions/1602324/rsync-how-do-i-synchronize-in-both-directions](http://stackoverflow.com/questions/1602324/rsync-how-do-i-synchronize-in-both-directions)

---

### Post by vanadium on 2013-12-07
If it concerns two installations of an identical Ubuntu installation, mirrorring your entire home directory between the two systems should be perfectly safe. I am not sure how you could automatically keep the installed software in sync, but this is something that does not change quickly anyway. If you installed software on one machine, and notice it is not yet there on the ohter machine, you can just install it: the settings will already be there from the other machine.

---

### Post by gregory12 on 2013-12-07
ok OneConf (which seems to just be setting in the ubuntu software centre?) seems to take care of syncing the installed apps.
So if I just sync the home folders as well i should have identical installs right?

is there anything else outside of the home dir that changes? (and that the software centre sync won't take care of?)

Also  what if i export the backup from the first computer to ubuntu one and  the import it to the second one? Would that mess anything?

---

### Post by ian-weisser on 2013-12-07
Any manual changes to /etc won't be synchronized. Like custom Upstart jobs or network settings or cron jobs or udev rules. 
Any changes to /var (logs, caches, etc) won't be similar. And generally shouldn't be similar.
Do you want the machine names to be identical?
If you clone udev rules for specific hardware across two installs, you get a bit of a mess.

So it depends what you want to sync, and what you want to backup/restore.

---

### Post by NTL2009 on 2013-12-07
If the OP uses Oneconf, I think he will still need to run updates from the second computer, right? Like for kernel  updates?

-NTL2009

---

### Post by gregory12 on 2013-12-10
well basically i will need synced the apps, their settings and data (I  suppose all of those are in the home folder?) and if possible the  customization of ubuntu, like themes, tweaks and stuff like that but  that's not critical.
for the first two i suppose the setting in the app center and syncing the home folder would be enough, right?

---

### Post by ian-weisser on 2013-12-10
Application data is usually in your home folder.
Application settings are often (not always) in your home folder. Some applications keep settings in live databases (like gsettings) instead of static config files.
Applications are almost never in your home folder. The installed applications are in /bin, /sbin, /usr/bin, /usr/sbin, and many other possible places - mostly owned by root (not you). To sync application versions like that on a Debian system, your should simply be ensuring you keep the same package versions.
Many customizations settings are in your home folder, others may be scattered among gsettings, /etc, environment variables, and other places.

---

### Post by gregory12 on 2013-12-12
i see, well i have a much better idea of it now, thank you all!
i'll be using the app centre sync and home folder syncing with 3rd party tool
hopefully it won't mess anything :)

---

