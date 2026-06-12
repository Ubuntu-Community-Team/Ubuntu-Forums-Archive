---
title: "Startup Script Woes"
date: 2014-05-01
forum: General Help
---

### Post by 0dyss3us on 2014-05-01
I have a Ubuntu 13.10 desktop that I turned into a make-shift thin client to connect to our terminal server at work. I installed rdesktop and wrote a shell script that establishes a connection at startup and then shuts down the computer once the user logs off the remote session. I set it to the proper file permissions (711), changed the executable behavior through the file manager preferences, and added it into the Startup Applications through System Settings. It works great, but too great.

The computer started to have network issues. When I turn the computer on, I go through BIOS and the loading screen, and the script starts to run before the graphical interface ever shows up. But since rdesktop can't establish a connection, the script jumps to the next line of code and shuts the pc down immediately. 

Since I never actually see the desktop, I can't open up a terminal and use pkill to stop the script. I tried starting up in recovery mode and going into a root shell prompt, but since the file system is set to read only during recovery mode, I can't rename the script, modify it in any way, or change its file permissions. 

There has to be another way to stop this script from running so I can diagnose the network issues and make it usable again, but I'm missing it. Any ideas?

---

### Post by steeldriver on 2014-05-01
Sounds like the easiest thing would be to remount the root filesystem with read-write permissions in recovery mode

```
mount -o remount,rw /
```

Then you can do whatever needs to be done (edit / delete / move the offending script).

---

### Post by 0dyss3us on 2014-05-02
That would do it. Remounted the filesystem as read/write and then edited the shell script with a sleep command for 10 seconds before shutting down. Thank you kindly!

---

