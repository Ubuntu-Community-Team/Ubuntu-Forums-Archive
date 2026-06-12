---
title: "installing scanner"
date: 2019-04-19
forum: General Help
---

### Post by jarp53 on 2019-04-19
I'm trying to install my scanner in Ubuntu 18.04  , i have always had success using this  [https://easylinuxtipsproject.blogspot.com/p/brother-printers.html](https://easylinuxtipsproject.blogspot.com/p/brother-printers.html)  ; but when I got to this part 
```
xed admin:///lib/udev/rules.d/60-libsane1.rules
``` 
 terminal result was that command not found ; like  I said I done this many times with no problem so because is 18.04 there must something different . can some one help please .

---

### Post by lutty2029 on 2019-04-19
Can you post a screenshot of your terminal running the command?

---

### Post by deadflowr on 2019-04-19
On Ubuntu switch out xed for gedit.
xed is a Linux Mint text editor and not within Ubuntu's ecosystem.
Ubuntu uses gedit.

(You can add a 3rd party repository (PPA) which has xed:
[https://launchpad.net/~embrosyn/+archive/ubuntu/xapps]("https://launchpad.net/~embrosyn/+archive/ubuntu/xapps")
if you really want, but gedit will do the job at hand fine.)

---

### Post by brian_p on 2019-04-19
> **jarp53 said:**
> I'm trying to install my scanner in Ubuntu 18.04  , i have always had success using this  [https://easylinuxtipsproject.blogspot.com/p/brother-printers.html](https://easylinuxtipsproject.blogspot.com/p/brother-printers.html)  ; but when I got to this part 
```
xed admin:///lib/udev/rules.d/60-libsane1.rules
``` 
 terminal result was that command not found ; like  I said I done this many times with no problem so because is 18.04 there must something different . can some one help please .

We are unfamiliar with the make and model *my scanner* for your device.

---

### Post by jarp53 on 2019-04-20
thanks i use gedit  and that work

---

