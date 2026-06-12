---
title: "Ubuntu 16.04.0 64 bit LTS &amp; Seahorse: no personal keys listed"
date: 2016-06-15
forum: General Help
---

### Post by Welly Wu on 2016-06-15
I performed a clean installation of Ubuntu 16.04.0 64 bit LTS GNU/Linux bare metal on my Sager NP8657 [Clevo P650-RE3] gaming laptop and I tried to import my GnuPG public and private keys using the Seahorse front end tool. It does not list my personal keys. I changed the view to see all of my personal keys. I think that there is a bug. How do I fix this issue so that I can see my keys and set the trust level?

---

### Post by Welly Wu on 2016-06-15
gpg2 --list-keys
gpg2 --import YourKeys
gpg2 --edit-key
>trust
>5
>quit
Do it each time for each key

Launch Seahorse
Personal keys will be listed

Set trust level for each key
exit

---

