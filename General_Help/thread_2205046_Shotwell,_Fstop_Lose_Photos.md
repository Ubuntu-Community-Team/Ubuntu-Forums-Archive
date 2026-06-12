---
title: "Shotwell, Fstop Lose Photos"
date: 2014-02-11
forum: General Help
---

### Post by erhollowell on 2014-02-11
I have had a problem that I assume has something to do with directory structure. I place photos into a directory and import them into Shotwell and come back a week later and Shotwell goes through a big show searching for photos and then tells me it can't find them. I can re-import them but the next time it will happen again.

I am guessing that, because I have the photos on a different drive than the OS somehow the directory structure is being changed on reboot and the app is loseing track of the location.

Any ideas on how to assure that the photo programs don't 'lose' the photos?

---

### Post by tgalati4 on 2014-02-11
First locate the shotwell database.  Then make sure the drive that you have your photos on is permanently mounted and that mount is correctly identified in /etc/fstab.

---

