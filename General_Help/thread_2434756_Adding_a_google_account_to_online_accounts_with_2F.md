---
title: "Adding a google account to online accounts with 2FA"
date: 2020-01-10
forum: General Help
---

### Post by gregac2 on 2020-01-10
I'm using Ubuntu 18.04 LTS and I'd like to add my work google account to online accounts in settings. However the account has strict 2FA enabled so I have to use a security key to login but I'm unable to do so.

When you add the account the google sign in page pops up but states you must use chrome for the 2FA bit, I've got chrome installed but it seems the issue is webkitgtk doesn't support the U2F protocol required and webkitgtk is what is used to open the sign in page. Does anyone know if there's a way to add a google account to online accounts that can use chrome or firefox to do the sign in?

---

### Post by fumandor on 2020-02-25
The same problem encountered when using Gnome Cloud Accounts.  When trying to add a Google account that has Advance Protection enabled with Titan keys the message "browser does not support keys"  comes up. Chrome and Firefox do allow for key authentication but it seems that WebKit still does not fully support 2FA.

---

