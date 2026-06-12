---
title: "Ubuntu Server 12.04.1 LTS - Snapshot?"
date: 2013-05-22
forum: General Help
---

### Post by henriquev16 on 2013-05-22
[COLOR=#333333][FONT=Ubuntu Beta]I'm configuring OpenStack in my ubuntu server and now that I think I have this working and I want to do and try some configurations for Live Migration I want to know if there are any way to make a snapshot of my server without GUI, and if anything goes wrong I would have a restore option to go back to the "normal" state... is there any way?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Thanks![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]PS: I want to save files and configurations like permissions in determinated file...


[/FONT][/COLOR]

---

### Post by sudodus on 2013-05-22
I would suggest that you make an image of the whole drive with ***Clonezilla***. If the drive in huge and you have a lot of other things on it, you can make an image of the relevant partition(s) instead of the whole drive (also with Clonezilla).

Such an image is a snapshot, that you can use to restore the drive/partition(s) or make a clone on another drive.

---

