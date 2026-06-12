---
title: "Cannot log into Budgie 20.04 after stopping Nvidia driver installation"
date: 2020-04-19
forum: General Help
---

### Post by voidpls on 2020-04-19
(Yes, I realize 20.04 is a beta build)

So earlier today I installed Lutris to try my luck at playing some Windows games, and had installed all its dependencies and etc. However, I was having a problem with a black screen whenever a game was fullscreen, so I tried to do a bit of troubleshooting. Eventually I got around to downgrading my Nvidia drivers (440 => 435), but I decided I should try rebooting first. I stopped my driver installation and then swapped back to build 440.

After rebooting, I couldn't log into Budgie. It would log me right back out onto the lock screen, and TTY was blank too (just a flashing cursor). Somehow I could still log onto regular Ubuntu though, so I went and sudo apt purge'd all my Nvidia packages, and then rebooted, but I was still getting the same login loop and broken TTY, so idk if it's the Nvidia driver's fault. 

Here's the journalctl logs from my most recent boot: [https://paste.ubuntu.com/p/g993g2HHn4/](https://paste.ubuntu.com/p/g993g2HHn4/) (I think Budgie log-in attempt is at line ~2000). As for system specs, I have an AMD CPU and an Nvidia GPU, and the OS is installed on an NVMe drive. Any help would be greatly appreciated! Let me know if additional info is needed!

---

