---
title: "Built in Firewall???"
date: 2007-12-23
forum: General Help
---

### Post by dethredic on 2007-12-23
Is there a built in Firewall or something in Ubuntu that is blocking my access to a port in Wine?

Does Wine have a built in firewall?

The thing is, I can use the port in windows, but not via wine in Ubuntu.

---

### Post by ubuntu27 on 2007-12-23
GNU/Linux has built-in Firewall called "IPTABLES"  that it is _turned **off** by default_

I don't it has anything to do with Wine. I can not assure you though, since I have never used Wine.

---

### Post by reckless2k2 on 2007-12-23
i think the better way to explain it is that all ports are closed on ubuntu with an initial install. as certain services are enabled the corresponding port will be opened. wine does not have a firewall in it. 

incoming connections are disabled by default. out-going connections are not blocked at all.

i'm not sure of the wine  program you are installing or running but more than likely if it requires a port opened for an outside connection to come in, then you are going to need to edit the iptables to tell it to open that port. sounds a little funny though.

---

### Post by dethredic on 2007-12-23
well, the program is Warcraft 3.

To be able to host (allow people to connect to me) you need to open port 6112. I have it open on my router, and can host when I switch to my windows partition.

How do I edit/access the Iptables?

---

### Post by az on 2007-12-23
Wine doesn't have a firewall.  But if the application that you want to use is trying to communicate directly with the hardware, it won't work.

Another reason why you can't use a port is if it already in use by another application.

What are you trying to run?

---

### Post by dethredic on 2007-12-23
I am trying to run Warcraft 3. I would like to be able to host custom games.

---

### Post by ubuntu27 on 2007-12-23
[How-To IPTables]("https://help.ubuntu.com/community/IptablesHowTo")

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Adjusting the IPtables manually is quite difficul (you have to have a deep understanding of how it works)

I recommend you to install an application that act as a frontend to IPtables.

Search for "iptables" and "firewall" in Synaptic.  I use KDE, and I like to use "[GuardDog"]("http://www.simonzone.com/software/guarddog/")

---

### Post by dethredic on 2007-12-24
Ok, I intalled GuardDog as well.

How do I open it?

---

### Post by SOULRiDER on 2007-12-24
If youre using KDE use GuardDog, if youre using GNOME use Firestarter. Look for hte application in your menu under the internet section. Alternatively you can run it from a console, type firestarter for Firestarter and for guarddor kguarddog or guarddog, i dont remember which.

---

### Post by dethredic on 2007-12-24
ok, thanks man.

---

