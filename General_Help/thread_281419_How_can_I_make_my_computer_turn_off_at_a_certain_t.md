---
title: "How can I make my computer turn off at a certain time?"
date: 2006-10-21
forum: General Help
---

### Post by thenetduck on 2006-10-21
Hi, 
 
 I would like to have my computer turn off at a certain time. (So I can listen to some music while I sleep, but not all night) Is there a way that I can do this? Is there a program for this? Thanks, 

 The Net Duck

---

### Post by aysiu on 2006-10-21
I don't know the exact syntax, but with the *shutdown* command, you can specify a time.

For example, ```
sudo shutdown -h **now**
``` shuts down the computer down... now.

Again, I'm not sure of the syntax for it, but I think you can substitute in a real time for *now*. Try something like this? Can anyone confirm this would work? ```
sudo shutdown -h 23:30
```

---

### Post by der_joachim on 2006-10-21
You can use the "at" command. It is probably installed already. You have to do something like ```
at -f 'shutdown -h now' 10pm
``` to shut down your computer at 10pm.

---

### Post by aysiu on 2006-10-21
Thanks for clarifying, der_joachim. I knew it could be done, but I had no idea what the proper syntax was.

---

### Post by CatKiller on 2006-10-21
Also, you can run the command like the "snooze" function of radios and the like: ```
sudo shutdown -h +60
``` The number at the end is in minutes, so that's "turn off in an hour". **man shutdown** will tell you more information about the options.

EDIT:aysiu, the man page says that your syntax is correct.

---

