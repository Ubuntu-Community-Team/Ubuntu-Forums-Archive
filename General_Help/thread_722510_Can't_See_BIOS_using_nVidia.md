---
title: "Can't See BIOS using nVidia"
date: 2008-03-12
forum: General Help
---

### Post by PopsTX on 2008-03-12
Fresh install of Gutsy.... SWEET!!  Even on an old machine!

Acquired an nVidia 5500 gfx card, anything is generally better than the onboard gfx. ( xorg.con identifies it as a GeForce 6200 !) and on install, the card was detected and works beautifully even with the box stock "nv" dirvers.  No Problem.

This machine will be used as a testing LAMP and occasional desktop work... 

Now, I'm in the process of doing some major upgrades to the machine:  Standard stuff... Power supply fans, new DVD-rw, a second HD  and the like and needed to check some BIOS settings before assembly.

Can't access the BIOS unless I unplug the monitor from the gfx card and plug back in to the onboard port.  

Not a big deal but, there's got to be a way to load the gfx card at boot... I think.  The xorg.conf file shows the proper settings and lists the card as "default..."

Would appreciate someone sending me in the right direction.

---

### Post by gobbles414 on 2008-03-12
PopsTX,

There should be a setting in your BIOS that tells your computer whether you prefer your PCs integrated graphics or a graphics card. While connected to your integrated graphics, switch the appropriate setting in the BIOS to your graphics card. Then reboot. Allow Ubuntu to start. Then shutdown. Plug your monitor into your new graphics card and attempt to access your BIOS.

Did this work for you?

---

### Post by PopsTX on 2008-03-12
> Did this work for you?  Like a Charm!

Brain fade on my part!  Thanks for the help!

If this install and machine works as long as the old Debian install on a beat up HP... I'll be back in about 5 years!  Hopefully with a not so prevalent dumb question.

---

### Post by gobbles414 on 2008-03-13
> **PopsTX said:**
> Like a Charm!

Brain fade on my part!  Thanks for the help!

If this install and machine works as long as the old Debian install on a beat up HP... I'll be back in about 5 years!  Hopefully with a not so prevalent dumb question.

I've asked more than my share of foolish questions. And this thread could help someone else in the future. So I'm glad to have helped. :)

---

