---
title: "Help with triple boot"
date: 2007-05-02
forum: General Help
---

### Post by telovoyagarcar on 2007-05-02
I have Feisty, Vista and XP installed in my machine and i am going nuts trying to make XP work again.
I can select the 3 options from grub..
Ubuntu boots fine, the vista boot loader also works.. but the XP option gives me a black screen and nothing else.

I checked the /boot/grub/menu.lst and the output from the df command, and the entry in the grub menu is right, on /dev/sda4.

And then i tried changing the partition number in the boot.ini file to 1, 4, 5, 6, 7, and 8 and still no luck.
I have the 3 necesary files for xp to boot in that partition, boot.ini, ntdetect.com and ntldr.

i think that maybe my problem is the way i have partitioned my disk.. looks like a mess.. but it should work.
here is the picture of my disk management in vista so you can see whats going on:

[IMG]http://img451.imageshack.us/img451/1199/particionesxy1.jpg[/IMG]

C, E, D, and F are NTFS partitions... and XP is installed on the Wingames (F:). That is the one im trying to boot.

The other partitions without letters 14gb and 690mb are ubuntu and the swap partition..
the temp partition is a logical drive that i created so i could make more than the 4 limit  partitions to be able to install ubuntu.
do any of you have any experience on this?

thanks a lot

---

### Post by confused57 on 2007-05-02
You might need to hide your Vista entry from XP:
```
title     Microsoft Windows 95
hide      (hd0,1)
unhide    (hd0,0)
root      (hd0,0)
savedefault
makeactive
chainloader +1

title      Microsoft Windows 98SE
unhide     (hd0,1)
hide       (hd0,0)
root       (hd0,1)
savedefault
makeactive
chainloader +1 
```

The above are just examples taken from this site, but might give you a possible idea:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

