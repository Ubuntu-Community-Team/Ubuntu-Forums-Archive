---
title: "excessive keyring request?"
date: 2018-07-15
forum: General Help
---

### Post by princeofnam on 2018-07-15
I'm getting excessive requests when I start up ubuntu to input my password to access the ubuntu keyring.  Any idea on how I can disable this?  I tried to search this awhile ago and came to a thread that said to make a blank pw but this didnt work.  Moreover I  can't find anything else.  Any suggestions? Thanks.f

---

### Post by VMC on 2018-07-15
Is this when you open browser or something else? Do you auto login?

---

### Post by princeofnam on 2018-07-28
Thanks for responding.  Yes it's when I open Google chrome specifically.

---

### Post by again? on 2018-07-30
Turn off autologin or start chrome with the option not to save passwords in the login keyring.
```
/usr/bin/google-chrome-stable --password-store=basic
```
In which case the passwords will be stored non-encrypted in an sqlite DB @ "**~/.config/google-chrome/Default/Login Data**".

---

