---
title: "Can't type my password in Terminal"
date: 2014-04-03
forum: General Help
---

### Post by eamonnsmith on 2014-04-03
I had been trying to install software (makemkv) via Terminal, and it seemed to be going o.k. until I was asked for password. The cursor then turned to a flashing white box, and I cannot get it to respond to my keyboard. I am mystified because commands at earlier stages in the process were entered without difficulty. Can anyone suggest where my problem is?

---

### Post by QIII on 2014-04-03
That is a normal security feature.  Just carefully type your password.  It will not be echoed in the terminal, but is is being accepted.

---

### Post by Double.J on 2014-04-03
Hi there! 

As described above it's supposed to be like that by default so people can't see how long your password is. It also means that there's no way to copy information out of the terminal screen.

it is possible to enable this if it is absolutely required such as an assistive and/or access issue for the user. You have to edit the /etc/sudoers.tmp file. you can only open it in vi, so it's back it up
```
 sudo cp /etc/sudoers.tmp /etc/sudoers.tmp.backup
```
then open it with vi with privileges
```
 sudo visudo
``` 
then find the line at the top 
```
 Defaults env_reset
```
and change it to 
```
 Defualts env_reset,pwfeedback
```

as I say it's not advised but I have enabled it before for a user with accessibility requirements.
Jj

---

### Post by Impavidus on 2014-04-03
Back in Ubuntu 6.06 there wasn't any feedback even when typing your password in the GUI. I liked it that way.

But indeed, it's standard behaviour. Just watch your keyboard, not your screen, whilst typing.

---

### Post by eamonnsmith on 2014-04-04
Thank you all for your prompt help. Problem solved.:redface:

---

