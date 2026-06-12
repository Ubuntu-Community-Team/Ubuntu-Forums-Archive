---
title: "kbfx kills kicker in feisty"
date: 2007-05-01
forum: General Help
---

### Post by fuscia on 2007-05-01
when i try to add it to the panel, it gets killed. this is what i'm getting in konsole while it happens...

fuscia@fuscianator:~$  load MOview siez x 124 39
QObject::connect: No such signal vista::hide()
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'kbfxspinx')
kicker: crashHandler called
KCrash: Application 'kicker' crashing...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


there is also no entry for kbfx in kcontrol. there is also no folder for it in /home/me/.kde/share/apps.

---

### Post by fuscia on 2007-05-06
bump

---

### Post by fuscia on 2007-05-11
ok, this is your last chance.

---

### Post by seaq on 2007-05-20
seems that i'm having same or at least a similar trouble... gone do further investigation

---

### Post by seaq on 2007-05-20
if i add kbfx to the kicker it hangs i must xkill it

if i try to reload kicker i've got this

kicker
andres@dieguito:~$  load MOview siez x 124 39
QObject::connect: No such signal vista::hide()
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'kbfxspinx')
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image

---

### Post by fuscia on 2007-05-21
i used the deb file from kde-look and it works fine now.

---

