---
title: "Re-registering my GPG Key (saved as an asc file)"
date: 2006-10-23
forum: General Help
---

### Post by TheForkOfJustice on 2006-10-23
I reformatted my HD and repartitioned. I saved the private key I sent to Launchpad as an asc file and saved a copy in my gmail account. I do not wish to make another key.

How am I supposed to get this asc file to be listed under 'My Personal Keys' in seahorse so I can sign files/decrypt text/etc with it?

---

### Post by mitch.c on 2006-10-24
> **TheForkOfJustice said:**
> I reformatted my HD and repartitioned. I saved the private key I sent to Launchpad as an asc file and saved a copy in my gmail account. I do not wish to make another key.

How am I supposed to get this asc file to be listed under 'My Personal Keys' in seahorse so I can sign files/decrypt text/etc with it?
I haven't used seahorse much, but can't you save the .asc file to your local computer, and then Import the key (Keys -> Import)?

---

### Post by TheForkOfJustice on 2006-10-24
I've tried importing but it just registers it as a trusted key. Not your personal key.

---

### Post by mitch.c on 2006-10-24
> **TheForkOfJustice said:**
> I've tried importing but it just registers it as a trusted key. Not your personal key.
This may sound stupid, but does the file contain your private key? It sounds like you are importing a public key. The header should read something like:
```
-----BEGIN PGP PRIVATE KEY BLOCK-----
Version: GnuPG v1.4.2.2 (GNU/Linux)
```

---

### Post by TheForkOfJustice on 2006-10-25
Your right.

For some reason it saved as a public key and not a private.

Guess I'll have to make a new key or is this fixable?

---

### Post by christhemonkey on 2006-10-25
Could you not just change the header and try re-importing it?

(back it up first!)

---

### Post by TheForkOfJustice on 2006-10-25
Tried editing the header to private as well as the footer.

They now look like this:

> -----BEGIN PGP PRIVATE KEY BLOCK-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

-----END PGP PRIVATE KEY BLOCK-----It only goes into my 'Keys I Collected' section (which I can upgrade into my 'trusted' keys) but not into my 'personal keys' in seahorse.

In other words, it doesn't change a thing.

EDIT

If I make a new key, how do I make sure it is saved as a private next time so I can sign stuff with it? I don't want to repeat this mess.

---

### Post by mitch.c on 2006-10-25
> **TheForkOfJustice said:**
> Tried editing the header to private as well as the footer.

They now look like this:

It only goes into my 'Keys I Collected' section (which I can upgrade into my 'trusted' keys) but not into my 'personal keys' in seahorse.

In other words, it doesn't change a thing.

Your public key and private keys are very different. Changing the headers doesn't change a thing (as you discovered). Without one, the other is useless.

> **TheForkOfJustice said:**
> If I make a new key, how do I make sure it is saved as a private next time so I can sign stuff with it? I don't want to repeat this mess.

From the shell prompt:
```
#exports public key
gpg -a -export "keyname" > keyname.asc

#exports private (secret) key
gpg -a -export-secret-keys "keyname" > keyname.asc
```
In both cases, keyname can be the user id or key id.

---

### Post by TheForkOfJustice on 2006-10-26
Thanks, mitch.c

I'll remember that from now on.

---

### Post by beerfan on 2006-10-26
It sounds like you only saved your public key. :-(

Also, if you value the secrecy of what you're encrypting I'd advise against uploading your private key to gmail :-)

---

### Post by TheForkOfJustice on 2006-10-26
That's how I always back things up :)

At least this time I know how to backup my PRIVATE key properly.

---

### Post by mitch.c on 2006-10-26
> **beerfan said:**
> Also, if you value the secrecy of what you're encrypting I'd advise against uploading your private key to gmail :-)
Great advice. I should have pointed that out earlier.
> **TheForkOfJustice said:**
> At least this time I know how to backup my PRIVATE key properly.If you really want to back up your keys, you should copy pubring.gpg, secring.gpg, and trustdb.gpg (maybe include gpg.conf) from ~/.gnupg to a safe/secure medium. These files contain your public/private key pair, as well as any other public keys you have collected.

---

