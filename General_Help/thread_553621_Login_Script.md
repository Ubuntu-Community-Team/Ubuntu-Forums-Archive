---
title: "Login Script"
date: 2007-09-18
forum: General Help
---

### Post by Pepsta on 2007-09-18
Hi All,

came across a previous thread where someone posted a way to create a script which will load certain applications with a time delay. Unfortunately I can't find that thread anymore no matter what I thought it was under.

Reason why I'd like to do this is because I am running Compiz Fusion and AWN, but on startup it seems that AWN loads either at the same time or just before and it looks crappy, I notice that when I load up without AWN then run it after all is loaded especially Compiz Fusion it loads up fine.

Any ideas are greatly appreciated.

Thanks.

---

### Post by JinxAu on 2007-09-18
Gday Pepsta,

I can't recall the exact name of the file that starts up applications when you login... I think it's .xsession (placed in your home folder), with a command like:
```
sleep 20 && awn &
```

You could also try using System -> Preferences -> Sessions and adding AWN to your Startup with the command of:
```
sleep 20 && awn
```

Sleep makes it wait for 20 seconds, then execute awn (just make sure that is the correct command to execute to get awn running).

Cya round
Jinx

---

### Post by Pepsta on 2007-09-19
Thanks mate, I couldn't get it goin the way you described but your info was exactly what I needed and led me to the right path of creating a .sh file and using the sleep command in it with  awn and adding that to sessions.

Cheers.

---

