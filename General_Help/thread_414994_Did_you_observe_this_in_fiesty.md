---
title: "Did you observe this in fiesty ?"
date: 2007-04-20
forum: General Help
---

### Post by ss0007 on 2007-04-20
H i ubuntians ,

It seems I have noticed a bug and I wanted you to confirm before I report this. Perhaps I might have even downloaded a RC or a beta version.

Try this ,
1. Right Click on the Time panel on top right corner and goto "Adjust Date and Time".
2. Click the Synchronize button 

Issue : No action performed to either synchronize or pop-up an error message

Scenario 2:
1. Right Click on the Time panel on top right corner and goto "Adjust Date and Time".
2. Select the "Keep synchronized from the Servers" from Configuration combobox on top
3. Click the "Install NTP Support" 

Issue: Dialog closes and nothing happens. 

Does this happen to you ?

---

### Post by sloggerkhan on 2007-04-20
no

---

### Post by ashz on 2007-04-20
your right it does not do anything when u try and synchronize also if ur running amarok it seems that amarok keeps the songs in sync with the clock, u put the clock a minute forward then so does the song lol

---

### Post by ss0007 on 2007-04-20
Thx ashz .. 
It seems to be a simple bug. It will take it to the launchpad.

BTW, sloggerkhan , did u upgrade or clean install fiesty ?

---

### Post by compwiz18 on 2007-04-20
Yes, same problem before I installed NTP support.

---

### Post by ss0007 on 2007-04-20
Seems like fix has been already done since Dapper :

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/37230](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/37230)

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/13890](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/13890)

It's certainly a regression

---

