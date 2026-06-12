---
title: "Hello . i Need Help to find my DVD drive Location"
date: 2012-12-03
forum: General Help
---

### Post by CCgirl6690 on 2012-12-03
Hello everyone
 (Please move my topic if its not in the right place thank you)
im trying to burn a backup game and im stuck ,  this is the command i must use  
```
growisofs -use-the-force-luke=dao -use-the-force-luke=break:2133520  -dvd-compat -speed=2 -Z /dev/sr0=/path/to/game.iso
```but i cant find my DVD drive Location . im on a laptop and i have 2 cd drives one internal and one external which is connected via USB . 
im trying to use the External Drive . however when i put a cd in each drive to find its location  to put in that command . both drives give me /media  , i am on ubuntu 12 latest .
would someone please help me find my Drive Location to replace with  /dev/sr0 . please?  
thank you so much

---

### Post by mc4man on 2012-12-03
try
/dev/sr1

With the usb drive connected this will give /dev links, look in  *-cdrom sections
```
sudo lshw -C disk
```

---

### Post by Cheesemill on 2012-12-03
Or you can use the 'mount' command to see the name of the devices currently mounted in /media.

---

### Post by CCgirl6690 on 2012-12-03
> **mc4man said:**
> try
/dev/sr1

With the usb drive connected this will give /dev links, look in  *-cdrom sections
```
sudo lshw -C disk
```

thank you so much , it helped alot , it was sr1 .
but now im getting this error,  can you help me please ?  thanks
```
/dev/sr1: splitting layers at 2133520 blocks
:-[ SEND DVD+R DOUBLE LAYER RECORDING INFORMATION failed with SK=5h/INVALID FIELD IN PARAMETER LIST]: Input/output error
none@None:~$ 
 
```

---

### Post by CCgirl6690 on 2012-12-03
nvm i fixed it .  i needed to omit  2 parts of the command , but thank alot for helping

---

