---
title: "Automount ISO script??"
date: 2008-06-04
forum: General Help
---

### Post by MasterNetra on 2008-06-04
I was wondering how would i make a automounting script for a .iso? I tried the following with failure. I suppose the script structure isn't allowing for the sudo password to be entered.

[SIZE="1"]Note: Naturally I replaced the actual password with "<password>" for security reasons :p[/SIZE]
---------------------------------------------------------------
[COLOR="Red"]
          ISO=/home/LocalShare/.iso/OBLIVION.iso
          sudo mount -o loop -t iso9660 $ISO /media/iso0/ 
          <password>
[/COLOR]
---------------------------------------------------------------

So if anyone knows the correct way of doing this I would appreciate it if you let me know. Thank you.

---

### Post by hal10000 on 2008-06-04
maybe you can make an entry into the /etc/fstab file, i don't know if this works for .iso files but you may try this
> 
/home/LocalShare/.iso/OBLIVION.iso /media/iso0 iso9660 noauto,user,ro 0 2


You should then be able to mount it as a normal user.

---

### Post by bigken on 2008-06-04
there is also gmount-iso you might be able to make it auto mount your iso

---

### Post by MasterNetra on 2008-06-04
Alright I'll try both. Thanks.

---

