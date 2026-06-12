---
title: "update from 22.04 to 24.04"
date: 2024-06-14
forum: General Help
---

### Post by jgw on 2024-06-14
I noticed that, apparently, ubuntu 24.04 is available so i thought I would look it up and maybe update to it.  What I found out was that my 22.04 doesn't know that there is a 24.04 and if that is the case I should not try and update to 24.04   Actually I am happy with 22.04 and was just wondering about the 24.04 thing and, because I don't know that there is a 22.04 i thought I would ask if anybody actually knows what is going on.  

I then brought up Software and Updates and made sure that it was setup correctly.  It is.  Anyway....

This is not a big deal, just curious...........

---

### Post by deadflowr on 2024-06-14
No upgrade until August when the first point release is available.
Always been this way for LTS to LTS upgrades.

---

### Post by jgw on 2024-06-15
Thank you for the reply!

All the offers to update to 24.04 just gave me pause.  Thank you, figured something like this..........

---

### Post by ne29914 on 2024-06-16
> **deadflowr said:**
> No upgrade until August when the first point release is available.
Always been this way for LTS to LTS upgrades.

Completely new to me. So a "sudo do-release-upgrade" will not work, but a .iso install will?

---

### Post by grahammechanical on 2024-06-16
> Completely new to me. So a "sudo do-release-upgrade" will not work, but a .iso install will?

An iso install is a fresh install. We cannot upgrade Ubuntu 22.04 LTS from a Ubuntu 24.04 LTS iso image on a USB memory stick. Back up your data before upgrading one LTS version to the latest LTS version using the fresh install method.

Some of us prefer a fresh install to an online upgrade. It clears out unwanted applications and configuration files.

Regards

---

### Post by Dennis N on 2024-06-16
There is a way to upgrade 22.04 to 24.04 now without doing a new install, and not wait. 

You do two successive upgrades to your 22.04. First to 23.10, and then upgrade again to 24.04.

1) In the "Software & Updates" utility of Ubuntu 22.04, open the "Updates" tab, set "Notify me of a new Ubuntu version" to "For any new version".

2) Run Software Updater, and after doing any updates, it will inform you of an upgrade to Ubuntu 23.10 (see screenshot). Do that upgrade. 

3) In Ubuntu 23.10, run Software Updater to do any updates, and you should also get another notification that you can upgrade to Ubuntu 24.04. Do that, and you are done.

Do this before July 11, 2024 when 23.10 loses support.

---

### Post by guiverc on 2024-06-16
The Ubuntu 24.04 LTS Release notes (and *annoucements*) I thought were rather clear

- [https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890](https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890)
- [https://fridge.ubuntu.com/2024/04/25/ubuntu-24-04-lts-noble-numbat-released/](https://fridge.ubuntu.com/2024/04/25/ubuntu-24-04-lts-noble-numbat-released/)
> 
[h=2]Upgrades[/h] Users of Ubuntu 23.10 will be offered an automatic upgrade to 24.04 soon after the release.
Users of 22.04 LTS however will be offered the automatic upgrade when  24.04.1 LTS is released, which is scheduled for the 15th of August.


The ISO release is for new installs, the upgrade from 23.10 was opened up a short time after ISO release, and we've not yet reached 15 August for upgrades from the prior cycle; though *release-upgrades* from 22.04 thru 23.10 to 24.04 are open.

This is detail that was already provided, but shouldn't have been new if release notes or the many announcements were read.

---

