---
title: "Change text size in ttys..."
date: 2007-04-26
forum: General Help
---

### Post by rich.bradshaw on 2007-04-26
Hi,

I realise that appending vga=XXXXX to the kernel line in grub changes the size of the text in the ttys, but on my laptop with 1400*1050 resolution this doesn't seem to work , I don't know which value I need to put after vga in order to make it the right size - any one know where to find this info?

---

### Post by chrisccoulson on 2007-04-26
I've got a table with some values in. I'm not sure how correct they all are, as these values have come from different sources over time. Have a look in the attached openoffice document.

---

### Post by rich.bradshaw on 2007-04-27
Thanks, looks useful!

I tried doing the one I thought was right, vga=0x342 , but it didn't work - said it was an unspecified value, then asked me to choose a mode. I chose 6, and it works, but how to get it do that automatically?

---

### Post by rich.bradshaw on 2007-04-27
Aha, you have to convert it from hex to decimal.

In case anyone else wants to do this,

[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

has all the details.

To convert hex to decimal:

perl -e "print hex(NUMBER WITHOUT 0x);"

for instance I want 0x342, so

perl -e "print hex(342);"

to get in decimal.

---

### Post by chrisccoulson on 2007-04-27
Yes, sorry - I forgot to mention that you need to change it to decimal

---

