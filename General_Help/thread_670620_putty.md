---
title: "putty"
date: 2008-01-17
forum: General Help
---

### Post by taimur on 2008-01-17
hi i m using my server remotly by putty through ssh the problem i m running two type of applications on it 

one is like this there is a command to run the application and suppose if i close my putty the program don't stop it is working internally and if i want to stop the progarm i have to use killall to stop the program 
this is ok i want it like that

and the other apllication is not like this when i start the application it works but when i close putty it also get close i don't want it to get close 
that's plz help me out

---

### Post by iowa on 2008-01-17
I would use screen with both apps. Good luck.

[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)

---

### Post by mathisdermaler on 2008-01-17
> **taimur said:**
> 
and the other apllication is not like this when i start the application it works but when i close putty it also get close i don't want it to get close 
that's plz help me out

My SSH is rusty but I think if you launch it in the background and redirect stdout and stderr then you can disconnect the ssh session and it will continue to run.  If "foo" is your application you want to continue running, when running "foo" launch it like this:

```

taimur:~$ foo >/dev/null 2>/dev/null &

```

(When running like this you won't see any output of course--I'm assuming this is something you want to run in the background.)

---

### Post by taimur on 2008-01-26
hi
i can't what you say
it is like that cd taimur  and theni type exucation command  ./cc -d
like this how to open this?

---

