---
title: "how to update firefox on this system ???"
date: 2020-01-11
forum: General Help
---

### Post by mordeau5006 on 2020-01-11
Firefox doesn't update automatically... Instead it wants to download each time to a folder,but than i can't use icon on panel - so annoying....... I tried this [https://www.tutorialology.com/ubuntu/how-to-update-firefox-in-ubuntu/](https://www.tutorialology.com/ubuntu/how-to-update-firefox-in-ubuntu/) and ended up with error message: 
E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

I read solution to this can permanently damage system and i don't have experience with this system, i don't want to do that.
Can you please tell me how to update firefox automatically ? 

I would appreciate it thanks !!!

---

### Post by Autodave on 2020-01-11
What version of 'buntu are you running??

---

### Post by mordeau5006 on 2020-01-11
19.04

---

### Post by Artim on 2020-01-11
It almost sounds like a snap download rather than from the Ubuntu repositories.  Is that possible?

---

### Post by howefield on 2020-01-11
Firstly 19.04 goes End of Life this month so you might want to think about upgrading when the time comes.

All currently supported versions of Ubuntu should have Firefox 72.0.1 so if you have something different there should be an update waiting for you to apply. On a default installation of Ubuntu you should receive notification of updates as they become available, this will update all packages to the current repository version including Firefox. Are you not getting any notifications ?

The above error just means that you have more than one package manager running simultaneously, so close yourl terminal and and open up Software Updater, the rest should be self explanatory.

---

### Post by crip720 on 2020-01-11
Open up 'software and updates' and check to see when updates are to notify/display to you.  Should be daily or weekly, adjust if needed.  Since Firefox is included, it should be updated automatically without you having to update manually, unless you don't install updates.

---

### Post by TheFu on 2020-01-11
> **mordeau5006 said:**
> 19.04

If using a the normal package manager, then normal patching will get the latest firefox.  My system has the version from 1/8/2020. Yes, I still use 16.04 here.

```
$ ll /usr/bin/firefox 
lrwxrwxrwx 1 root root 25 **Jan  8** 06:23 /usr/bin/firefox -> ../lib/firefox/firefox.sh*


$ dpkg -l |grep firefox
ii  firefox     **72.0.1**+build1-0ubuntu0.16.04.1      amd64        Safe and easy web browser from Mozilla

```
I only patch weekly, on Saturday mornings.  That's it.
```
sudo apt update
sudo apt upgrade
```

If you've allowed snaps onto your system, in theory, it should be updated for you automatically.  I prevent snap packages for a number of reasons, but everyone is different. To see installed snaps, use:
```
snap list
```
May want to filter that list with a grep. IDK.

Support for 19.04 ends very soon. If you have time today, make a backup of the system (however you normally do that), then get fully patched (**sudo apt update && sudo apt dist-upgrade**) and run the upgrade to 19.10 process (**sudo do-release-upgrade**).  Most of the time, that should go fine, but perhaps 20% of the time, it doesn't.  Please do not skip the backup process.

---

### Post by VMC on 2020-01-11
removed

---

