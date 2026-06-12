---
title: "Autostart Ventrilo (or anyother thing) on start up"
date: 2007-03-01
forum: General Help
---

### Post by chris.snafu on 2007-03-01
Ive got everything working, ressurected an old computer with Xubuntu, and got a stable ventrilo server set up. prob is, i have to start vent manualy, 

anyone know how i could start it auto when i start up my comp? 

the command to start it is

(open terminal)
```
cd ventrilo
./ventrilo_srv
```

and it starts. is there a way to have this run in terminal once xfce is started?

i was messing around with autostarted applications, but i couldnt get it to work.

Thanks for any help you can give.
(server comp specs are in sig)

i know i can just leave it on, and it probly wont crash, but i want to be able to turn it off, and come back later (save power) and just press the button... and 5-8 mins later be able to connect to it.

---

### Post by janz84 on 2007-03-02
I don't know about xfce but in gnome it's in system -> preferences -> sessions

---

### Post by Jphenow on 2007-03-02
I would also be curious to know how one would do this in KDE just for future reference

---

### Post by po0f on 2007-03-02
chris.snafu,

If this is something you want started at boot time (it should run even if no one is logged in), add the command to /etc/rc.local.  If it's something you want running only when a certain user is logged in, use janz84's solution.

[EDIT]

Note that the commands that are run from /etc/rc.local are run with root privileges, be careful.


Jphenow,

I believe you just create a script in ~/.kde/autostart, but I haven't used KDE in months.  :)

---

### Post by chris.snafu on 2007-03-03
ok, ive got rc.local open, but what do i put in it?

its got # comments, then non commented Exit 0

---

