---
title: "Boot logged in, in Shell with other programmes"
date: 2008-02-18
forum: General Help
---

### Post by GodsDead on 2008-02-18
Hey there, i have been using the Desktop version of Ubuntu for a while, as a home server, mini web server, CSS Server, File storage, a bunch of stuff lol
Thing is, each time i need to reboot, or something i need to login each time, and wait for a bootup, then CTRL+ALT+F1 and kill processes etc, then run what i need to server wise..
this is getting up my ****.
i wondered, if theres a way i could boot in this shell?
but then loads my web server and whatever apps i want to start, inc main webmin, s that i can control what im doing from anywhere =]


I was thinking about gogin to the server edition, but im too ***** to =[
and i dont know that much about ubuntu or any linux distros really..

the idea, is that if i do hiccup, and want to lay back into the GUI then, im safe to do so!
that would be asuom.

Cheers guys & gals

---

### Post by pointone on 2008-02-18
You can remove or rename /etc/rc2.d/SXXgdm to prevent GDM from starting in runlevel 2 (the default runlevel). You can then start GDM manually by either running /etc/init.d/gdm start, or by switching to runlevels 3, 4, or 5.

---

### Post by GodsDead on 2008-02-19
hey cool, so how do i get some things to start up once booted, like logging me in, and then running the programmes, i only know the Terminal Commands to run them..

---

### Post by kpkeerthi on 2008-02-19
> i wondered, if theres a way i could boot in this shell?
An easy way to disable GDM in ubuntu is from System -> Admin -> Services.

> how do i get some things to start up once booted, like logging me in, and then running the programmes..
You need to add the start-up commands to .bash_login file in your $HOME directory. Create this file if it does not exist.

---

### Post by GodsDead on 2008-02-19
Thanks! =]

---

