---
title: "lifespan of files in /run directory?"
date: 2015-09-12
forum: General Help
---

### Post by roland-logikalsolutions on 2015-09-12
Maybe I'm just getting tired and getting stupid, but this particular problem woke me up again. I have to solve it later today. Right now I'm testing on Ubuntu 12 32-bit.

Basically this little kiosk type application has an admin page with a one-button-uninstall. After prompting for a password the uninstall program copies an upstart job and a systemd job to the directories where they go. Both of these execute a shell script which the uninstall copies to /run. The uninstall then forces a reboot.

What I find in syslog after reboot and exiting the kiosk app because it restarted, is a message saying the shell script could not be found. Sure enough, it is no longer in the directory listing. Oh, must not have completed copy before reboot. I hand copy it out there and do a directory listing to verify it is there. Force a reboot and am greeted by the kiosk starting up.

I'm really tired and will probably regret posting this when I read it much later after sleep.

It appears all of the systemd stuff is there on Ubuntu 12. The syslog messages I see are from the upstart job, not the systemd service. Would a systemd only job work with Ubuntu 12, 14, & 15 both 32-bit and 64-bit? All of this was working until I went to 15 and found out upstart was no longer supported. This is fallout from refactoring and trying to straddle the fence.

---

