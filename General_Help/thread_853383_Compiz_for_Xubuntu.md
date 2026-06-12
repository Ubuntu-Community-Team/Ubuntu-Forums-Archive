---
title: "Compiz for Xubuntu?"
date: 2008-07-08
forum: General Help
---

### Post by racie on 2008-07-08
The Great Desktop Effects FAQ of 2008 doesn't include anything on Xubuntu.  I've installed Compiz through the Add/Remove Programs section, but don't know how to start it.  Do I need to download anything else?  Oh, and has anyone ever tried Compiz on Xubuntu?  Does it work well?  Thanks. :)

---

### Post by overdrank on 2008-07-08
> **racie said:**
> The Great Desktop Effects FAQ of 2008 doesn't include anything on Xubuntu.  I've installed Compiz through the Add/Remove Programs section, but don't know how to start it.  Do I need to download anything else?  Oh, and has anyone ever tried Compiz on Xubuntu?  Does it work well?  Thanks. :)

Hi and xubuntu, kubuntu, ubuntu are all the same under the hood although they use different DE. If you wish to start compiz-fusion you can use the alt, F2 keys and enter ```
compiz --replace
``` then you may have to add it to the sessions for start up. You can also install the fusion icon to help. Yes I have used compiz and XFCE before and still ( although the system is not running at the moment) and works just as well. :)

---

### Post by racie on 2008-07-08
Do I need to download XGl for it to work?  I just installed it and it said something like "XGl not detected.  exiting"

---

### Post by overdrank on 2008-07-08
> **racie said:**
> Do I need to download XGl for it to work?  I just installed it and it said something like "XGl not detected.  exiting"

Hi and have you run compiz check from the FAQ's and what is the model of the graphics card?

---

### Post by racie on 2008-07-08
How do you check what model the graphics card is?  I only know how from Windows.

---

### Post by sub2007 on 2008-07-08
If you installed XFCE on top of Ubuntu (ie installed Ubuntu first and THEN installed XFCE) then you will have Compiz. If you installed xubuntu from the xubuntu CD then you won't have Compiz. You will need to install it through Synaptic if you want to use it. AFAIK if you install fusion-icon then that will handle the Compiz dependencies but this isn't how I installed it so I'm not 100% sure. I installed (I think) ccsm, compiz-core and compiz-plugins. And if you want fusion-icon then that should handle your dependencies too.

---

### Post by overdrank on 2008-07-08
> **racie said:**
> How do you check what model the graphics card is?  I only know how from Windows.

HI and you can use the command ```
lspci 
``` and look for VGA.

---

### Post by racie on 2008-07-09
> **sub2007 said:**
> If you installed XFCE on top of Ubuntu (ie installed Ubuntu first and THEN installed XFCE) then you will have Compiz. If you installed xubuntu from the xubuntu CD then you won't have Compiz. You will need to install it through Synaptic if you want to use it. AFAIK if you install fusion-icon then that will handle the Compiz dependencies but this isn't how I installed it so I'm not 100% sure. I installed (I think) ccsm, compiz-core and compiz-plugins. And if you want fusion-icon then that should handle your dependencies too.

I don't have Ubuntu, I have a Xubuntu and Vista dual-boot.  I installed Compiz through the Add/Remove programs, but it says that I need xgl.  What's fusion-icon and the all the other things you're talking about?  I'm so confused lol. :confused:

> **overdrank said:**
> HI and you can use the command ```
lspci 
``` and look for VGA.

Oh okay, thanks.  I'm going to edit this post and tell you what it is because I'm having an error where I can only run one program at a time and nothing can minimize.  I posted my problem [here](http://ubuntuforums.org/showthread.php?t=853888) if you think you can help.

*edit* I found this:
```
VGA Compatible Controller: nVidia Corporation GForce 700M (rev a2) (rev a2)
```

---

