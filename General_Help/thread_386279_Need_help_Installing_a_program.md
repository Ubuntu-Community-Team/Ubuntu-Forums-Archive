---
title: "Need help Installing a program"
date: 2007-03-16
forum: General Help
---

### Post by AnthonyJK@gmail.com on 2007-03-16
I want to install this program from [this site]("http://desrt.mcmaster.ca/macbook.xhtml") but I'm not even sure where to start can anyone help?


```
Backlight Control

    


     Not supported in Dapper as per default, so I reverse engineered the
     AppleIntelIntegratedFramebuffer.kext kernel extension and found the
     memory address of the register responsible for controlling it.
    

    


     After experimenting with poking random values at it I wrote a program
     which controls it.  This program is a temporary hack. I've also added
     support for macbook backlight control to HAL (patch awaiting upstream
     approval) since this is the proper fix.  See
     Launchpad #72287 for more
     information.
    

    


     You can download the C source for the program here:
     Macbook Backlight Control.  You need to link against libpci with -lpci.  Make sure you
     have pciutils-dev installed.  If you want to use the old version that
     has the hard-coded video card address (and does not require libpci), it
     is still available in the same directory, called macbook-backlight-old.c.
    

    


     If you intend to use the program as a normal user you'll have to install
     it setuid root as it needs access to /dev/mem to function.
    

    


     note: this program does not work for macbook pro -
     only macbook.
    

    


     update: The program now automatically detects the video
     card address via libpci.
```

Thank you!

---

### Post by Kateikyoushi on 2007-03-16
This page has infor how to add his repository to your sources list and install the program. [LINK]("http://desrt.mcmaster.ca/dapper.xhtml")

---

