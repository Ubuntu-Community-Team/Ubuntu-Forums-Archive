---
title: "Problem running update and upgrade"
date: 2017-06-30
forum: General Help
---

### Post by satimis on 2017-06-30
Hi all,

Host - Ubuntu 16.04
VM (guest) - 16.04
Oracle VirtualBox

Each time after starting VM and run;
&#10219; sudo apt-get update ; sudo apt-get upgrade
following warning popup```

Hit:1 http://hk.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:3 http://hk.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Reading package lists... Done                     
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I have to run following command to remove the lock```

sudo rm /var/lib/apt/lists/lock

```

Is there a permanent solution?  Thanks

Regards
satimis

---

### Post by ajgreeny on 2017-06-30
Tyhe VM of 16.04 may be trying to auto-update security packages if that is the setting you have chosen, and therefore will have locked the system stopping you doing this manually.

Try waiting a few minutes, or if you prefer to update manually and not leave it to the system, turn of the auto-update system in Software-Sources by choosing as shown in my screenshot.

---

### Post by satimis on 2017-06-30
> **ajgreeny said:**
> Tyhe VM of 16.04 may be trying to auto-update security packages if that is the setting you have chosen, and therefore will have locked the system stopping you doing this manually.

Try waiting a few minutes, or if you prefer to update manually and not leave it to the system, turn of the auto-update system in Software-Sources by choosing as shown in my screenshot.
Hi,

Thanks for your advice.

I can't resolve that if I run "Software Updater" first and after finish I still need to run "sudo apt-get update and sudo apt-get upgrade".  It seems that there are some packages which can't be upgraded by "Software Updater"

satimis

---

### Post by ajgreeny on 2017-06-30
Not sure about that as I never use the software-updater; it's always either terminal or synaptic for me.

However, if you have security packages updating automatically there may still be other packages that have updates but are not considered security risks, so do not automatically update at the same time.

---

### Post by satimis on 2017-07-01
> **ajgreeny said:**
> Not sure about that as I never use the software-updater; it's always either terminal or synaptic for me.

However, if you have security packages updating automatically there may still be other packages that have updates but are not considered security risks, so do not automatically update at the same time.
Hi,

Advice noted and thanks

satimis

---

