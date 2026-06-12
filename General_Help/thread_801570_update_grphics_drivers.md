---
title: "update grphics drivers"
date: 2008-05-20
forum: General Help
---

### Post by guymn999 on 2008-05-20
i am unsure if this is the right place to post,
but i need to update my video drivers,
i know my card is integraded but idk how to find out what it is,
i believe the brand is ASUS if that is of any help
also i believe this is the product number: P48533-VM

i tried google-ing it but no luck, i might very well doing it all wrong, ima total n00b still to linux and im seeking some L337 help

---

### Post by bzoomer16 on 2008-05-20
Get envy. It's a program that you can find in either a package manager or the official envy site at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Envy should auto-detect your card and get the right driver. I use it and it's great. (P.S. the text-based mode saved my butt once...just another reason to use it)

---

### Post by ryanhaigh on 2008-05-20
Run the following command in the terminal to determine what type of graphics card you have:
```

lspci | grep VGA

```

The info may also be available from an item in the system menu, unfortunately I'm not on my ubuntu machine so can't be more specific.

---

### Post by guymn999 on 2008-05-20
well i ran envy and it didnt work
i put in the code and got back this:

Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

anyplace where i can get the driver for that?

---

### Post by ryanhaigh on 2008-05-20
The intel driver is already included in ubuntu, you are probably already running it. Unlike nvidia and ati intel releases its driver code as open source which means ubuntu can include it by default. The output of the command ```
lsmod
``` will give you all the loaded modules/drivers, you should see something related to intel in the list.

---

### Post by guymn999 on 2008-05-20
ok thanks guys, man i really need a new comp lol

---

