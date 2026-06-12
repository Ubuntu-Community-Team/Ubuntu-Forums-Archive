---
title: "Problem with wine 0.9.42"
date: 2007-07-31
forum: General Help
---

### Post by nu buntu on 2007-07-31
Ok, I just upgraded to wine 0.9.42 and I tried to type winecfg in the terminal, this is what I got...

```
wine client error:c: version mismatch 306/307.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?
```

Also, none of my programs will run, I get the same error as above.  Does anyone know how to fix this?

---

### Post by nitro_n2o on 2007-07-31
according to your error message you still have the old process running.. 
try killing the process then start your new wine 
do```
 ps aux | grep wine
``` to know the process number then ```
kill -9 <process number that you found>
```

---

### Post by nu buntu on 2007-07-31
ok, i see all these numbers

```
mike     11774  0.0  0.1   4444  1976 ?        Ss   10:26   0:22 /usr/bin/../lib/../bin/wineserver
mike     26161  0.0  0.0   2884   756 pts/0    R+   16:50   0:00 grep wine

```

what one is the right one?

EDIT: LOL.  This morning, I tried to get Counter-Strike Source to work but it kept crashing before I entered the server.  So I just quit it and kept using my system.  I haven't shut it down/rebooted so it was still running hl2.exe from like 8 hours ago.  That fixed my problem, thanks.

---

