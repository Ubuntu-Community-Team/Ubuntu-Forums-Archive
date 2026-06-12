---
title: "Synaptic won't open"
date: 2017-11-20
forum: General Help
---

### Post by geovino on 2017-11-20
Running 17.10... installed synaptic but it won't open. Never had this happen before. what causes this? How to fix?

---

### Post by Bashing-om on 2017-11-20
geovino; Hello'

> 
what causes this? How to fix? 

No gksu / pkexec ->
Integration pains with wayland .

Work-a-round: see;
[https://ubuntuforums.org/showthread.php?t=2374812](https://ubuntuforums.org/showthread.php?t=2374812)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by geovino on 2017-11-20
Thank you. it's working after running 
$ xhost +si:localuser:root

so its Waylands fault. ;)

---

### Post by ajgreeny on 2017-11-20
Yes, it is a fault, or they would say a feature of wayland; they do not really want any GUI programs to be run as root.

If you want to stay with wayland, and why not, as so far it has been no problem for my system, add that **xhost +si:localuser:root** command to your startup applications list.  

There is no need to turn it into a shell script or anything like that just add **xhost +si:localuser:root** into the command box; job done!

---

