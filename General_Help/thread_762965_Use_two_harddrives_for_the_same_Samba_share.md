---
title: "Use two harddrives for the same Samba share?"
date: 2008-04-22
forum: General Help
---

### Post by _sAm_ on 2008-04-22
Two of my harddrives are both full with movies. I am sharing them with Samaba on the LAN, and they show up as shared folders called "Movie" and "Moive2". 

Is it possible in Samba conf two add two ore more path(to folders/harddrives) for the same share? So in my case harddrive 1 & 2 would show up as "Movie"? 

Thanks for any answer

---

### Post by blastus on 2008-04-22
> **_sAm_ said:**
> Two of my harddrives are both full with movies. I am sharing them with Samaba on the LAN, and they show up as shared folders called "Movie" and "Moive2". 

Is it possible in Samba conf two add two ore more path(to folders/harddrives) for the same share? So in my case harddrive 1 & 2 would show up as "Movie"? 

Thanks for any answer

Why don't you use a script on the client side that creates links to all the files on all your mount points? I do this in MythTV so that I don't have multiple video sources and it works great.

---

