---
title: "I can't log in!"
date: 2007-05-21
forum: General Help
---

### Post by stee on 2007-05-21
I'm running Kubuntu 7.04. Suddenly, I cannot log in! Everything worked well when I used my computer to surf on the web last night. Now, I type in my password and the screen goes black, then I see my mouse icon, and woomp - back to the login screen.
I am able to start KDE by using the recovery mode, logging in as root and typing "startx".

What?! How?! Why?!

---

### Post by total wormage on 2007-05-21
is there the possibility that you ran out of disk space?
try to run
```
df -h
```
in a terminal, it will spit out some info about your harddisks :]

---

### Post by anaconda on 2007-05-21
Has your password changed?

just boot to recovery mode and give yourself a new password.
```
passwd your_user_name
```

---

### Post by stee on 2007-05-21
> **total wormage said:**
> is there the possibility that you ran out of disk space?
try to run
```
df -h
```
in a terminal, it will spit out some info about your harddisks :]

I found out that i had in fact done that, on my home-partition. I downloaded some video files via bittorrent while I slept, and they had eated up all the space on my computer. Now I deleted them, and I can log in, but something weird happens; I only get a console window! From there I am able to start programs fine, but they don't have menu lines or borders. It's so weird. Everything works fine if I startx as root.

---

### Post by total wormage on 2007-05-21
> **stee said:**
> I found out that i had in fact done that, on my home-partition. I downloaded some video files via bittorrent while I slept, and they had eated up all the space on my computer. Now I deleted them, and I can log in, but something weird happens; I only get a console window! From there I am able to start programs fine, but they don't have menu lines or borders. It's so weird. Everything works fine if I startx as root.

oh that shouldn't happen, did you already try to completely restart your computer?

---

### Post by stee on 2007-05-21
haha, only like 10 times. ;)

i'm not a complete idiot! (just partly)

---

### Post by total wormage on 2007-05-21
> **stee said:**
> haha, only like 10 times. ;)

i'm not a complete idiot! (just partly)

hehehe :]
hey do you see grub loading somewhere during boot? or does a grub menu pop up somewhere?
if you don't see the menu you should hit some button, f10 i think or esc, i don't know it states which button to press.

try to select a non recovery option.

if that doesn't work i think you have a grub problem OR some troubles with autostarted programs, how to fix that i don't know... might be you'll need to led dpkg configure xorg.
(i apparently am i a very non-helping mode hehe sorry for that)

---

### Post by stee on 2007-05-21
> **total wormage said:**
> hehehe :]
hey do you see grub loading somewhere during boot? or does a grub menu pop up somewhere?
if you don't see the menu you should hit some button, f10 i think or esc, i don't know it states which button to press.

try to select a non recovery option.

if that doesn't work i think you have a grub problem OR some troubles with autostarted programs, how to fix that i don't know... might be you'll need to led dpkg configure xorg.
(i apparently am i a very non-helping mode hehe sorry for that)

Grub was working perfectly. Anyway, you led me to find a solution to my problem:
I removed xorg and installed it again. Simple as that! 
Now everything finally works like a charm.

thanks for the help

---

### Post by total wormage on 2007-05-21
> **stee said:**
> Grub was working perfectly. Anyway, you led me to find a solution to my problem:
I removed xorg and installed it again. Simple as that! 
Now everything finally works like a charm.

thanks for the help

great to hear so :]
good luck on the downloading :p

though it bothers me why this thing happened, i wonder if the full disk had something to do with the screwed up xorg...

---

### Post by stee on 2007-05-21
darn!

it only works if I - from the kdm login screen - choose to log on in konsole mode
then i run startx (as a normal user) and everything is fine.
obviously this starts X without going through kdm

if i log in normally from kdm, i get the same silly problem as before

---

### Post by stee on 2007-05-21
now i've installed gdm as a workaround, and i can log in fine. 

the problem seems to lie in going from kdm to X...

edit:
okay, i installed gdm, then reconfigured to use kdm and then removed gdm

now everything is back as it was. how odd.

---

