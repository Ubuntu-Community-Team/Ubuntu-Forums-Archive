---
title: "u10xxx Kill all passwords all keyrings!!!!"
date: 2013-01-12
forum: General Help
---

### Post by mawil1013 on 2013-01-12
Running ubuntu 10LTS, how do I stop it from asking for password after a reboot, and stop asking for keyring to get wifi going,

I seriously thought I did not set these up, I ignored first asking of keyring, now everytime reboot it asks and I have to reenter the wifi network password.

---

### Post by orb9220 on 2013-01-12
Found two files in ~/.gnome2/keyrings/ default and Default.keyring.

To make it work you have to go into that location ~/.gnome2/keyrings/
and delete those 2 files in there and then start again.

Then at the two password dialog just hit enter key nothing else. It will inform you of unsecured and just click Ok and then you won't be bugged anymore.

---

