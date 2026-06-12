---
title: "Invalid Filename Extension"
date: 2017-01-14
forum: General Help
---

### Post by tb75252 on 2017-01-14
I am using Ubuntu 16.04 LTS, 64-bit.

Whenever I run "sudo apt-get update" I also get the following message:
"AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
**N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension**".

And whenever I run "sudo apt-get upgrade" I also get the same message:
"**N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension**"

How do I fix this?

---

### Post by egeezer on 2017-01-14
That's an older file, superceeded by a new one.  If you open **/etc/apt/apt.conf.d/' you'll see two 20auto-upgrades files with different extensions.  The newer one is in use, older is ignored.**

---

### Post by deadflowr on 2017-01-14
Appstream error has a fix, see:
[https://ubuntuforums.org/showthread.php?t=2348398&p=13593863#post13593863]("https://ubuntuforums.org/showthread.php?t=2348398&p=13593863#post13593863")

Unless the upgrading doesn't go through and run like normal (meaning the process stops before anything ever happens or ends with error messages like a failed to fetch or something),
you can either ignore the .ucf file or remove it.
Your choice.

---

### Post by tb75252 on 2017-01-14
I decided to remove file "**20auto-upgrades.ucf-dist**" and things seem normal.
Thanks for the help!

---

