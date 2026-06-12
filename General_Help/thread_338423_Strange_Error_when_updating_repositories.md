---
title: "Strange Error when updating repositories"
date: 2007-01-14
forum: General Help
---

### Post by Sir_Sid on 2007-01-14
So what exactly does this mean?

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I tried installing automatix earlier, but gave up. Is that error related to my previous attempt? 
Currently Im trying to install wine, but thats getting in the way.

---

### Post by rabid9797 on 2007-01-14
did you install a key when you put the win repo in? if not see if you can find one(i'll look too), or try using "-f" when doing apt-get.

EDIT:

what do you actually have in your sources list for the wine repo?

---

### Post by Sir_Sid on 2007-01-14
No  there was no key given. Where can i get the key? I got that error when doing apt-get update so it wont even connect to the repo

---

### Post by Sir_Sid on 2007-01-14
bump

Where can I get the key for the wine servers?

---

### Post by Azakus on 2007-01-14
Do this in the terminal
```
wget -O - http://wine.budgetdedicated.com/apt/387EE263.gpg | sudo apt-key add -
```

---

