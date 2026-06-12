---
title: "Evolution/gpg wont send mail"
date: 2007-02-11
forum: General Help
---

### Post by acidblue on 2007-02-11
I can't send sign or encrypt email.
Using Seahorse as a key manager, i can ecrypt files on my desktop
but when i try to sign or encrypt mail I get this error:

Because "can't connect to `/home/acidblue/.gnome2/seahorse-fS3auO/S.gpg-agent': Connection refused
gpg: can't connect to `/home/acidblue/.gnome2/seahorse-fS3auO/S.gpg-agent': connect failed
gpg: writing to `-'
gpg: DSA/SHA1 signature from: "2D6CE269 Rocko


Using 6.06TLS

---

### Post by Alveric on 2007-02-14
try running the command

seahorse-daemon

in the shell.

I think this starts up the part of seahorse which actually handles the email signing or something like that, and this daemon doesn't always _automatically_ start up.

cheers,

Al.

---

