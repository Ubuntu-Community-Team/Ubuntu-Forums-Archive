---
title: "sudo gedit not Saving"
date: 2013-12-07
forum: General Help
---

### Post by Quarkrad on 2013-12-07
I'm getting this error in VirtualBox with a win7 cloned guest to do with the machine uuid code.  When I try to change the offending file using gedit I get the following message:

[B]dad@dadubuntu:~$ sudo gedit /media/backup/virtualbox/Win7 base Clone/Win7 base Clone.vbox

(gedit:4027): IBUS-WARNING **: The owner of /home/dad/.config/ibus/bus is not root![/B]


(I have tried changing codes in VirtualBox files using gksudo nautilus and cannot Save the changes to .xml or .vbox files using sud).   I guess this *The owner of /home/dad/.config/ibus/bus is not root*! is the cause of my problems.  I do not understand what this means - I thought (niavely) that you could change any file using sudo gedit because root was the owner of everything - obviously not!  Any help appreciated. 

(Ultimately I'm trying to get over the issue of having created a win7 guest clone on my 13.04 machine, I have to re-authenticate win7.  I have created the win 7 guest with my legit CD and microsoft is happy with the licence key.  But when I create a clone for a test microsoft doesn't like the key - VirtualBox changes uuid codes when a clone is created).

---

### Post by Lars Noodén on 2013-12-07
Try with gksudo instead of sudo.  Graphical programs generally should be lauched with gksudo instead.

---

### Post by steeldriver on 2013-12-07
use **gk**sudo or **gk**su for **g**edit - otherwise you will get a screwed up environment (as indicated by the message about root not owning files in your home dir)

---

### Post by Quarkrad on 2013-12-07
I must be doing something stupid - sorry.  When I enter **gksudo gedit /media/backup/virtualbox/Win7 base Clone/Win7 base Clone.vbox** or **gksu gedit /media/backup/virtualbox/Win7 base Clone/Win7 base Clone.vbox** I do not see the opened file.  I'm getting the attached.

---

### Post by Lars Noodén on 2013-12-07
If you have spaces in the path or file name then you'll have to wrap it in quotes or else 'escape' the spaces:

```

gksudo gedit /media/backup/virtualbox/Win7\ base\ Clone/Win7\ base\ Clone.vbox
gksudo gedit "/media/backup/virtualbox/Win7 base Clone/Win7 base Clone.vbox"

```

See if that opens up the file you want.

---

### Post by Quarkrad on 2013-12-07
That did it - thank you.  A valuable lesson.

---

