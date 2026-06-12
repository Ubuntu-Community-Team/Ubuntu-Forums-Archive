---
title: "Lenovo 100S hardware support in Ubuntu"
date: 2016-11-13
forum: General Help
---

### Post by zachg2 on 2016-11-13
I consider buying a Lenovo 100s for some programming goodness

How is the driver support?

I think we gonna have the same UEFI x86 Problems that Asus Asus X205TA has

---

### Post by wildmanne39 on 2016-11-13
There should not be any trouble with driver issues but it does depend what hardware is in the one that you buy so without knowing that we can not be for sure. 

The newer the hardware the more likely there will not be a driver for wifi yet for ubuntu.

---

### Post by zachg2 on 2016-11-13
> **Wild Man said:**
> There should not be any trouble with driver issues but it does depend what hardware is in the one that you buy so without knowing that we can not be for sure. 

The newer the hardware the more likely there will not be a driver for wifi yet for ubuntu.

Well Chipset wise it has the same chipset  as  Asus X205TA (Atom Z3735F                                                                                                 )

I dont know if the installation process/Wireless Drivers would be the same

---

### Post by wildmanne39 on 2016-11-13
Can you post a link the exact model you plan to buy?

---

### Post by zachg2 on 2016-11-13
> **Wild Man said:**
> Can you post a link the exact model you plan to buy?
It's this one 
[h=1]Lenovo IdeaPad 100S-11IBY (Z3735F/2GB/64GB/W10)[/h]

---

### Post by wildmanne39 on 2016-11-13
It looks like at least one person has installed ubuntu 32bit on one, they reported the wifi was not detected. If you do get one I recommend lubuntu.

---

### Post by zachg2 on 2016-11-13
> **Wild Man said:**
> It looks like at least one person has installed ubuntu 32bit on one, they reported the wifi was not detected. If you do get one I recommend lubuntu.
I'll do get one cause I need something cheap for college
Anyway I have to clarify that chipset is 64 bit but UEFI is 32bit (so I'll have to flash Debian 32bit UEFI Boot Support files into an Ubuntu 64 image  just like Asus X205TA )
There are reports on ask ubuntu
([http://askubuntu.com/search?q=+Lenovo+100S](http://askubuntu.com/search?q=+Lenovo+100S))
but no one has answered them...
Also I'am planing to install Ubuntu 64 bit,the hardware isnt that bad for it

---

### Post by wildmanne39 on 2016-11-13
The posts I found said even though it is 64bit they had to install 32bit because 64bit would not install.

---

### Post by zachg2 on 2016-11-13
> **Wild Man said:**
> The posts I found said even though it is 64bit they had to install 32bit because 64bit would not install.
I found this post
[http://askubuntu.com/questions/392719/32-bit-uefi-boot-support?noredirect=1&lq=1](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support?noredirect=1&lq=1)
So you're right
It says I have to install 32 bit Ubuntu, but the 32 bit version has no UEFI Support 
so I'll have to mod the ubuntu img with 32 bit UEFI Debian files to make it boot

Here:
[URL="http://askubuntu.com/questions/746156/hardware-problems-running-ubuntu-on-lenovo-100s-ideapad"]http://askubuntu.com/questions/746156/hardware-problems-running-ubuntu-on-lenovo-100s-ideapad
[/URL]     Drivers Problems:

[LIST=1]
[*]No sound card detected 
[*]No wifi card detected (ethernet works fine though) 
[*]No power management capabilities (battery tools don't work, but the  laptop gets charged without problems, there's just no monitoring) 
[/LIST]

---

### Post by wildmanne39 on 2016-11-13
After some time the wifi will probably be supported.

I read all of that, there are several things not working.

---

### Post by zachg2 on 2016-11-13
Ok Thanks for the help ;)

---

### Post by wildmanne39 on 2016-11-13
Your welcome!

---

### Post by zachg2 on 2016-11-13
So,
Anyone who tried this ?

---

