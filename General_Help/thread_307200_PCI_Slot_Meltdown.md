---
title: "PCI Slot Meltdown?"
date: 2006-11-26
forum: General Help
---

### Post by AlphaMack on 2006-11-26
Dell Inspiron 4100, stock, Ubuntu 6.06-1
Linksys WPC54GS

Over the last 11 months since installing Ubuntu on this machine I have been having a mostly problem-free experience with WiFi.  It sees very light usage as it belongs to my SO and is used to surf the web when I'm visiting her.

Unfortunately, I'm beginning to suspect that the PCI slots on this 5 yo machine are going south.  Dapper has been acting flaky and even locking up Mac OS 9-style - that is, total screen freeze with no way to move the mouse pointer or use a key combo to drop into a console (later I found out that these are kernel panics).  Upon rebooting, the WPC54GS isn't recognized *at all* - only if I repeatedly eject it and reload it enough times or switch between the upper and lower slots.  If it doesn't KP, it will eventually read the card and Network Manager will begin searching for my base station.  At first, it happened maybe once in a while and I originally thought that perhaps Dapper burped and needed a reboot.  Now it happens all of the time and I'm lucky if I can even get the card to function correctly in Dapper.  I would say that the frequency of this phenomenon was a progressive one.

When it does work nowadays, I'm lucky if I can go 20 minutes before I lose the connection and Dapper completely freezes while NM is trying to reconnect.  Again, in the past, I have had little to no trouble with this setup (aside from the Breezy to Dapper wlan0->ethX issue and maybe my noobness with NDISwrapper).

To determine whether the card was the issue, I placed it into my PowerBook G4 and Dapper there immediately recognized it.  Scratch that one.

To determine whether something borked in my Dapper install, I booted from a live CD.  Nope, the card wasn't recognized there either.  Didn't even show up in the Device Manager.  Scratch that one.

What is odd is the fact when I stick in the card, the lights come on and it *appears* to be working, but Dapper does nothing on this machine unless I "trick" it enough as described above (and without locking up the machine with a KP).

Thoughts?  Comments? Other suggestions?

---

### Post by AlphaMack on 2006-12-01
Resolved...

The card began to completely freeze Dapper frequently to the point where I suspected that the card itself was the issue, even after reinstalling 6.06-1 from scratch.  Even under Knoppix the card recognition was spotty.  Replaced with a Linksys WPC54G v.3 and no issues so far.

I ruled out the upper/lower PCIMCIA slots since the card was obviously receiving power from the status indicators.

Unbelievable that a freaking PCMCIA card craps out after barely 11 months of usage.

---

