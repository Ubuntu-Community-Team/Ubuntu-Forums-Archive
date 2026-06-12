---
title: "I can tell the add/remove to install do other drive"
date: 2008-04-17
forum: General Help
---

### Post by ~StAR~ on 2008-04-17
I would like to install Compiz on to my 2GB Eee Pc, I know the Eee pc can run compiz that the problem is my drive is full with mostly the os, I know I could reinstall but the my 4gb sd card would be fulll and I would have the 2 gb drive out of use... So I am looking for a way that I can tell the add remove and the packet manager to put the files on to the sd card rather then the hard drive. I seen on a site that it can e done, but I am new to linux and dident want to mess anything up.

---

### Post by northern lights on 2008-04-17
Run ```
sudo aptitude download <package>
``` then copy the package(s) to your Eee PC and  install...

---

### Post by ~StAR~ on 2008-04-17
> **northern lights said:**
> Run ```
sudo aptitude download <package>
``` then copy the package(s) to your Eee PC and  install...

but how would I go about installing them on to my SD card?

---

### Post by northern lights on 2008-04-17
Copy the package(s) onto the card, pop it in the Eee and install as you would on a regular comp...

---

### Post by ~StAR~ on 2008-04-17
> **northern lights said:**
> Copy the package(s) onto the card, pop it in the Eee and install as you would on a regular comp...

Yes, but that would put them in to the /usr folder, all that dose is is gives me Deb files, I need to move the /usr file first.

---

### Post by daengbo on 2008-04-17
Are you a new user? Do you really want to do this? If so:

1) copy the CONTENTS of /usr (do NOT copy the /usr directory) over to the SD. Make sure the SD is formatted with EXT3 or something *nixy.
2) reboot into a live USB system
3) delete all the /usr files on the first disk
4) modify /etc/fstab to point /usr to the new SD card.

This is really dangerous and may result in you totally screwing up your system. You have been warned!

---

### Post by ~StAR~ on 2008-04-24
> **daengbo said:**
> Are you a new user? Do you really want to do this? If so:

1) copy the CONTENTS of /usr (do NOT copy the /usr directory) over to the SD. Make sure the SD is formatted with EXT3 or something *nixy.
2) reboot into a live USB system
3) delete all the /usr files on the first disk
4) modify /etc/fstab to point /usr to the new SD card.

This is really dangerous and may result in you totally screwing up your system. You have been warned!

Would it just mess up the os, or could it mess up my computer?

---

### Post by northern lights on 2008-04-24
Apart from software overclocking, you can't screw your hardware via non physical interaction.

--> It could only screw your os.

---

