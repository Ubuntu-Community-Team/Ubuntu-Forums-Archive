---
title: "change login without password to login with password."
date: 2021-04-13
forum: General Help
---

### Post by jpaulb on 2021-04-13
That title should explain. Can anyone point me to how this is done?

---

### Post by Rex Bouwense on 2021-04-13
Using Ubuntu 20.04 I would assume.  Go to main menu->Settings->Users.  Select Unlock and enter your password.  Turn off automatic login.

---

### Post by jpaulb on 2021-04-14
> **Rex Bouwense said:**
> Using Ubuntu 20.04 I would assume.  Go to main menu->Settings->Users.  Select Unlock and enter your password.  Turn off automatic login.

It's Xubuntu 18.04 There is a check box beside "don't ask for password at login" whether that is checked or not it doesn't matter.

---

### Post by deadflowr on 2021-04-15
Remove yourself from the nopasswdlogin group.

---

### Post by ActionParsnip on 2021-04-15
> **deadflowr said:**
> Remove yourself from the nopasswdlogin group.

Oooh is that a thing? Learned something new today. Thanks! :-)

---

### Post by HermanAB on 2021-04-15
Eish... that sounds to me like a relatively easily exploitable feature.

---

### Post by deadflowr on 2021-04-15
> **ActionParsnip said:**
> Oooh is that a thing? Learned something new today. Thanks! :-)
This works for Xubuntu as it still uses lightdm display manager for the logins.
This feature works out of the box on lightdm.
It doesn't work out of the box on regular Ubuntu.
Ubuntu's gdm display manager login needs it to be set in PAM to allow it.
> **HermanAB said:**
> Eish... that sounds to me like a relatively easily exploitable feature.
About the same as using automatic logins.
I guess take it with a hefty grain of salt.

---

