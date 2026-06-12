---
title: "root as user ?"
date: 2007-04-19
forum: General Help
---

### Post by Ne0z on 2007-04-19
is it possible to always log in as root ?

my ubuntu is just a virtual machine to me so can i somehow configure it to always log in as root ?

thanks !

---

### Post by fanatik on 2007-04-19
hmm well yes, of course, although perhaps not the best option....

you need to set a root password, with 
$ sudo passwd

then you can use the GDM options to configure automatically log you in if you wish.
$ sudo gdmsetup

Regards,

---

### Post by Ne0z on 2007-04-24
i tried doing the step you mentioned

under Login Windows Preferences > Security Tab > Check Enable Automatic Login 

but when i chose the user to be root

it says 


"autologin or timed login to the root account is forbidden."

hmmm how do i make it auto login as root ?

---

### Post by mdurham on 2007-04-24
you could try:
> system->administration->login window->security and tick "allow local system admin login"
this might work, I don't know because I've never done it.

---

### Post by Ne0z on 2007-04-24
yep i've done that, 

but still i can't auto login as root :) 

cheers

---

### Post by Ne0z on 2007-04-29
anyone ?

---

### Post by aysiu on 2007-04-29
Nope. Can't be done for security reasons.

---

