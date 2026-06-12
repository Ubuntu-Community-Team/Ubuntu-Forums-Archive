---
title: "Sources list edited, upgrade, now Ubuntu broken"
date: 2012-11-19
forum: General Help
---

### Post by lemonoid on 2012-11-19
Okay so I'm about to install Win8, wipe my Ubuntu and install Ubuntu 12.10. I was on 12.04 and wanted a version of 12.10 to clone for after I have Win8 setup. Since Quantal came out, it WILL NOT show it in my update manager. So after looking at help forums last night I was told that I could go into my Sources list and change all of precise to quantal, save, then apt-get update & apt-get upgrade. I did all that, it ran like 1400 some upgrades, I turned off the computer. I just woke up and turned it on, and I go to the login screen, put in my password and hit enter, then I'm taken to a black screen and I should've remembered what it said but it was something along the lines of Can't Load System ...... does anyone know how I can fix this?? it would REALLY help me right now, I'm booting Live right now.

---

### Post by lykwydchykyn on 2012-11-19
This can happen when the disk is full, which is certainly a possibility if you just downloaded 1400 packages.  It could also be that the upgrades are not complete, and your system is in limbo between precise and quantal.

Boot your system to the "recovery mode" and select "root shell" from the options.  

Run "df -h" in the terminal to see how full your file systems are.

If your main partition is full, try running "apt-get clean" to clear up the space.

If not, try running "apt-get -f install", or maybe just "apt-get dist-upgrade".

---

### Post by snowpine on 2012-11-19
> **lemonoid said:**
> So after looking at help forums last night I was told that I could go into my Sources list and change all of precise to quantal, save, then apt-get update & apt-get upgrade.

Whoever told you that doesn't know what they are talking about; this upgrade method is 100% unsupported by Ubuntu.

The actual instructions are here (if it's not too late; you may need to reinstall your broken system): 

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

If the 12.10 upgrade doesn't show:

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_12.04_LTS)

---

