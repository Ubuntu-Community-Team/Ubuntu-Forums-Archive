---
title: "External Harddrive Permissions"
date: 2007-11-03
forum: General Help
---

### Post by CupofDice on 2007-11-03
I just got a seagate freeagent drive, and I'm guessing it's formatted in ntfs because even gksudo nautilus prevents me from copying files. I am trying to take files from one unconnected comp to the one I'm on now. Should I hook up the drive to the comp I am on now to format it in fat32. Are there ntfs-3g debs out there for feisty fawn?

I gonna try to compile the source ntfs-3g source and see if that works, but any help is welcome.:)

Edit- Compiling didn't work. When I tried to make, I got "No targets specified and no make files found". I guess that means I need to debs for feisty.

---

### Post by Pumalite on 2007-11-03
You can install ntfs-3g:
sudo apt-get install ntfs-3g

---

### Post by CupofDice on 2007-11-03
I can't because it's unconnected to the net. I'm trying to format the drive now.

---

### Post by Thyme on 2007-11-03
Hi CupofDice, the install process is:

1) ./configure
2) make
3) sudo make install

---

### Post by Pumalite on 2007-11-03
Make sure you have build-essential installed.

---

### Post by CupofDice on 2007-11-03
I know, that didn't work. I just formatted the drive as fat32. Hope this works.

Edit- It worked. Thanks for the help.

---

