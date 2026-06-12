---
title: "Ubuntu 7.10, beryl?"
date: 2007-12-30
forum: General Help
---

### Post by Kodge on 2007-12-30
Hi, I know that beryl comes with 7.10. But I remember when I used to use 7.04 on my old box. There was an option to add more visual effects. More so the effect where your frames would burst into flames when you closed a window.
Is this option still available in 7.10?

---

### Post by chewearn on 2007-12-30
Beryl has been discontinued.  What we have in Gutsy 7.10 is compiz and compiz fusion.

And yes, flame still available.

---

### Post by Kodge on 2007-12-30
Hey, thanks for your reply. 

Is Compiz and Compiz Fusion still available via the normal methods? ( aka: the package manager ).

*edit*

A quick edit, i curently have Compiz running. However is there anyway I can get into its options to play around with the effects?

---

### Post by chewearn on 2007-12-30
Install CCSM:
```
sudo aptitude install compizconfig-settings-manager
```You will get a new menu entry:
System > Preferences > Advanced Desktop Effects Settings

---

### Post by Kodge on 2007-12-30
I must seem like a terrible bother to you, I do apologize in advance, when I enter my password whenever I try and install anything via the terminal, I get this:
[http://img148.imageshack.us/img148/6905/screenshothw5.jpg](http://img148.imageshack.us/img148/6905/screenshothw5.jpg)

My password is correct, strange :S

---

### Post by chewearn on 2007-12-31
It could be already obvious to you, but I ask just in case.

The password is the same one you specify when you install ubuntu.  If you have not add another non-root user, then it's your current user's password.

Also, make sure capslock is not on (it happens to everyone). :)

Another way is to open up Synaptic (Top Panel Menu > System > Administration > Synaptic Package Manager).  Search for this package, and click the checkbox, then the Apply button.

---

