---
title: "MP3 Player Installation"
date: 2008-01-25
forum: General Help
---

### Post by ilovelinux on 2008-01-25
Hi there, I am fairly new to installing programs etc on my system.....I run Ubuntu 2.0 and have bought a fairy low end MP3 Player for my 9 yr old son.  It's a Diamond MP3 1iGB player.  

The problem is I have no idea how to install the drivers as it's seems to be only for Windows.....AAGGHH.... Could someone give me insight to install the drivers...I have attempted to look up the Website for company but am not able to find it......is there a quick solution???

Any assistance would be appreciated :-)

---

### Post by benanzo on 2008-01-25
I'm not sure about your particular MP3 player, but if it's low-end then it is likely just USB mass storage and should work out of the box.  If it is MTP-based then you'll want to enable the portable player MTP plugin in Rhythmbox.

Disconnect the player then go to Edit -> Plugins in Rhythmox and enable MTP.  Then close Rhythmbox and plug your player in.  You can now re-launch Rhythmbox and if it worked then you'll see it appear in the sidebar on the left.

---

### Post by dcstar on 2008-01-25
> **benanzo said:**
> I'm not sure about your particular MP3 player, but if it's low-end then it is likely just USB mass storage and should work out of the box.
.........

Agreed, it should just mount and appear on the desktop like any other USB drive, then you just "drag-and-drop" MP3 (or whatever) files into it.

Some devices have Windows only software (I had a Sony Network Walkman like that), my solution was to install VMware server and run Windows inside of that, then I could access the player with Windows while still running Ubuntu.

---

