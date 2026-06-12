---
title: "ubuntu file server for xp network"
date: 2007-04-13
forum: General Help
---

### Post by 95aspire on 2007-04-13
i just got my 80gb to where i can format it via the gui, but i cant choose ntfs, if i choose ext3 can windows xp see it and write to it? if not can you tell me how to format to ntfs please? thanks guys

---

### Post by murlosad on 2007-04-13
> **95aspire said:**
> i just got my 80gb to where i can format it via the gui, but i cant choose ntfs, if i choose ext3 can windows xp see it and write to it? if not can you tell me how to format to ntfs please? thanks guys

if you are sharing the drive between linux and XP on the same machine (dual boot setup) it's probably easier to use ntfs or fat32 so both operating systems can write to it.

if you are sharing the drive over a network you can setup a samba share and xp will see it as a network filesystem and depending on your permissions it can write to it.

check out this guide for help setting up samba: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")

as always there is lots of help around here for this type of thing, the [Search]("http://ubuntuforums.org/search.php") button is your friend

---

### Post by 95aspire on 2007-04-13
> **murlosad said:**
> if you are sharing the drive between linux and XP on the same machine (dual boot setup) it's probably easier to use ntfs or fat32 so both operating systems can write to it.

if you are sharing the drive over a network you can setup a samba share and xp will see it as a network filesystem and depending on your permissions it can write to it.

check out this guide for help setting up samba: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")

as always there is lots of help around here for this type of thing, the [Search]("http://ubuntuforums.org/search.php") button is your friend

yes i know i needed an answer asap and i already have samba setup and stuff. just didnt know if it would work from my server as an ext3 partition to a xp machine. 

and no its not the same machine. thanks man tried it and it works.

---

### Post by dmizer on 2007-04-13
*already solved* sorry folks too late on the draw here.

---

