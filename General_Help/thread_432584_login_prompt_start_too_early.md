---
title: "login prompt start too early"
date: 2007-05-04
forum: General Help
---

### Post by nebi on 2007-05-04
I have a wierd problem , the login prompt start too early on boot up , it starts before apache2 starts . I can still login but i perfer that the login prompt shows up after the boot proccess :) Any idea ?

This happend after I upgrade from edgy to feisty on my server. (first I had the tty problem but it's solved I think (no error on boot) after that i notice that the login prompt showed up middle in the boot frequency of other service I run on the server)

---

### Post by kidders on 2007-05-06
Hi there,

This is deliberate. Once enough services have started to allow users to log in, the prompt is presented, while the rest of your startup sequence continues in the background. This normally doesn't cause any problems ... the purpose is to let you start your display manager sooner, so you don't have to wait too long before your system goes interactive.

---

### Post by Glucose52 on 2007-05-08
Thanks for the info kidders, I am having the same problem and I was wondering if there was anyway to remedy it.
Is there any way to change it so that the prompt doesn't come up until everything else is loaded?
(it messes up my pretty boot screen)
I am using the base only without X so I don't have any *dm to start.

---

### Post by dcstar on 2007-05-08
> **nebi said:**
> I have a wierd problem , the login prompt start too early on boot up , it starts before apache2 starts . I can still login but i perfer that the login prompt shows up after the boot proccess :) Any idea ?

This happend after I upgrade from edgy to feisty on my server. (first I had the tty problem but it's solved I think (no error on boot) after that i notice that the login prompt showed up middle in the boot frequency of other service I run on the server)

```
sudo nano /etc/default/rcS
``` and try DELAYLOGIN=yes

---

### Post by Chaoz23 on 2007-05-08
sad to say i did the above modification and it didn't work :( any other ideas? :confused: 

thanks

---

