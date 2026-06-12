---
title: "can't upgrade cryptsetup; insserv complains about checkroot"
date: 2014-01-12
forum: General Help
---

### Post by quequotion on 2014-01-12
I had never heard of "checkroot" (apparently responsible for running fsck at boot on a schedule or when poorly rebooted) until today, and then this is blocking upgrade to saucy:
```
insserv: Service checkroot has to be enabled to start service cryptdisks-early
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing cryptsetup (--configure):
 subprocess installed post-installation script returned error exit status 1
```

Apparently, I cannot proceed with installation until "checkroot" is installed and enabled, but it doesn't seem to exist. What do I do about that?

I have an encrypted home directory and encrypted swap on a RAID. I'm *terrified* at the prospect of not finishing this installation before the next reboot.

---

### Post by quequotion on 2014-01-13
Can anyone tell me what level of good/bad idea this is: to proceed with the installation, I simply removed "checkroot" from the initscript header.

---

### Post by quequotion on 2014-01-13
Carrying on, I've had to perform similar surgeries on about a half-dozen initscripts so far.

Since there isn't any particular documentation on the changes made to the init system for Saucy, although I did find a short list of "removed" scripts in a launchpad bug reply post, I really can't have any idea if this is the right thing to do.

---

### Post by quequotion on 2014-01-18
Well, no one ever replied...

If anyone ever has the same problem: delete the conflicting requirement from the init script and hope for the best.

The installation finally came to an end, but required several restarts because of these conflicts and other problems.
Furthermore upgrading to Saucy has made a complete and useless mess of my computer.

---

