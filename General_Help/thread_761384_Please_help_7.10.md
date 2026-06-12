---
title: "Please help 7.10"
date: 2008-04-21
forum: General Help
---

### Post by popo_joe on 2008-04-21
hi i just downloaded and burnt on a CD ubuntu 7.10 desktop edition 32bit, and when i start the install everything works fine until i get these messages :
(it just freeze there and nothin happens)

*Starting deferred execution scheduler atd [OK]
*Starting periodic command scheduler crond [OK]
*Checking battery state [OK]
*Running local boot scripts(/etc/rc.local) [OK]

and then OMG nothing happens i press ENTER i don't get anything the machine just stops there and doesn't do anything.
i have VISTA installed and just trying to make a dual boot with ubuntu but i atleast need to make the install work -_-
Please help!

my specs : 
Q6600
8800 GT
2gb ram

---

### Post by ryanhaigh on 2008-04-21
Because your graphics card is so new (in terms of ubuntu release date its still pretty new) and as far as I know is not supported by the open source nv driver, the graphics system, calld X or xorg cannot start because it cant use your card. You could try starting with safe settings from (i cant remember if thats what it says exactly) from the livecd menu, or you can grab the alternate cd image which is a text based installer but is not particularly difficult. Or you can figure out how to install the proprietary nvidia driver in the livecd environment then install the system (after which you will still have to reinstall the nvidia driver).

---

### Post by popo_joe on 2008-04-21
i did finally chose to use the alternate CD! but i got a new problem while resizing my main partiton, as soon as i launch the resize it pops an error message saying an error has occured while writing data to the disc (( something like that )
anyone have an idea?

---

### Post by ryanhaigh on 2008-04-22
You could try using vistas disk management tools to resize the partition, from what I understand that is what is recommended.

---

