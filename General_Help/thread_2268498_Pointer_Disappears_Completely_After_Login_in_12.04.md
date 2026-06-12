---
title: "Pointer Disappears Completely After Login in 12.04"
date: 2015-03-09
forum: General Help
---

### Post by patocka-c on 2015-03-09
Running 12.04 on a Dell XPS Developer Edition configured with Sputnik. On to the context. 

Here is the workflow that led to this problem.

```
sudo apt-get remove --purge xserver-xorg
```

Then I installed updates via Update Manager and rebooted my laptop only to discover a purple screen with a couple of orange dots where the login screen should be.  Realizing that I made a mistake I rebooted and opened to tty1 to re-install xserver.

```
sudo apt-get install xserver-xorg
```

Upon reboot, this brought the GUI back but I realized that there were some issues with the pointer. 

The pointer appears during the login screen but can not be moved with the trackpad on my laptop. Once I log into the device,  the pointer appears for about a fraction of a second, switches to its processing animation for another fraction of a second, and then disappears entirely.  Its important to note that the pointer is not merely invisible. When I touch the trackpad, it doesn't interact with anything on my desktop.  It's like it doesn't exist.

The keyboard works fine and I can still interface with everything through the terminal, I just don't have any mouse functionality whatsoever.

In the process of troubleshooting I went into /etc/X11/ to see if this was related to a config issue.  The directory didn't have an xorg.conf file. So I created one using:

```
sudo Xorg -configure
```

And moved it from /home to /etc/X11/

Subsequently, I've rebooted the device, but am wondering what next steps I should take in order to configure the file properly.  My knowledge of driver configuration is novice at best, and I'm not even sure I am troubleshooting correctly after a day of trying to resolve this problem.

Currently I am in the process of backing up everything to a cloud service but would prefer to try to fix this without having to wipe, install, and configure a new image. 

Thanks in advance.

---

### Post by patocka-c on 2015-03-10
After digging through Xorg arcana I pulled up Xorg_0_log in /var/log/ and discovered the following string repeating at the end of the file:

```
[COLOR=#000000][FONT=Consolas][    21.701] [dix] SynPS/2 Synaptics TouchPad: unable to find touch point 1[/FONT][/COLOR]
```

This led me to believe that the synaptics driver probably wasn't included on the previous re-installation attempt  After running:

```
sudo apt-get install xserver-xorg-input-syanaptics
```

And then rebooting, lo' and behold, pointer functionality mysteriously returned. 

Never underestimate the power of discovery enabled by breaking things.

---

