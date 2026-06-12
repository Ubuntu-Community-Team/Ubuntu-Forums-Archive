---
title: "cannot seem to update"
date: 2015-03-24
forum: General Help
---

### Post by jgw on 2015-03-24
I decided to run the updater as I had not seen it for a bit on this machine.  There were a number of updates.  The first one caused the following error:"The version 1.12.3-0ubuntu1/Ubuntu of liblightdm-gobject-1-0 isn't available." and it didn't get any better with the rest of the listed updates.    Since nothing seemed to get updated I ran the updater again and, this time, I got two more updates, VLC and ubuntu base.  When I told it to do it the updater dropped out and I got the notification there was a problem and did I want to restart.  I fear I have a problem and I am clueless.

Thank you..........

---

### Post by ian-weisser on 2015-03-24
Open a terminal.
Run the following two commands. Copy-and-paste the complete output here (it may be long).
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jgw on 2015-03-24
Thank you for the reply.  I fixed it, I think.  After I ran the stuff below I tried the updater again and, this time, it told me that there was nothing to do so the routine, below, seemed to do the trick - thanks again!

Here is what I did:
sudo apt-get update ##syncs the data bases between your system and your mirror site##
sudo apt-get upgrade ## updates installed software to what is current on your mirror##
sudo apt-get dist-upgrade ## installs new software (kernel) that 'update' does not handle##
sudo apt-get -f install ## looks and tries to 'fix' broken packages##
sudo dpkg -C ## runs an 'audit' of the package management system

sudo apt-get autoremove

---

