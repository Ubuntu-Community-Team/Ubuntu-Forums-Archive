---
title: "firefox crashing randomly (it seems)"
date: 2007-07-08
forum: General Help
---

### Post by BoneSaw on 2007-07-08
so for some reason firefox has been crashing about every 5-20 min i cant figure out what causes it. i tried reinstalling it in synaptic but no help there. i ran it in terminal and came out with this 
```
bonesaw@monarch:~$ firefox
/home/bonesaw/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/bonesaw/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/bonesaw/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x813b7c8: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x813b7c8: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x813b7c8: NP_GetValue
GCJ PLUGIN: thread 0x813b7c8: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x813b7c8: NP_GetValue return
GCJ PLUGIN: thread 0x813b7c8: NP_GetValue
GCJ PLUGIN: thread 0x813b7c8: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x813b7c8: NP_GetValue return
Segmentation fault (core dumped)
bonesaw@monarch:~$ 

```

it crashed after about 10 min here. any suggestions?

---

### Post by jwh400 on 2007-07-08
List the extensions and themes you're using. Are any of them recent additions?

---

### Post by Vajra Vrtti on 2007-07-08
Extensions could cause that. Disable all extensions and then enable them one by one to check it.

---

### Post by BoneSaw on 2007-07-08
adblock plus, foxmarks, foxytunes, google desktop for firefox (this is new, i disabled it just now and ill see if that helps) and speed dial (installed after crashes began)

the only other thing i can think of that i did recently was install the java plugin, so i removed that too.

---

### Post by Vajra Vrtti on 2007-07-08
Check them all. I've already have Firefox randomly crashing in pages containing javascripts and that turn out to be caused by an innocent extension named CuteMenus.

---

### Post by BoneSaw on 2007-07-08
well it was one of those two things (im thinking google). it isnt crashing now. thanks for the help guys.

---

### Post by jwh400 on 2007-07-08
It should be safe to reinstall your java plug-in.

---

