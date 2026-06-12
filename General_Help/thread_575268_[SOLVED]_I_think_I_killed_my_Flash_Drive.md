---
title: "[SOLVED] I think I killed my Flash Drive"
date: 2007-10-13
forum: General Help
---

### Post by -grubby on 2007-10-13
OK, so I have a 32 MB flash drive from Memorex. It was fine until today. I was going to back up to it, when I accidentally knocked it out of the USB port. So I remounted it and deleted all the files on the flash drive. the files (documents) got deleted but in the ./trash folder there is a ./trash100 that I can't write (or delete) to. In fact I don't have permissions anymore to write to the whole flash drive . I checked the flash drive and it is indeed set to the "unlocked" postion. If I can't fix it then I'll just buy a new one for $5.00

---

### Post by -grubby on 2007-10-13
well?

---

### Post by ryanVickers on 2007-10-13
try viewing it with the live CD - it has even more power than root on the regular system ;)

Also, if it's a Linux filesystem (which I would automatically doubt if it's corrupt ;)) is run fsck on it

---

### Post by PmDematagoda on 2007-10-13
Did you try viewing the USB drive using:-

```
gksudo nautilus
```

or 

```
gksudo konqueror
```

or 

```
gksudo thunar
```

?

---

### Post by Nesman on 2007-10-13
Take $10 to OfficeMax and get a 512 stick.  They have them in a candy bowl at my local store by the register.

Outside of that, see if you can delete the files as root.
From command prompt, try something like: 
sudo rm -rf .trash100

---

### Post by ryanVickers on 2007-10-13
if that doesn't work, try the live CD - it has even more power some how ;)

---

### Post by -grubby on 2007-10-13
> **Nesman said:**
> Take $10 to OfficeMax and get a 512 stick.  They have them in a candy bowl at my local store by the register.

Outside of that, see if you can delete the files as root.
From command prompt, try something like: 
sudo rm -rf .trash100

I've never heard of OfficeMax! I live in a city of 2000! The ONLY technical store in this town is RadioShack. They are VERY overpriced. Otherwise I can go 21 miles to WalMart to buy one.

---

### Post by -grubby on 2007-10-13
> **PmDematagoda said:**
> Did you try viewing the USB drive using:-

```
gksudo nautilus
```

or 

```
gksudo konqueror
```

or 

```
gksudo thunar
```

?

i've tried thunar and nautilus lets try Konqueror! NOPE

---

### Post by PmDematagoda on 2007-10-13
Did you try to format it using Gnome partition editor?

---

### Post by -grubby on 2007-10-13
> **PmDematagoda said:**
> Did you try to format it using Gnome partition editor?

just a second..

---

### Post by -grubby on 2007-10-13
OK thanks!!! I formated it to Fat16(original filesystem) but it only has 23.4 MB of space. I'll try reformatting. Can't go Fat32 because it requires 32 MB of space. Well whatever I'll just keep it at 23.4 MB of Space I don't use the other space anyway..nevermind That's how much the formatting requires

---

### Post by -grubby on 2007-10-13
how do I mark this as solved?

---

### Post by PmDematagoda on 2007-10-13
Thread Tools:)

---

