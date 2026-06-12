---
title: "ubuntu install"
date: 2007-07-08
forum: General Help
---

### Post by grimmjimm on 2007-07-08
I am new to ubuntu or any linux for that matter. I have been trying to install ubuntu but so far have been unable to make a boot disk that works. Can anybody explain how to make a boot disk that will work in my pc.
I run windows xp pro at the moment,i cannot boot from my cd-rom, i can only boot from a floppy.
I need somebody to explain in layman terms how to make a floppy boot disk that i can install ubuntu 7.04
to my computer. thank you all

grimmjimm

---

### Post by confused57 on 2007-07-08
> **grimmjimm said:**
> I am new to ubuntu or any linux for that matter. I have been trying to install ubuntu but so far have been unable to make a boot disk that works. Can anybody explain how to make a boot disk that will work in my pc.
I run windows xp pro at the moment,i cannot boot from my cd-rom, i can only boot from a floppy.
I need somebody to explain in layman terms how to make a floppy boot disk that i can install ubuntu 7.04
to my computer. thank you all

grimmjimm
Here's how to burn an iso:
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

Make sure to select burn as an "image", not as a data or bootable cd, and burn at a low speed(8x or less)...there should be an option in your cd burning software for burning as an image...

---

### Post by ZapperJet on 2007-07-08
The Ubuntu ISO is a 698mb file, a floppy holds 1.44mb. 

You do the math.


Cheers,
John

---

### Post by kyphi on 2007-07-08
Your computer boot sequence is probably configured to boot from floppy first and hard drive second.  You can change that in the BIOS to floppy first, CD second and hard drive last.

Your motherboard booklet should tell you how to do that but if you are not confident to tackle that just say so and you will get help.

---

### Post by az on 2007-07-08
> **grimmjimm said:**
> 
I need somebody to explain in layman terms how to make a floppy boot disk that i can install ubuntu 7.04

grimmjimm

See here:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

SBM is on the desktop cd, in the /install folder.

---

