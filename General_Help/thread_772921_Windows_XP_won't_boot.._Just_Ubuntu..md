---
title: "Windows XP won't boot.. Just Ubuntu."
date: 2008-04-28
forum: General Help
---

### Post by RSahlgren on 2008-04-28
I installed Ubuntu 8.04. I already had Windows XP installed. So I don't want to "lose" it. So i installed on my other hard drive. It won't boot. I have tried the start up thing there you can setup bios ans choose which thing to boot. I choose the hard drive that windows is installed on. And it still comes to Ubuntu's boot menu. I can see the windows files and such, in Ubuntu.

It would be nice to get help with this problem.

---

### Post by TheLions on 2008-04-28
you'll need to edit grub menu...

to edit it type ```
sudo gedit /boot/grub/menu.lst

```

and on end add[PHP]title		Windows Vista/Longhorn (loader)
root		(hdX,Y)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1[/PHP][

where X is drive number and Y partition number...
eg. XP is on 2nd drive and first partition then you need to put (hd1,0)

also copy here output of ```
sudo fdisk -l
```

---

### Post by ugm6hr on 2008-04-28
It sounds like you installed GRUB (the bootloader) onto the Windows HD, and GRUB hasn't automatically detected the Windows partition.

As stated, menu.lst need to be edited.

---

### Post by RSahlgren on 2008-04-28
Woops.. look at post below.

---

### Post by RSahlgren on 2008-04-28
Here is the sudo fdisk output:
```
Disk /dev/sda: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x00012547

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1       29644   238115398+   7  HPFS/NTFS
/dev/sda2           29645       30401     6080602+   5  Utökad
/dev/sda5           29645       30401     6080571   82  Linux växling / Solaris

Disk /dev/sdb: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x4dcd77fb

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               1       30401   244196001   83  Linux
```

It's in swedish..

Also I got some error: it was like error 23: <insert something here>.

---

### Post by RSahlgren on 2008-04-28
Sorry but i need to bump this..

---

### Post by ugm6hr on 2008-04-29
The fdisk output confirm the following:

sda has Windows, with a Linux swap partition at the end.
sdb has Linux.

This is an unusual setup.  Ubuntu shouldn't normally do this as default.

Did you manually partition when you installed?

Show us the contents of the file /boot/grub/menu.lst
```
gedit /boot/grub/menu.lst
```

---

