---
title: "Three Ubuntu 14.04lts"
date: 2016-01-30
forum: General Help
---

### Post by rosswmcgee on 2016-01-30
We have 3 ubuntu 14.04lts computers on the same cable connection. This morning one computer will not connect to the internet. I checked the cable by using an older mint computer it works, so it is not mechanical. I re-booted the modem that is not the problem. I have checked the connections that is not it either, so what to do???

---

### Post by kansasnoob on 2016-01-30
It's good that you tried a different computer on the same network cable, that tells us we can rule out problems up to that point. Two additional easy troubleshooting steps come to mind:

(1) Try booting the affected computer using a live DVD/USB. If you have a connection using the live session but not the installed system then it's likely a problem with the operating system. Of course if it also doesn't work with the live session then I'd be suspect of a hardware failure - possibly worth checking BIOS settings including PC Health.

(2) If you have a connection running a live session then we could narrow it down a bit more by having you boot into the installed OS, then log out and log into a guest session. If you have a connection in the guest session but not the user session then we know it's something mis-tweaked in user settings.

---

### Post by rosswmcgee on 2016-01-30
Thanks will get busy..

OK running live cd works fine that way. Running diagnostics in bios// must be operating system so I guess a new install is in order???

Passed diagnostics test.

So what could have gone wrong, now doing new install of Ubuntu 14.04.3?

---

### Post by kansasnoob on 2016-01-31
Sorry for the long delay :redface:

Knowing that I'd try this (**do not reboot until the second command has been run**):

```
sudo apt-get purge resolvconf
```

Wait for that to finish and then:

```
sudo apt-get install resolvconf* ubuntu-minimal*
```

Then reboot and keep your fingers crossed.

That should restore most of the default network settings to out-of-box status.

---

### Post by sammiev on 2016-01-31
If this happen after an update you may want to read this [thread]("https://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet") as it seem to have effected multiple users.

---

