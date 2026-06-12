---
title: "Removing ppa doesn't remove gpg key"
date: 2014-01-09
forum: General Help
---

### Post by spider623 on 2014-01-09
I have a really strange problem on ubuntu 13.10, when i remove or purge(ppa-purge) for some reason the key on /etc/apt/trusted.gpg.d stays there and i have to manually remove it, any ideas why it doesn't remove it any more?

p.s. i figured it because i had gpg no_pubkey errors and and since everything was working fine a few days ago i went to check if they where there and found some ppa that i didn't want and purge them and while the ppa was gone the key was there, after manually removing the gpg no_pubkey errors were also gone

---

