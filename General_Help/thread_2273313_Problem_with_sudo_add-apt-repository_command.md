---
title: "Problem with sudo add-apt-repository command"
date: 2015-04-12
forum: General Help
---

### Post by wdm2 on 2015-04-12
Hi there,

I am new to the ubuntu environment and just getting started with Linux at all.
So first I ran Linux Mint, and switched to Ubuntu 12.04 LTS after a short period of time.
I installed the new OS without formatting my drive. When I try to install software with the command sudo add-apt-repository ppa:...  I get the following error:
sh: 1: /usr/lib/linuxmint/mintSources/mintSources.py: not found

Somehow Ubuntu tries to access the Mint library, and since I am new to Linux, I don't know, how to fix this issue.

I also hope, that this is the right place to post my problem.

Kind regards,
wdm

---

### Post by TheFu on 2015-04-12
Seems your install is mixed.  I don't know how to fix that other than a format. Sorry.  You might be able to clean up /etc/apt/sources.list AND /etc/apt/sources.list.d/* - do an update.

OTOH, since you are so very new to this - a format would be much safer. Pick an OS. Use it.  If you want to play with another OS, create a 10G partition and play OR use virtual machines.

---

### Post by wdm2 on 2015-04-13
Thanks for the reply. 
I just formatted my drive in order to get a clean start with ubuntu.

Regards,
wdm

---

