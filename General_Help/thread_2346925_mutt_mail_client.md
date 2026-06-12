---
title: "mutt mail client"
date: 2016-12-20
forum: General Help
---

### Post by Hotchilli on 2016-12-20
i am setting up mutt i havve some questions

where does the .muttrc file go in home/root?
i have gpg key I only want to sign messages only

in .muttrc are there any other lines I might add other than these below


```
set pgp_sign_command="gpg --no-verbose --batch --output - --passphrase-fd 0 --armor --detach-sign --textmode %?a?-u %a? %f"

set pgp_sign_as=0x12345678 

set pgp_timeout=60
```

set from="your@email.com"

set realname="hotchilli"

set signature='~/.signature'

thanks

---

### Post by howefield on 2016-12-20
> **Hotchilli said:**
> where does the .muttrc file go in home/root?

Put it in ~/home/

```
~/.muttrc
```

> in .muttrc are there any other lines I might add other than these below

I'd suggest an address book, a way of viewing html that needs it and possibly some colour options.

---

