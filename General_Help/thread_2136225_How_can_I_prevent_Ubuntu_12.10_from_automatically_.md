---
title: "How can I prevent Ubuntu 12.10 from automatically going into suspend mode?"
date: 2013-04-16
forum: General Help
---

### Post by jimfl on 2013-04-16
Under System Settings--Power, I've set it to never suspend, but it still automatically goes into suspend mode after maybe 30 minutes or so. Very frustrating if I'm trying to download something!!!

---

### Post by pqwoerituytrueiwoq on 2013-04-17
you could make a script that uses xdotool to press a useless key or move the mouse 1 pixle

you could run this command while you are downloading untill you find a solution
```
sh -c 'while [ 1 -eq 1 ];do xdotool mousemove_relative 1 0;sleep $((29*60));done'
```
never had that issue on xubuntu

---

