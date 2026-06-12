---
title: ".ICEauthority account lockout"
date: 2004-10-30
forum: General Help
---

### Post by mikep on 2004-10-30
Hello ubuntu users,  for some reason I've been locked out of my main account.  After logging in I get an error message: x-session-error file - warning **: unable to read ICE authority file.  

The last thing that I did was to try to alter the gnome menu by going to applications:/// and adding new launchers.  

I've created a temp account which is running fine, but I would like my old settings back.

Any help appreciated.


Thanks

---

### Post by WW on 2004-10-30
This just happened to me--again!

I'm not sure if your problem is the same as mine, but here is how I fixed it.

You have to change the ownership of .ICEauthority:
```
$ sudo chown user .ICEauthority
$ sudo chgrp user .ICEauthority
```
where **user** is your user name.

Running k3b can cause this problem.  There is a HowTo on the Ubuntu web site about it.  I had this problem once, and I followed the HowTo in order to fix it.  I had the problem again, after running k3b, but also after some upgrades, and a reboot, so I don't know if k3b is the culprit.

---

### Post by mikep on 2004-10-30
[QUOTE=WW]This just happened to me--again!

I'm not sure if your problem is the same as mine, but here is how I fixed it.

You have to change the ownership of .ICEauthority:
```
$ sudo chown user .ICEauthority
$ sudo chgrp user .ICEauthority
```
where **user** is your user name.

Running k3b can cause this problem.  There is a HowTo on the Ubuntu web site about it.  I had this problem once, and I followed the HowTo in order to fix it.  I had the problem again, after running k3b, but also after some upgrades, and a reboot, so I don't know if k3b is the culprit.[/QUOTE]
 Thanks WW for sharing that with me, I recently installed k3b so perhaps thats what caused it.  I will hunt down the howto you mentioned.

---

