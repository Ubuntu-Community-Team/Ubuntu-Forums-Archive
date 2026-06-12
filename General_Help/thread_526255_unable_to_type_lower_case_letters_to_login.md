---
title: "unable to type lower case letters to login"
date: 2007-08-15
forum: General Help
---

### Post by plop166 on 2007-08-15
Hello all im having a problem that im hoping someone out there can help with.

I have been using and playing around with Ubuntu for the last couple of week and have been really impressed by it. Unfortunately last night while playing with the Xserver config program i changed the keyboard settings. Now i cannot type in certain lower case charracters. This is stopping me from being able to login as all three of the accounts setup for the machine need to use a lowercase 'm' (which i can no longer type!) either in the username or password.

Is there any way to fix this with out having to reinstall the whole of ubuntu again??
I have never come accross this type of problem again and im cursing myself for making this mistake as i had just managed to get everything else working for the first time:(

Any suggestions???

Thanks in advance for anyhelp you can provide:)

---

### Post by 1/0 on 2007-08-15
You could alway hit <Shift> + <Alt> + <F2> and log in there. Then change "XkbLayout" or whichever config that was changed.

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by plop166 on 2007-08-17
Hi again,

the <Shift> + <Alt> + <F2> at login screen dosent seem to be working. Where and when should i be pressing this to get the alternative login screen?

Thanks again for the reply!!

BC

---

### Post by Ozor Mox on 2007-08-17
Try Ctrl + Alt + F1 or F2.

---

### Post by matigol on 2007-08-17
Try Ctrl + Alt + F1 for having one console.
Then, edit with nano your xorg.conf file et give it us in ```
patati patata
```.

You must tape this when you see the login screen.

:)

---

### Post by plop166 on 2007-08-17
Success!!!!

Thanks guys... it was a piece of cake and i feel a whole lot better now :-)

---

