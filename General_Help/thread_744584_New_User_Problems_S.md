---
title: "New User Problems :S"
date: 2008-04-03
forum: General Help
---

### Post by IzMbit on 2008-04-03
hi everybody, i am new in ubuntu and in linux also so excuse me for my questions-problems..

i installed ubuntu 7.04 and just starting updating.. then i started looking in settings etc.. i went to 
System - Administration - Users and Groups, put the root pass and logged in the pass of root was the same with the user so i wanted to change it and i changed the root pass and privilege and the user pass and privilege also. :S well now i try to reach any of the system-administration option and doesnt open. somehow i can change it as i was before? (tryed to logged off and log in as root but got error root cant log in throw this window? (something like this) 

thx in advance :)

---

### Post by wPwLUi3N on 2008-04-03
Welcome to the forums.

That's a strange problem ... are you sure you didnot made any type error while changing password. That is only possible reason come to my mind.

---

### Post by pseudo-random on 2008-04-03
TBH you shouldn't have touched the root account. Ubuntu is designed in a way that you should never in theory have to be root. Sudo will do for administration.
Root is not allowed to log in to the X server, thats why you get that error.
Can you Ctrl-Alt-F1 and reset your password with 'passwd'.

---

### Post by IzMbit on 2008-04-03
no error came out :S any way i can log in as root and fix it? i am confused :confused:

---

### Post by IzMbit on 2008-04-03
> **pseudo-random said:**
> Can you Ctrl-Alt-F1 and reset your password with 'passwd'.

i did this. now the user and the root have the same pass. this is right? i didnt khow how to get back to x server so, i restarted. i logged as user , i went to system administration and many things are lost.. and i dont have the option user and groups to change it. any way to open it somehow else?

---

### Post by pseudo-random on 2008-04-03
Morale to this story: If it ain't broke, don't try and fix it.
Pressing Ctrl-Alt-F7 will get you back to the X server normally if you're logged in elsewhere.
As for user and root having same pass: no-no.
Imagine if you got a keylogger? It wouldn't just be your user/sudo pass but your root pass as well!
Root password should be good eg. jw$jwn45r342jnr4j$f kinda sketch.

---

### Post by IzMbit on 2008-04-03
> **pseudo-random said:**
> Morale to this story: If it ain't broke, don't try and fix it.
Pressing Ctrl-Alt-F7 will get you back to the X server normally if you're logged in elsewhere.
As for user and root having same pass: no-no.
Imagine if you got a keylogger? It wouldn't just be your user/sudo pass but your root pass as well!
Root password should be good eg. jw$jwn45r342jnr4j$f kinda sketch.

how will i reach the "user and groups" to change the pass and the privileges?

---

### Post by IzMbit on 2008-04-03
well that was a bit stupid - loosing my privileges.. but anyway , just fixed with visudo :) 

thanks you

---

