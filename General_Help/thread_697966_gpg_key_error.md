---
title: "gpg key error"
date: 2008-02-15
forum: General Help
---

### Post by fedex1993 on 2008-02-15
okay i am trying to make my gpg/pgp key for my email this is the error i get ```
gpg: no writable public keyring found: eof
Key generation failed: eof
gpg: note: random_seed file not updated

```
any suggestions

---

### Post by kevdog on 2008-02-15
What commands are you typing to generate your keys?

---

### Post by fedex1993 on 2008-02-16
gpg --gen-key

---

### Post by fedex1993 on 2008-02-16
Bumbbububu

---

### Post by kevdog on 2008-02-16
Can you post the entire command line here when you try to generate keys (just cut and paste whatever is listed on the command screen)

---

### Post by fedex1993 on 2008-02-16
yes hhere it is 
```
seand@seand-laptop:~$ gpg --gen-key 
gpg (GnuPG) 1.4.6; Copyright (C) 2006 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.

gpg: failed to create temporary file `/home/seand/.gnupg/.#lk0x811cab0.seand-laptop.8353': Permission denied
gpg: keyblock resource `/home/seand/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/seand/.gnupg/.#lk0x811ce38.seand-laptop.8353': Permission denied
gpg: keyblock resource `/home/seand/.gnupg/pubring.gpg': general error
Please select what kind of key you want:
   (1) DSA and Elgamal (default)
   (2) DSA (sign only)
   (5) RSA (sign only)
Your selection? 1
DSA keypair will have 1024 bits.
ELG-E keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 
Requested keysize is 2048 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y

You need a user ID to identify your key; the software constructs the user ID
from the Real Name, Comment and Email Address in this form:
    "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"

Real name: Sean Fedex
Email address: s_e_a_n_d@sbcglobal.net
Comment: 
You selected this USER-ID:
    "Sean Fedex <s_e_a_n_d@sbcglobal.net>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
You need a Passphrase to protect your secret key.

gpg: can't open `/home/seand/.gnupg/random_seed': Permission denied
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
..++++++++++++++++++++++++++++++++++++++++.+++++.+++++.++++++++++++++++++++...+++++++++++++++++++++++++++++++++++.++++++++++++++++++++++++++++++............................+++++

Not enough random bytes available.  Please do some other work to give
the OS a chance to collect more entropy! (Need 59 more bytes)
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
++++++++++...++++++++++.+++++++++++++++++++++++++++++++++++.++++++++++++++++++++++++++++++++++++++++++++++++++..++++++++++..++++++++++.+++++++++++++++.+++++>++++++++++>..+++++.......<..+++++.......+++++^^^^^^^^^
gpg: no writable public keyring found: eof
Key generation failed: eof
gpg: note: random_seed file not updated
seand@seand-laptop:~$ 

```

---

### Post by kevdog on 2008-02-16
What are the permissions on the .gnupg directory?

---

### Post by fedex1993 on 2008-02-16
um how can i check?

---

### Post by kevdog on 2008-02-17
cd ~

ls -la

Look for the rwx bits

---

