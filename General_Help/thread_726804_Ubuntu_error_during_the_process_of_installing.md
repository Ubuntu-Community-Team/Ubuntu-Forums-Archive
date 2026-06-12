---
title: "Ubuntu error during the process of installing"
date: 2008-03-17
forum: General Help
---

### Post by DanielsaN8 on 2008-03-17
Asking on behalf for a pal, he got the following error while installing ubuntu [b]hdb error code 0x70: sense key 0x03: Asc 0x11: ASCQ 0x05", 
and: "Buffer I/O error on device hdb, logical block 4xxx[/b]

I posted on behalf for him and someone from this forum mention that it could be due to some of the key couldn't be detected and suggested getting a new key board. Fyi he's using a 4 way KVM switch for his Folding PC's but then though he got a **new keyboard recently since i inform him what someone mention on this forum** and reinstalling ubuntu again but get same error

So he has to reinstall xp again. Could any guru kindly advise us on this? thanks! :)

---

### Post by jan quark on 2008-03-17
did you have tried the alternate installation CD?

by "while installing" do you mean while booting or does this message crop up during the real installation process?

---

### Post by 3rdalbum on 2008-03-17
No, that error has nothing to do with the keyboard.

hdb sounds like a second hard disk - is this correct? The disk could be damaged.

---

### Post by DanielsaN8 on 2008-03-17
> **jan quark said:**
> did you have tried the alternate installation CD?

by "while installing" do you mean while booting or does this message crop up during the real installation process?

Tks for the prompt reply. Following are his thread on another forum 

> As far as Ubuntu, I downloaded the ISO file, burned to a CD and tried installing it. Went ok for a while then started with errors:
"hdb error code 0x70: sense key 0x03: Asc 0x11: ASCQ 0x05", 
and: "Buffer I/O error on device hdb, logical block 4xxx"
Kept repeating these errors one after the other for several screens until finally I hit reset. I think I waited about 5 minutes to see what would happed. It's fine for now, one day I'll try Ubuntu again

Here are his system specs and the particular rig which he's trying to run ubuntu on, fyi he downloaded the lastest version of ubuntu 

>  AX78, Phenom 9600+, 2Gb OCZ PC6400, EVGA 7100, CDRW/DVD :(

---

### Post by DanielsaN8 on 2008-03-17
> **3rdalbum said:**
> No, that error has nothing to do with the keyboard.

hdb sounds like a second hard disk - is this correct? The disk could be damaged.

If the hd could be any isssue then why it allow him to install xp without any issue?? Hope someone could point him to the correct direction. As far as i'm concern i've never face any major issue running redhat, fedora and ubuntu, not to mention encounter similar error as what he has which is why i'm helpless in rendering him assistance

---

### Post by Sef on 2008-03-17
> "Buffer I/O error on device hdb, logical block 4xxx

The most common cause is a bad sector on the hard drive.

> If the hd could be any isssue then why it allow him to install xp without any issue?? 

XP didn't need that sector, so no problem installing it.

---

