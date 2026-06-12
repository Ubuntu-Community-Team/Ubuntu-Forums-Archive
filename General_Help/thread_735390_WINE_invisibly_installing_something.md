---
title: "WINE invisibly installing something?"
date: 2008-03-25
forum: General Help
---

### Post by adn258 on 2008-03-25
I am trying to install tomb raider anniversary which according to wine has great compatability.  IT WORKS it gets done installing though and then instead of the program taking up memory on my /home drive it uses / instead which doesn't make sense I can tell it puts it on the /home because a couple percent more memory is taken up there.  Then what's worse is the LOCATION that I choose for it to be installed in on my wine Hard drive c: it isn't there at alll?   Does anyone know what's going on?

---

### Post by unoodles on 2008-03-25
your wine virutal drives are locate in /home/<username>/.wine

---

### Post by forrestcupp on 2008-03-25
You didn't type **sudo** did you?  Never type 'sudo' when using wine.  But your post is confusing.  Did it install it to /, or to /home?

---

### Post by adn258 on 2008-03-26
> **forrestcupp said:**
> You didn't type **sudo** did you?  Never type 'sudo' when using wine.  But your post is confusing.  Did it install it to /, or to /home?

dang yes I DID lol but I kind of had too because the CD image won't run unless I run it with super user privileges and IDK why but when I don't it says insert CD now please.  Wh at should I do because I don't have the CD?

---

### Post by forrestcupp on 2008-03-26
Can't you just burn the image to a CD and do it normally?  You really shouldn't be pirating stuff anyway.

If you install things through wine using 'sudo' it will set it up somewhere on your root drive instead of your default .wine directory in /home.

---

### Post by eye208 on 2008-03-26
> **adn258 said:**
> dang yes I DID lol but I kind of had too because the CD image won't run unless I run it with super user privileges
Don't confuse Windows admin privileges with Linux root privileges. WINE should never be run as root.

---

### Post by adn258 on 2008-03-26
> **eye208 said:**
> Don't confuse Windows admin privileges with Linux root privileges. WINE should never be run as root.

Thanks everyone well I will try to see what to do but does anyone know where the stuff goes like if you do it as sudo?

---

