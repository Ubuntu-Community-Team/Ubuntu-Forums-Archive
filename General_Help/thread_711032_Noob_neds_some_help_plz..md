---
title: "Noob neds some help plz."
date: 2008-02-29
forum: General Help
---

### Post by Arkas on 2008-02-29
okay im a total noob, and never heard of linux  untill a few months ago.

Okay 
Ive tried Applications>Accessories>Terminal

I have tried different commands and all have failed such as,
sudo apt-get bluefish

Debian and Ubuntu users just run apt-get install bluefish and Bluefish will be downloaded, configured and installed on your system.

I would like to install bluefish to start a web page

Thanks inadvance

---

### Post by kesman on 2008-02-29
you forgot the install part. apt-get bluefish doesn't do anything, but apt-get ***install*** bluefish will.
Also check out applications -> add/remove programs, it's a graphical application for installing programs.

---

### Post by zvacet on 2008-02-29
Check that you have all repos open in sysem>admin>software sources check all boxes under Ubuntu software and under updates tab.Reload.In terminal 

```
sudo apt-get install bluefish
```

---

### Post by 3rdalbum on 2008-02-29
Bluefish is a code-based HTML editor; you pretty much need to know HTML already. If this is going to be your first web page, you should try Kompozer.

```
sudo apt-get install kompozer
```

---

