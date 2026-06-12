---
title: "Visual effects depends to a user connected !!"
date: 2008-05-29
forum: General Help
---

### Post by fard63 on 2008-05-29
Franck...

I was a problem with the visual effects.
Indeed, I created several user on my laptop and I can't activate the visual effect for all users but just for one.
I can't understand why, isn't a problem with the display driver, it's work  for the default user... Certainly, that be due to bag configuration.
Is there anybody able to help me ?
By advance thank for your help.

Bye

-------------------------------

---

### Post by Forlong on 2008-05-30
It's a hardware/driver issue. Some drivers support it, some don't.

---

### Post by fard63 on 2008-05-31
Thank for your prompt help !!

I used compiz-check, it's seem to be OK, so what....is there a trap somewhere ???
 I know where to looking for :

Please find follow some information get from compiz-check :

Regards

fard@fard-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Forlong on 2008-05-31
Like I said, the problem is with your hardware/driver.
For example, I am able to use Compiz on multiple users at the same time with the fglrx driver but not with the ati/radeon one.

I don't think there's anything you can do about this atm, I'm afraid.

---

