---
title: "failed to start x server"
date: 2007-07-31
forum: General Help
---

### Post by SonicBOOM on 2007-07-31
I just installed ubuntu and it wont start up, it's says failed to start x server and something about configuring and it tells me to log in. What should I do?

---

### Post by AlexThomson_NZ on 2007-07-31
Can you please supply more information about the errors you are getting?

Have a look at /var/log/Xorg.0.log too, that should have some detailed information about why it couldn't start up

---

### Post by SonicBOOM on 2007-07-31
> **AlexThomson_NZ said:**
> Can you please supply more information about the errors you are getting?

Have a look at /var/log/Xorg.0.log too, that should have some detailed information about why it couldn't start up

it says no such file or dicterory found when i type that

---

### Post by dragonwings on 2007-07-31
i had same problem

startup in recovery mode by pressing Esc button on start up 
go to the first recoverymode ya see press entre 

let it do its thing when its finished you will be able to put commands in

to start xserver-xorg use command blow

sudo dpkg-reconfigure xserver-xorg

and you should get the graphical interface

---

### Post by SonicBOOM on 2007-07-31
> **dragonwings said:**
> i had same problem

startup in recovery mode by pressing Esc button on start up 
go to the first recoverymode ya see press entre 

let it do its thing when its finished you will be able to put commands in

to start xserver-xorg use command blow

sudo dpkg-reconfigure xserver-xorg

and you should get the graphical interface
i tried that and after i rebooted, it took me back to the same failed screen

---

### Post by SonicBOOM on 2007-07-31
ok it works now, thanks

---

