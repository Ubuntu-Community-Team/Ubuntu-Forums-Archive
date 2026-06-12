---
title: "restoring backup file [Resolved]"
date: 2007-04-15
forum: General Help
---

### Post by cessna_89702 on 2007-04-15
i backed up my xorg.conf and i cant start ubuntu normally it goes into a text based one. how do i restore the backup xorg with commands?

---

### Post by aysiu on 2007-04-15
```
cd /etc/X11
``` will put you into the correct directory. Make sure the X is capital (X11) and not lowercase (x11). ```
ls
``` will list all the files in that directory. Make note of the exact name of the backup. Let's assume for now that it's xorg.conf.bak (substitute in the actual name, of course). ```
sudo mv xorg.conf xorg.conf.bad
``` will make a backup of the screwed up xorg.conf. Then ```
sudo mv xorg.conf.bak xorg.conf
``` will restore the original backup. Finally ```
sudo /etc/init.d/gdm restart
``` should get you up and running again if you're using Ubuntu or Xubuntu. Use ```
sudo /etc/init.d/kdm restart
``` if you're using Kubuntu.

---

### Post by cessna_89702 on 2007-04-15
there is no bad xorg conf.       theres only the backup

---

### Post by cessna_89702 on 2007-04-15
i try to restore but i need a password and i type it in and it says incorrect so i cant do anything..I might just get rid of ubuntu

---

### Post by aysiu on 2007-04-15
The bad one is the one you're using now.

Presumably you want to replace the bad one (the one you're using) with the good one (the one you were using--the backup copy).

Are you sure you're typing your password correctly? It is case-sensitive.

---

### Post by cessna_89702 on 2007-04-15
Ok i logged in not sure what happenend before.


I dont believe I actually am using a xorg.conf now. I made a new one wihch was the bad one which got deleted.  

I ran ls and I see that the backup IS there. what command makes it the actual regular xorg

---

### Post by aysiu on 2007-04-15
Well, the command really depends on what the name of the backup is. If the name of the backup is xorg.conf.bak, then the command would be ```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
``` If the name of the backup is xorg.conf~, then the command would be ```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
``` After that type ```
sudo /etc/init.d/gdm restart
``` to use the new file (and restart the X server).

---

### Post by cessna_89702 on 2007-04-15
dont mind my last post i got it going

thanks

---

### Post by rickycodie on 2007-04-16
thanks i did seach for this and now i'm not freaking out. whew!!

---

