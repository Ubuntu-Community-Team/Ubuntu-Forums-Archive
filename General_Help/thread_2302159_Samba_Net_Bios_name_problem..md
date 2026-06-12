---
title: "Samba Net Bios name problem."
date: 2015-11-08
forum: General Help
---

### Post by gordon16 on 2015-11-08
Hello,

I have installed Samba, but has some problem with the netbios name.
I`m not able to access the samba server from another computer on bios name but I can use the IP adress, from windwos \\192.168.1.3 works...

net bios name = ball

If I try to ping the netbios name i got ping replay from my offical IP adress on the outside....


**Copy past from smb.conf**

[I][global]

# workgroup = NT-Domain-Name or Workgroup-Name, eg: MIDEARTH
   workgroup = mbo

   netbios name = ball[/I]

---

### Post by gordon16 on 2015-11-08
It started working, but I dont now why :)

---

