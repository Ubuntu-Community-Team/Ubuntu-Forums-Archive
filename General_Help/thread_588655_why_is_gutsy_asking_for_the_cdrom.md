---
title: "why is gutsy asking for the cdrom"
date: 2007-10-23
forum: General Help
---

### Post by coloured on 2007-10-23
Sometimes when installing and uninstalling software my new gutsy system will ask for the cdrom to be inserted - which is a real pain in the *rse, because like most ppl I dont carry it with me all the time.

for example - I installed gnash - and found that it messes with the video window on youtube, so I decided to uninstall it, during the uninstall process (initiated from synaptic) I was prompted to insert the gutsy cdrom. I had initially installed gnash without the requirement for the cdrom, why should it need it during the removal?

example2: I wanted to setup vmware workstation - it requires c++ compiler etc. I selected build-essentials from synaptic - hit apply and was again prompted for the gutsy cdrom!

I never had this issue with feisty - is there something I am missing? - am I able to prevent it from asking for the cdrom and rather get the files from somewhere else on the net if the cdrom is unavailable.

cheers
Jurgen

---

### Post by chrisccoulson on 2007-10-23
You might have a cdrom entry in your /etc/apt/sources.list. If you do, then comment it out. If you're not sure, post it here and we may be able to help.

---

### Post by Shiva88 on 2007-10-23
Or you can check via the GUI:

System>Administration>Software Sources

enter password

On the first tab ("Ubuntu Software"), see if the CD-Rom option under "Installable from CD-ROM/DVD" is checked.   If so, uncheck it.

---

### Post by chrisccoulson on 2007-10-23
Yes, that may be easier actually

---

### Post by coloured on 2007-10-23
thanks very much chris! 
I knew it must have been something noobish I was doing :P

I have never used that sources tool in the administration menu until now with gutsy.
I failed to notice the checkbox to enable the cdrom sources.

thanks heaps
Jurgen

---

