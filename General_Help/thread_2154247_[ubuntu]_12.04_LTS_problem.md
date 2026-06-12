---
title: "[ubuntu] 12.04 LTS problem"
date: 2013-06-14
forum: General Help
---

### Post by stabwound18 on 2013-06-14
Ok so i installed ubuntu 12.04 on my hp pavilion dv5000 cpu amd turion64. I start by installing the wifi drivers and i get this black screen with some codes (im sorry for my lack of technical words) here is a pic of the screen i get. 

[http://i108.photobucket.com/albums/n39/Caba_16/2013-06-14020643.jpg](http://i108.photobucket.com/albums/n39/Caba_16/2013-06-14020643.jpg)

 i would appreciate if u guys help me thanks in advanced :-)

---

### Post by stabwound18 on 2013-06-14
ok so im installing drivers needed in my laptop and suddenly it goes to this screen 

[ATTACH=CONFIG]243810[/ATTACH]

it freezes there and theres nothing i can do. would appreciate if someone helps me :)

hp pavilion dv5000 laptop 
amd turion 64 mobile

ps.if more info is needed just let me know

---

### Post by zero2xiii on 2013-06-14
Thanks Mod: QIII

---

### Post by QIII on 2013-06-14
Threads merged.

Please do not create multiple threads with the same subject.  This dilutes the community's efforts to help you.

Thanks.

---

### Post by ahallubuntu on 2013-06-14
~

---

### Post by stabwound18 on 2013-06-14
> **QIII said:**
> Threads merged.

Please do not create multiple threads with the same subject.  This dilutes the community's efforts to help you.

Thanks.

sorry man. now i know for next time

---

### Post by stabwound18 on 2013-06-14
it was the broadcom drivers for the wifi. i need to add that any update i make to the system it does this

---

### Post by stabwound18 on 2013-06-14
> **ahallubuntu said:**
> What driver did you try to install?  Where did you get it?

Open a terminal (Ctrl Alt t) and in the terminal type these two command:

```
sudo lshw -C network
rfkill list all
```

and please give the results here.

i tried the code then connected the ethernet and opened the update maneger and gave me this [[IMG]http://i108.photobucket.com/albums/n39/Caba_16/2013-06-14161850.jpg[/IMG]](http://s108.photobucket.com/user/Caba_16/media/2013-06-14161850.jpg.html) i clicked on partial upgrade and after a while before finishing it goes to the original problem

---

### Post by stabwound18 on 2013-06-15
i keep hiting that wall. i would appreciate if someone helps me

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by stabwound18 on 2013-06-15
> **ahallubuntu said:**
> I never got a response to my question about the output of those commands.  I can't really help you if you won't respond to specific questions with the results.

ok i got the driver automatically from the system to download and it was broadcom 802.11 Linux STA

and the commands didnt work. the computer froze again in the same screen you saw. after i try to install the drivers or any update it keeps doing it

---

### Post by stabwound18 on 2013-06-15
anyone?

---

### Post by Iowan on 2013-06-15
Please allow 24 hours between bumps...

---

### Post by stabwound18 on 2013-06-17
> **Iowan said:**
> Please allow 24 hours between bumps...

ok :)

---

### Post by stabwound18 on 2013-06-19
so i try again to see if the updates install and it keep giving me the black screen with the codes :s

---

### Post by stabwound18 on 2013-06-24
?

---

