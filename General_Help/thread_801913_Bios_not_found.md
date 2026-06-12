---
title: "Bios not found"
date: 2008-05-21
forum: General Help
---

### Post by TrezenChath on 2008-05-21
Hi, I'm trying to update my ASUS Motherboard drivers to get my sound to work, but everytime I put in the update cd that came with the Motherboard and run the program it says no Bios could be detected. Anyone know what I need to do?

FYI my motherboard is an ASUS 939 Socket A8V-VM

---

### Post by fsmithred on 2008-05-22
You shouldn't need to install any additional drivers for that generation of motherboard. I think you need to do:

asoundconf list
asoundconf set-default-soundcard CARD

where CARD is a value you got from list. I can't remember if it's a name or a number, and you might need to use sudo with that command. I'm not on ubuntu right now to check.

---

