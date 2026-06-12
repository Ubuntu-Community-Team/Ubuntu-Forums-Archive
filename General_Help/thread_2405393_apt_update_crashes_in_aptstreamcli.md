---
title: "apt update crashes in aptstreamcli"
date: 2018-11-05
forum: General Help
---

### Post by daveh001 on 2018-11-05
I've done a lot of searching, but cannot find a solution for this:

me>> sudo apt update
[sudo] password for me: 
Hit:1 [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) bionic InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]                      
Hit:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic InRelease
Get:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]        
Get:5 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Fetched 247 kB in 2s (114 kB/s)     

(appstreamcli:2186): GLib-ERROR **: 09:30:29.212: ../../../../glib/gmem.c:105: failed to allocate 8388608 bytes

This is xubuntu 18.04.1 installed as a VM under VirtualBox 5.2.20, downloaded and installed within the past week.  It has 4G RAM and 2G swap allocated.  The disk (.vdi format) is dynamic, can grow to 80G, currently allocated 7G, of which about 10% is used.  There seems to be plenty of space.

Suggestions?

---

### Post by speartip on 2018-11-05
Does the same thing happen when updating via the live media? If not it could be a glitch in VirtualBox.

---

### Post by daveh001 on 2018-11-05
I don't know.  I do know that I've never had any problem with xubuntu LTS VMs under VirtualBox, which I've been using for many years.

The problem does not appear immediately.  That is, I install from .iso, reboot, run update and upgrade to bring everything up to date, reboot, no problems so far.  Then I start installing the additional software I want, e.g., php, mysql, vim, tcsh.  At some point, "apt update" starts crashing.  I can provide a crash report file if that will help.

Note that this crash happens after all the update information has been retrieved, and I can follow that up with "sudo apt upgrade", which properly updates whatever needs updating, although that always ends with this:

E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Start. Current value: 42991616. (man 5 apt.conf)
W: Could not open file /var/log/apt/eipp.log.xz - open (12: Cannot allocate memory)
W: Could not open file '/var/log/apt/eipp.log.xz' - EIPP::OrderInstall (12: Cannot allocate memory)

I don't know if this is related, or is a separate problem (suggestions found via google have not helped with this, either).  I was planning on starting another thread with this problem after this current one got resolved (if it does).

---

### Post by speartip on 2018-11-06
The apt cache size seems to be the problem.
After googling I found this:
[https://stackoverflow.com/questions/11911495/increase-the-size-of-aptcache-limit#](https://stackoverflow.com/questions/11911495/increase-the-size-of-aptcache-limit#)
Answer 3 might be what you're looking for.

---

### Post by daveh001 on 2018-11-06
I had found that page and tried all the possibilities given there.  No luck, but thx for the suggestion.

---

### Post by speartip on 2018-11-06
And yet the error line in #3, is definitely indicating that the apt cache size needs increasing.
It could well be a glitch that only appears in VirtualBox. I never did find things ran that well in virtualbox, so I carved up my Hard Drive, & dual/triple boot now.

---

