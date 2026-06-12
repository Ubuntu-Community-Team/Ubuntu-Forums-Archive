---
title: "Eclipse suddenly doesn't detect plugins"
date: 2015-01-25
forum: General Help
---

### Post by ImTroyMiller on 2015-01-25
I extracted the eclipse archive to /etc/eclipse, it contains the main eclipse.exe.  After installing the CDT plugin and some others, Eclipse was running fine except that I couldn't switch workspaces(it would just close eclipse and wouldn't automatically relaunch and when I relaunched, it would be in the original workspace).  I tried chmod +x on the eclipse.exe and I tried creating a .desktop file and doing a chmod +x on it, but no success.  I added a skin and placed the .jar into /etc/eclipse/dropins/plugins and it was working fine.


I made the mistake of removing eclipse from the launcher in an attempt to fix this.  Now when I run eclipse.exe from /etc/eclipse/eclipse.exe...
    1. No pluggins detected
    2. No skin
    3. But I can switch workspaces until I close Eclipse


When I pin the above instance of Eclipse to the launcher, close it, and relaunch from the launcher
    1. No plugins detected
    2. Skin is now there
    3. Switching work spaces just closes the program with no relaunch


It appears that the CDT plugins are in /home/user/.eclipse/org.eclipse.platform_4.4.1_808071875_linux_gtk_x86_64/plugins


How can I fix these issues?

---

### Post by ImTroyMiller on 2015-01-25
So I made a copy of the entire folder located at /etc/eclipse in /home/user/ and then I copied all of the files in /home/user/.eclipse/org.eclipse.platform_4.4.1_808071875_linux_gtk_x86 _64/plugins to /home/user/eclipse/plugins.  When I run the eclipse.exe in my copied folder, everything works perfectly(it detects the CDT, I can switch work spaces without problems, the skin is detected) except that when I pin it to the launcher, close Eclipse and reopen, it no longer detects the CDT.  Also my Java paths are askew.

---

### Post by ImTroyMiller on 2015-01-25
This seems to have fix these problems entirely.

Until next time...

---

