---
title: "[SOLVED] How to make package unupgradeable"
date: 2007-12-22
forum: General Help
---

### Post by seabra on 2007-12-22
Hi everybody!

 I'm using qemu but since the upgrade to gutsy it stopped working.
 After some forum search I found out that there are some problems with qemu 0.9 and that people got their problem solved by downgrading to 0.8.
 However everytime I do updates i get qemu marked for upgrade which is something i don't want.
 Is there a way to mark the package as non-upgradeable so it doesnt keep showing up in updates?

 Thanks,

 Seabra

---

### Post by handaxe on 2007-12-22
Assuming you are in Gnome, in Synaptic highlight your installed package and select "lock" from the "Package" menu.

HA

---

### Post by tgilber1 on 2007-12-22
Another alternative is the CLI using the terminal

[LIST=1]
[*]From menu panel, click #Applications#Accessories#Terminal
[*]Type " sudo apt-get install --no-upgrade qemu
[/LIST]

The command should respond with the following:

Skipping qemu, it is already installed and _upgrade is not set_

The part that is underlined shows that the package has been set to prevent upgrades

---

