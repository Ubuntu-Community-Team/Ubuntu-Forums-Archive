---
title: "0 bytes in boot when updating"
date: 2015-05-26
forum: General Help
---

### Post by Spae on 2015-05-26
Ok, I realise I have to delete old linux images(?) to make space but i'm not sure which I can delete. I'm trying to update my 14.04 LTS. I think the software updater should do this...

Can you tell me which to delete from synaptic or how to do it with the terminal?

---

### Post by Bashing-om on 2015-05-27
Spae; hello;

The terminal command:
```

sudo apt-get autoremove

```
will remove obsolete files, as well as old kernels, leaving the kernel that is booting and one other for a backup.

[INDENT]my bit to try and help
[/INDENT]

---

### Post by Spae on 2015-05-27
Great! Thanks

---

### Post by SeijiSensei on 2015-05-27
Autoremove may not completely fix the problem depending on how many stale kernels there are. For  those cases, I posted a method in [http://ubuntuforums.org/showthread.php?t=2276860](http://ubuntuforums.org/showthread.php?t=2276860).

Also please read [http://ubuntuforums.org/showthread.php?t=2278674](http://ubuntuforums.org/showthread.php?t=2278674) for more context.  Did you set up a system with Logical Volume Management (LVM) or full-disk encryption?  Both of those require a separate /boot partition that can easily run out of space if you're not vigilant. Ordinary users should never need LVM except in very unusual circumstances, and full-disk encryption only matters if you are worried about your computer falling into someone else's hands.  I never use either of these options.

You might want to drop by bugs.launchpad.net and endorse Elfy's bug report on this matter: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

---

