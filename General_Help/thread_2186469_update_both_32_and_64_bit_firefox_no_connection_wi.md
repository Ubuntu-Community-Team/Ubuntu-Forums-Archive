---
title: "update: both 32 and 64 bit firefox no connection without proxy on 64bit ubuntu 12.04"
date: 2013-11-07
forum: General Help
---

### Post by johnsonttc on 2013-11-07
hi all

i found this problem a month ago, and not until then i realized i was running a 32bit firefox before
here are the details about the problems:

- with a 32bit firefox, i am able to surf the internet, with or without a proxy resides on the same machine
- with a 64bit firefox, i have NO internet access if not via proxy, although local network can be accessed without problem

note that:
- i have my ubuntu updated
- no problem with the network settings or such, or otherwise the 32bit firefox wont be able to go online
- same results for 64bit firefox binaries downloaded from mozilla.org
- not just firefox 24 or 25 only but other releases as well
- removed/reinstall firefox and tested with new profiles but didnt help


some more info:
- i have installed some i386 libs on my linux box as to build android stuff
- uname -a: 3.2.0-55-generic #85-Ubuntu SMP Wed Oct 2 12:29:27 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


attached is a screen shot showing both 32bit and 64bit firefox side by side with newly created profiles and without proxy connection

hope that someone can help to fix this problem, thank you

PS just tell me if more info is needed

---

### Post by tgalati4 on 2013-11-08
Burn a LiveDVD of 64-bit 12.04 and boot off of it.  Make sure your internet is connected and open firefox in the Live Session.  If it works, then you know you have an issue with your installation and not a 32-bit vs 64-bit CPU/execution problem.

If the Live Session firefox works, then I would suspect some 32-bit library or a symbolic link that got created which points a critical library to the 32-bit version.  This may have happened with the Android SDK installation.  I would look for an installation log to see exactly what got installed and what symbolic links got created.  You could search by date if the Android library files all have similar creation dates.

---

### Post by johnsonttc on 2013-11-08
thanks for your reply

yeah, i suspect it is the lib files causing the problems too. however, i don have any clue about where to look for the problems. since it was installed for nearly a year, it is not possible to look at the file timestamps only to find out the changes for the reason that there were quite a lot of patches installed as well. also, as it is a server, reinstalling the whole system is not an option at the moment

---

### Post by tgalati4 on 2013-11-08
Look at /var/log/apt and /var/log/installer for installation log files.  Perhaps you can piece together what happened.

---

### Post by johnsonttc on 2013-11-08
thanks, will take a look at the log files later, and perhaps i will need to do objdump to find out the dependencies as well

---

### Post by johnsonttc on 2013-11-09
well, i think it is better for me to switch to 32bit firefox for too many things need check

---

### Post by johnsonttc on 2013-11-12
update:

i switched to 32bit firefox several days ago, but then since yesterday, it didnt have connection if set to no proxy also!

what's wrong???!

---

