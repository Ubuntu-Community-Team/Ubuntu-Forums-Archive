---
title: "kde  &amp; root"
date: 2004-11-05
forum: General Help
---

### Post by ~zoey~ on 2004-11-05
I installed ubuntu in hopes that it would run my printer and it does.

I am a newbie who is used to kde, and I installed it with no problem.

I cannot run synaptic though, because it asks for the root password and will not accept the user password.  I can't get into manage users because it needs a root password to open, so it is kind of a catch 22.

I would really appreciate some suggestions.

Thanks, zoey  :?

---

### Post by im_ka on 2004-11-05
try
```
sude useradd root
```
and
```
sudo passwd root
```
add your new password

hth

---

### Post by iarwaith on 2004-11-05
Are you initialising synaptic from a menu (and thus triggering gnome-sudo or similar)?

I was, and was having the same problem, so I do this instead:

If you don't want to add the root account as im_ka wisely suggested, try running 

 sudo synaptic 

from a terminal, which _should_ accept your user password. Slight annoyance perhaps, but no real hassle.

Cheers

---

### Post by ~zoey~ on 2004-11-05
Thanks to you both.  I had tried to run synaptic with sudo run-synaptic.  No go.  Sudo synaptic worked just fine, though!

Now I have another question.  In order to install kde, I uncommented  universe.  Now I am wondering if it would be a good idea for me to go in and block it again?

Thank you for your help and quick responses.  zoey  :D

---

### Post by im_ka on 2004-11-05
yea you can uncomment it but that'll keep you away from updating (which doesn't happen with _debian_ very often :)).

but why would you do that? it shouldn't mess things up,

---

