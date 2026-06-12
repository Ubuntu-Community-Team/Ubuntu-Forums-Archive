---
title: "downloading"
date: 2006-09-30
forum: General Help
---

### Post by hemple on 2006-09-30
i needed the latest version of flash player. so i got it off the website.but 

but i have trouble finishing it. how do i unpack it. is that even the right word. 

how do i do that for any program. i have a bunch of programs i got off of synaptic package manager.

:P

---

### Post by got_nix on 2006-09-30
what file extension is the file you downloaded? if its sa tar.gz then use 
```
tar -zxvf
```
if tar.bz then
```
 tar -jxvf
```

however if its just flash you want and you cant be bothtered then just isntall the non-free plugin from the repositoriess

sudo apt-get install flashplugin-nonfree

you might end up with a little problem.. flash saying it hasnt installed propelry you can easily fix that by doing this 

> change the line 35 of /var/lib/dpkg/info/flashplugin-nonfree.postinst

from

    /var/lib/dpkg/info/flashplugin-nonfree.postinst

to

    update-rc.d flashplugin-nonfree defaults >/dev/null

next time however.. use the [search]("http://www.ubuntuforums.org/showpost.php?p=1520991&postcount=17") luke.. may the search be with you

---

