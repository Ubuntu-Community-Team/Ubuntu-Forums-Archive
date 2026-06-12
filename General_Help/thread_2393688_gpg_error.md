---
title: "gpg error"
date: 2018-06-06
forum: General Help
---

### Post by me-mitch on 2018-06-06
Forgive me if this is the wrong place to post this. I'm trying to creat a gpg key pair as i don't know a lot about making them here's what i type in 
gpg --gen-key then it ask the questions and i answer them it goes to making the keys and i end with this.

mitch@mitch-Inspiron-3650:~$ gpg --gen-key
gpg (GnuPG) 2.2.4; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

gpg: keybox '/home/mitch/.gnupg/pubring.kbx' created
Note: Use "gpg --full-generate-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

Real name: Mitch
Email address: [snipped] 
You selected this USER-ID:
    "Mitch <[snipped]>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: agent_genkey failed: No such file or directory
Key generation failed: No such file or directory
mitch@mitch-Inspiron-3650:~$ 

I followed this guide.

[https://alexcabal.com/creating-the-perfect-gpg-keypair/](https://alexcabal.com/creating-the-perfect-gpg-keypair/)

---

### Post by again? on 2018-06-06
Try the solution from here.
[https://unix.stackexchange.com/a/340105](https://unix.stackexchange.com/a/340105)

---

