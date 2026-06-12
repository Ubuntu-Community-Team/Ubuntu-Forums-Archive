---
title: "Ubuntu Software"
date: 2017-05-08
forum: General Help
---

### Post by lordgallen on 2017-05-08
Ubuntu Software is all of a sudden asking for a username and password to be able to download software. It never has before. Is it necessary to register an account to download from Ubuntu Software now?

Thanks.

---

### Post by howefield on 2017-05-08
Snap packages are available to install via the Software application in addition to the traditional deb packages. Snap packages require an SSO login to install.

What is it that you are trying to install ?

---

### Post by lordgallen on 2017-05-15
Electrum Wallet.

---

### Post by howefield on 2017-05-15
There doesn't seem to be a deb package in Ubuntu Software for electrum but there is a snap package, so yes it would need an SSO account to download and install it. It is the same account that you use to sign into the forums so you already have the credentials to install the snap package.

```
sudo snap find electrum
Name      Version      Developer  Notes  Summary
electrum  2.6.4-tpaw0  tpaw       -      Lightweight Bitcoin Client
```

---

### Post by lordgallen on 2017-05-18
gotcha- and thank-you

---

### Post by howefield on 2017-05-18
> **lordgallen said:**
> gotcha- and thank-you

You're welcome and feel free to mark the thread as solved, if you feel that it is.

---

