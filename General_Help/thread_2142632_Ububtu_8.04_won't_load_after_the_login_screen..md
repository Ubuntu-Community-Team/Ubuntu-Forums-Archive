---
title: "Ububtu 8.04 won't load after the login screen."
date: 2013-05-06
forum: General Help
---

### Post by youseeff on 2013-05-06
Hello everyone

I'm having a problem with my ubuntu, now it won't load after the login screen it just a black screen and i guess i know what caused that problem but i don't how to fix it.
Today i found my internet doesn't work, anyway i missed with terminal after i put this code
>  gksu gedit/etc/NetworkManager/NetworkManager.conf 

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

Then 
> gksudo gedit /etc/NetworkManager/nm-system-settings.conf
 [ifupdown]
managed=false

so is their anyway to recover this and fix it?

---

### Post by fantab on 2013-05-06
Seriously, are you still using 8.04? It reached its [end of life]("https://wiki.ubuntu.com/Releases") in May 2011. or is the server edition, which will reach its eol this month. Install the latest available Ubuntu versions.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by youseeff on 2013-05-06
Ok dude.
First I like my classic ubuntu and second Ubuntu 12 and 11 is not for my style .
Anyway thanks for the reply.

---

### Post by fantab on 2013-05-06
There other alternatives to Unity which you obviously don't like. My suggestion install Cinnamon or Gnome-classic to get the feel of older Ubuntu. Or you can try Kubuntu or Xubuntu.

---

### Post by youseeff on 2013-05-06
Thank you my friend
I guess i'll install Ubuntu 12.04 then Gnome-classic
The reason why i hate the new Ubuntu is the Unity interface.

---

