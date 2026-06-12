---
title: "Apt-get upgrade won't work in Kubuntu [Resolved]"
date: 2007-03-03
forum: General Help
---

### Post by caffienda on 2007-03-03
I used the sources.list file from my Ubuntu Edgy install for my new Kubuntu 6.10 install is this ok?  I can run apt-get update, but not upgrade.  This is what I get: Oh, I am logged in as the administrator (account set up in the installation)

caffiendo@Kubuntu:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
caffiendo@Kubuntu:~$

---

### Post by aysiu on 2007-03-03
Is another process using it?

Other processes might be the update manager, Adept Package Manager, or Add/Remove Programs.

---

### Post by caffienda on 2007-03-03
Yeah, I just found the  GUI updater running in the background.  This is my first time using Kubuntu so I don't know what is normal/default.  I guess the GUI updater automatically runs.

Thanks for replying!

---

### Post by aysiu on 2007-03-03
Just so you know, *dpkg* takes many forms. From the command-line, it can be *apt-get* or *aptitude*. Through the GUI, it can be update manager, or Synaptic Package Manager, Adept Package Manager, or Add/Remove Programs. Those are all frontends to *dpkg*, and only one can be running at any given time.

Glad you got it all sussed out.

---

