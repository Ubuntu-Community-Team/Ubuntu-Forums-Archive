---
title: "how do i uninstall SHA1?"
date: 2020-01-19
forum: General Help
---

### Post by Skaperen on 2020-01-19
i what to eliminate SHA1 from my system.  but [COLOR=#0000cd][FONT=courier new]**dpkg -l**[/FONT][/COLOR] finds no such package.

---

### Post by CelticWarrior on 2020-01-19
There is no such package.

What exactly are you trying to do?

---

### Post by Holger_Gehrke on 2020-01-19
SHA1 is not a separate piece of software, it's a hashing algorithm built into multiple pieces of software (take a look at 'apt search sha1'; there's at least three libraries (librhash0, libmhash2, libgcrypt20) that each implement SHA1 and a lot of other hashes). Since these usually offer several hash-functions, the right way to handle the vulnerability of SHA1 is to configure your software to use a different hashing algorithm and to **never ever** fall back to SHA1.

Holger

---

### Post by Skaperen on 2020-01-20
i want to have any software still using SHA1 to fail, if it is trying to use shared implementations.  that is to discover any overlooked uses of SHA1.

---

### Post by Impavidus on 2020-01-21
You could get the source code of the hashing library, remove the SHA-1 code, compile and install. But that doesn't seem like a good idea to me. SHA-1 may no longer be considered cryptographically secure (and hasn't been for years), but it's widely used in applications where that doesn't matter: git, backup tools, file indexing tools, checking for accidental file corruption. Even MD5 is still widely used for such purposes. And you'd have to make sure you get the security upgrades for the other hashing functions in the same library manually.

---

