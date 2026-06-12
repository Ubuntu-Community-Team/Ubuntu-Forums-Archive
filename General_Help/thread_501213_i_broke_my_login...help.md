---
title: "i broke my login...help?"
date: 2007-07-15
forum: General Help
---

### Post by bishop9226 on 2007-07-15
ive been having trouble getting on any wireless outside of my house for some reason.  it just sits there trying to connect and then it never does.  the only thing i can think of was that i had the keyring set so that it didnt ask me to enter it.  so i did 

sudo gedit /etc/pam.d/gdm

then commented out the last line from 

@include common-pamkeyring

to // @include common-pamkeyring

because i wanted to have it ask me for the keyring again.  but now when i try to login to my desktop it says "authentication failed!" in a popup window (different from entering an invalid username or invalid password).  how do i edit this file in recovery mode so i can get this back, and why the heck is my wireless being annoying?  im stuck back on win xp because ubuntu is being annoying about wifi all the sudden.

---

### Post by Koybe on 2007-07-15
Boot in recovery mode, and then :

```
nano /etc/pam.d/gdm
```
'remove your comments //'
CTRL+X, then Y to write and ENTER to get out of nano
```
init 2
```

---

