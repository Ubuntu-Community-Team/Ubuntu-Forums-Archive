---
title: "loading ubuntu screen"
date: 2007-03-10
forum: General Help
---

### Post by red1916 on 2007-03-10
Hi,

When ubuntu edgy is starting I get the default Ubuntu screen. With the bar in the middle that goes increasing. Kind of the one for windows.

Sorry but it reminds me just that...to windows.

Is  there a way to get the black screen that shows how all devices goes loading so if any device or thing goes wrong you see it.

Dunno if I'm clear. I apologize but still trying to get the "vocabulary" :- ( 

thanks

---

### Post by adam.tropics on 2007-03-11
Well if you like to practice your speed reading, edit your /boot/grub/menu.lst file. You will find the line in there referring to the kernel you are using, something like,
```

kernel        /boot/vmlinuz-2.6.17-11-generic root=UUID=7992b129-4b3c-43fb-9039-0b833fe1c444 ro quiet splash

``` and delete the words 'quiet' and 'splash'. When you reboot, you will get the full on text you seek!

---

