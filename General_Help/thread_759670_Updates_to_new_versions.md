---
title: "Updates to new versions"
date: 2008-04-19
forum: General Help
---

### Post by BradBrening on 2008-04-19
So, I've been using Ubuntu for about a week now and am enjoying this new "gadget".  I have to say I'm pretty impressed with the system - last night I purchased possibly the cheapest wireless keyboard/mouse set known to man from WalMart, and everything worked without a hitch.  Quite impressive.

I note that a new version is coming out soon.  Will this version get installed automatically via the system update process, or is it more like Windows where I would have to manually upgrade if I so desire?

Thanks!

---

### Post by ibutho on 2008-04-19
You would have to manually upgrade, but you don't necessarily need to get new installation media. You can edit your /etc/apt/sources.list file and change all instances of the word "gutsy" to "hardy". Once thats done, you can upgrade the OS by running the commands
```
sudo aptitude update
sudo aptitude dist-upgrade

```
If you prefer using the GUI, you could use the Add/Remove program or Synaptic to do the upgrade.

---

### Post by BradBrening on 2008-04-19
Excellent!  Thanks!

---

### Post by ramjet_1953 on 2008-04-19
Some people have no problem with upgrades, others do.

You can run into problems if you have used 3rd party installers, like AUTOMATIX.

What I prefer to do is to back up my /home directory and do a clean install.

Regards,
Roger :cool:

---

