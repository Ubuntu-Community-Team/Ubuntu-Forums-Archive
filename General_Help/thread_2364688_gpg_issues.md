---
title: "gpg issues"
date: 2017-06-26
forum: General Help
---

### Post by hexd19722 on 2017-06-26
Hi, I am pretty novice at gpg.
I lost my old usb thumb drive with the past pgp keys.
I have the public key in the format of:
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v2

-----END PGP PUBLIC KEY BLOCK-----
I know the password, but I think im having a problem because of no secret key.

I created a new key using gpa and seahorse
I imported my old public key
someone sent me a message using my old public key

but when I try and decrypt it, it says no secret key available

when i do gpg --list-keys I get results
when I do gpg --list-secret-keys I get no results

I did not send the keys to a keyserver, not sure if I need to do that or not.
Is there any way of opening a message that was sent using an older pgp public key? If you know the password

Any help would be great!
Thank you, Mike

---

### Post by Dennis N on 2017-06-26
> Is there any way of opening a message that was sent using an older pgp public key? If you know the password.

No, because decoding can only be done with the secret key, and without both the password and secret key, you are out of luck.
A public key is only for encoding messages intended for the key's owner, and you need no password to encode something with it.

---

### Post by hexd19722 on 2017-06-26
OK thanks a lot for answering.

---

