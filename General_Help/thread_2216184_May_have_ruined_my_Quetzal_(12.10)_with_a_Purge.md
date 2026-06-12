---
title: "May have ruined my Quetzal (12.10) with a Purge"
date: 2014-04-10
forum: General Help
---

### Post by hylianhal2 on 2014-04-10
I was trying to find a method for running BrawlBox through Wine, and decided I should try uninstalling Wine and Winetricks. 

However, after uninstalling, there were signs that Wine was still present. Googling the issue turned up someone else with a similar issue, which led me to a command line post that seemed like the solution to my problems.

..purge/*

Looking back, that command is ominous as hell, and I shouldn't have messed with it, not being very familiar with it or Wine. The user's warning was to 'be careful, since this will purge the system of everything related to Wine' or something to that effect.

"Sounds great," I thought.

I wasn't really concerned until I noticed the GUI being affected. Trying to close out the command line wasn't working, so I panicked and shut down the laptop.

Upon booting, the GUI's borked, the side launcher is gone, and shortcuts are unresponsive.

Is there ANYTHING I can do, before resorting to wiping it and installing another distro?

---

### Post by grahammechanical on 2014-04-10
My advice? Re-install and do it with a version of Ubuntu that is not about to run out of support - 12.04 or 14.04 when it is released in a few days time.

Who knows what you purged with that command. The asterisk ( * ) is used in commands as a wildcard to represent any and all characters in file names. So, putting the asterisk after a forward slash ( / ) is the same as saying everything after the slash.  For example Documents/* would refer to everything in the Documents folder and any command that was used would do what the command does to every file in the Documents folder. Who knows what you purged?

Regards.

---

