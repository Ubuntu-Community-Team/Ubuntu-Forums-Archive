---
title: "Launch a GUI app with cron"
date: 2007-12-12
forum: General Help
---

### Post by Mramius on 2007-12-12
I'm really struggling on how to go about doing this, can anyone provide some pointers?  Thank you very much.

---

### Post by drs305 on 2007-12-12
One of the problems may be trying to invoke a gui-based app in a cron script. Try adding this to the command line:
" export DISPLAY=:0 && " before any gui based app command

So if I want to have an alarm play at 8:50 am, my cron job would look like this:
```
50 8 * * * export DISPLAY=:0 && <someapp> <somefilename> 
```

---

