---
title: "[SOLVED] Conky startup session weather forecast"
date: 2008-07-02
forum: General Help
---

### Post by Kevbert on 2008-07-02
Hi.  I'm very new to conky and want to run a script automatically at startup.
I'm using a slightly modified script (attached) which displays a system monitor and weather.  I've set conky to run automatically in Sessions and the weather does not display (it runs fine if I run it manually from terminal).  Does anyone know how to get this to work ?  Do I need to add a time delay to allow my wireless adapter to connect to the web ? :(:(:(

---

### Post by Doji on 2008-07-02
save this as .startup.sh

```
#!/bin/bash
sleep 20;
conky &
```

and put it in Sessions. It'll start up conky after a delay, which will hopefully fix your problems.

---

### Post by Kevbert on 2008-07-03
Hi Doji. Thanks for the reply.  Do I need to use chmod on this script to make it executable ?  And do I need to put it in a certain directory ? (It's currently in my home directory).  I've browsed to it via the Sessions option and it still doesn't run.

---

### Post by Kevbert on 2008-07-03
In terminal entered 
```
chmod a+x .startup.sh
```
and everything works like a dream.:lolflag::lolflag::lolflag:

---

