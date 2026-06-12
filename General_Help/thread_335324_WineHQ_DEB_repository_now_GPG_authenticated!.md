---
title: "WineHQ DEB repository now GPG authenticated!"
date: 2007-01-10
forum: General Help
---

### Post by Limulus on 2007-01-10
For as long as I can remember, the WineHQ repository (see [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) for info) always gave a "not authenticated" error in Synaptic, so I contacted the maintainer about it.  He fixed the problem :)

Now all you need to do is add Scott Ritchie's GPG key (387EE263), e.g.:

```
gpg --keyserver subkeys.pgp.net --recv 387EE263 && gpg --export --armor 387EE263 | sudo apt-key add -
```

press reload in Synaptic and for Dapper and Edgy the problem should be fixed! ^_^

---

### Post by Severa on 2007-01-10
WOOHOO!

Thanks for posting this, worked wonderfully on my Edgy 6.10!

---

### Post by FuturePilot on 2007-01-10
Ahh thanks. There was an update for Wine today and I got that unauthenticated message.

---

### Post by grazie on 2007-01-13
The key server appears to down and has been for a while. Anyone know who to contact to bring it back up?

---

### Post by grazie on 2007-01-15
Now back online.

---

### Post by Limulus on 2007-01-16
> **grazie said:**
> The key server appears to down and has been for a while. Anyone know who to contact to bring it back up?

Apologies; I should also have mentioned that Scott keeps a copy of the key on the repository:
[http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
which can be imported into Synaptic.

---

