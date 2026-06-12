---
title: "Ubuntu Server hangs at &quot;Loading hardware drivers&quot;"
date: 2007-06-01
forum: General Help
---

### Post by SuperJason on 2007-06-01
My server runs GREAT with 2GB of RAM.  However, adding 2 more gigs causes Ubuntu to hang at the "Loading Hardware Drivers" screen.

It booted fine in XP, but I didn't use it much to determine if it was stable.

I tried 2 different kinds of RAM, and if I use any 2 sticks of RAM, it works fine.  All the ram is the same brand, and passes with Memtest.

Here is my motherboard:
[http://www.newegg.com/Product/Product.asp?Item=N82E16813128012](http://www.newegg.com/Product/Product.asp?Item=N82E16813128012)

Here is my memory:
[http://www.newegg.com/Product/Product.asp?Item=N82E16820231098](http://www.newegg.com/Product/Product.asp?Item=N82E16820231098)

I've tried the following:
- Moving the memory around, and even swapping some chips with another brand
- Changing the memory timings
- Changing the memory voltage (still within spec)
- Trying a different motherboard (same model, different board)
- Trying recovery mode (no messages displayed when it stops)
- Trying the Live CD, Ubuntu 64, Ubuntu 32, Cent OS

Please help!  I really need 4gb of RAM!

---

### Post by SuperJason on 2007-06-01
Just tried 3 sticks, that works as well.  It just doesn't like 4 sticks of RAM!

What do I do now?

---

### Post by dirichs on 2007-06-05
Got the same problem, using the Asus P5B Deluxe motherboard:
[http://www.asus.com/products4.aspx?modelmenu=2&model=1179&l1=3&l2=11&l3=307&l4=0]("http://www.asus.com/products4.aspx?modelmenu=2&model=1179&l1=3&l2=11&l3=307&l4=0")

Runs fine with one module of 2G of memory, hangs at "Loading hardware drivers" with 4G. Each module by itself operates fine, so I assume that there is no hardware memory error causing the problems.

The system also starts fine with 4G of RAM if memory remapping is disabled via the BIOS. This configuration ends up with only around 3G usable by the OS, which is certainly sub-optimal.

To track down the problem you may boot with different kernel parameters, editable via grub. Removing "quiet splash" from the kernel start options causes the kernel to print out some more details during startup.

For me, the startup process ends during the initialization of the "agpgart" module. The last regular messages is:
```

agpgart: Detected an Intel 965G Chipset.

```

After that there may come 0-2 varying error messages, right now I have:
```

iTCO_vendor_support: vendor-support=0
modprobe[4119] trap invalid opcode rip:402040 rsp:7fff92946018 error:0

```
Another time there was a segfault reported by modprobe[4036] as the last message.

I also tried to disable loading the agpgart during startup, using the kernel parameter "agpgart.blacklist=yes". In this case, instead of hanging, the system directly initiated a reboot.

---

### Post by dirichs on 2007-06-05
Maybe I should mention the Ubuntu version I tried: It is ubuntu-7.04-desktop-amd64.

---

### Post by dirichs on 2007-06-05
Ok, at least for me the problem seems to be resolved. This thread gave me the key hints:
[http://ubuntuforums.org/showthread.php?t=375853]("http://ubuntuforums.org/showthread.php?t=375853")

The solution was to add "blacklist intel_agp" to /etc/modprobe.d/blacklist.

I had no problems with the jMicron controller (that is the other potential source of problems often reported with regard to the Asus P5B).

SuperJason, I am not sure if this solution also applies to your motherboard, but perhaps it's worth a try.

---

