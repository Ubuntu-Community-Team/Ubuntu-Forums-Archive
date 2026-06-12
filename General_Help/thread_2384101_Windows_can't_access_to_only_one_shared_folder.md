---
title: "Windows can't access to only one shared folder"
date: 2018-02-02
forum: General Help
---

### Post by erny83pd on 2018-02-02
hi guys, I shared two folder with samba in Ubuntu 16.04, the first one is inside the folder "home" and the other is inside a secondary hard drive.
I dont' have problems to access to the first one but I can't access to the secondary shared folder (that in the secondary hard drive), windows say "unable to access: insufficient permissions"

this is the configuration:
```

[BOX]
 path = /home/rivs/BOX

 available = yes

 browsable = yes
 public = yes
 writable = no
  

  

 [MEDIA]
 path = /media/rivs/Box2/MEDIA
 available = yes
 browsable = yes
 public = yes

 writable = no
```

---

### Post by Morbius1 on 2018-02-02
Change this:

> [MEDIA]
 path = /media/rivs/Box2/MEDIA
 available = yes
 browsable = yes
 public = yes
 writable = no
To this:
> [MEDIA]
 path = /media/rivs/Box2/MEDIA
 available = yes
 browsable = yes
 public = yes
 [COLOR=#0000cd]**force user = rivs**[/COLOR]
 writable = no
Restart smbd:
```
sudo service smbd restart
```

---

### Post by erny83pd on 2018-02-02
Thank u very much Morbius1 :) it worked!

---

