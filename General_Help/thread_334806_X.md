---
title: "X"
date: 2007-01-09
forum: General Help
---

### Post by gmanigault on 2007-01-09
I have a server that I setup.  I want to run it in graphical mode instead of Text.   I have tried the following. 

=====[snippet]

sudo aptitude  update     Successful
sudo aptitude  install ubuntu desktop       Successful
sudo /etc/init.d/gdm  start        Failed

Startx       Failed


=====[snippet]

I also thought that if you changed the run level to multiuser it would switch to graphics mode?  Was I wrong?  Can anyone direct me as to how to get graphic mode working and set it to the default?  Thanks. 

Gary M. 
GWShark](*,)

---

### Post by az on 2007-01-09
Are you running Dapper or Edgy?

You may need the desktop kernel and the associated packages:

sudo apt-get install linux-generic

---

### Post by gmanigault on 2007-01-09
I am running Dapper not Edgy.  I understand that if i don't need anything specific from Edgy then stick with Dapper for now.   Is that right.  What will that Sudo statement do for me?

Gary M. 
GWShark
:-k

---

### Post by az on 2007-01-09
> **gmanigault said:**
> I am running Dapper not Edgy.  I understand that if i don't need anything specific from Edgy then stick with Dapper for now.

Yup.

> **gmanigault said:**
> 
   Is that right.  What will that Sudo statement do for me?

Gary M. 
GWShark
:-k

It will install the desktop kernel.

---

