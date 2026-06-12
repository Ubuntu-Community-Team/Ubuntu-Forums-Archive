---
title: "Trouble setting up system sounds"
date: 2018-03-08
forum: General Help
---

### Post by maindux on 2018-03-08
Hello,

Recently, I’ve been playing with system sounds on xubuntu 17.10 (as niceties for my younger sister, who hasn’t much experience with anything but macOS and older versions of Windows). It’s gone pretty well overall: I have all the dialog sounds, some battery charge notifications, hardware insert and remove, and a login sound. 

The problem is in two places: logout sound and network status sounds.

Optimally, I would like to have the logout sound play whenever XFCE exits, either back to the login page or when shutting down and restarting. I have managed to get it to work for exiting to the login screen, but not shutdown or restart. 

The current setup is: init.d script with symlinks in rc0 and rc6 prefixed with K99. However, the sound still won’t play. My best guess right now is that pulse audio is stopping before it can play the sound, and I’m not sure how to fix that. 

As for the network sounds, I have no idea how that would be implemented. 

Here’s my init.d script:
```
#!/bin/bash
echo “Attempting to play shutdown sound...”
pulseaudio --start
/usr/bin/play /usr/share/sounds/custom/stereo/desktop-logout.ogg
sleep 2
```

Any help would be greatly appreciated!

---

### Post by maindux on 2018-03-09
Hello again,

I managed to get the network connection and disconnection sounds up and running by putting scripts in /etc/network/if-up.d and if-post-down.d/

I&#8217;m still not sure about how to fix the shutdown/restart sound though.

EDIT: Right after I posted this I saw a post in a different forum about needing start() and stop() functions with a lock file in order to run a script at shutdown. I&#8217;m not sure how I would implement that in this case, so if someone could elaborate on how the process works, I would appreciate it.

---

### Post by kerry_s on 2018-03-09
you can change the logout command to call a script instead, with something like

xfce4-session-logout && play /usr/share/sounds/custom/stereo/desktop-logout.ogg

that way you can control whats called.

just tested it a bit, but couldn't get the sound to wait for logout dialog to finish. it kept playing at the same time as the dialog showed & screen dimmed. :(
[ATTACH=CONFIG]278882[/ATTACH]

---

