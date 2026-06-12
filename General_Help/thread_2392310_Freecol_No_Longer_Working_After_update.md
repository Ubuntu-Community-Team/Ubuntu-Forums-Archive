---
title: "Freecol No Longer Working After update"
date: 2018-05-19
forum: General Help
---

### Post by ehud2 on 2018-05-19
I updated from Xubuntu 17.10 to Xubuntu 18.04.

Everything works that worked before (I'll have to start a whole new topic on why I worded it that way) except Freecol.

I have totally uninstalled Java and all the bells and whistles, uninstalled Freecol, but when I re-installed it I got the following message;

[[IMG]http://i247.photobucket.com/albums/gg152/strangerandapilgrim/Screenshot_2018-05-19_09-51-35.png[/IMG]](http://s247.photobucket.com/user/strangerandapilgrim/media/Screenshot_2018-05-19_09-51-35.png.html)

Little help here? :-D

Thanks!

---

### Post by Holger_Gehrke on 2018-05-19
The option '-Xincgc' has been deprecated. It was used to set incremental garbage collection for the  java VM. If 'freecol' is a shell script (use 'file  $(which freecol)' to find out), you can simply edit it and remove that  option to run freecol with the standard garbage collector or replace it  with an option to select one of the garbage collection methods still supported. 

Holger

---

