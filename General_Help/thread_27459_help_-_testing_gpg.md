---
title: "help - testing gpg"
date: 2005-04-16
forum: General Help
---

### Post by brickbat on 2005-04-16
hi, could someone please help me test my gpg installation in thunderbird. Could you please send me an encrypted message to [email]da.brickbat@gmail.com[/email]

ciao
bb

---

### Post by joshmachine on 2005-04-16
[QUOTE=brickbat]hi, could someone please help me test my gpg installation in thunderbird. Could you please send me an encrypted message to [email="da.brickbat@gmail.com"]da.brickbat@gmail.com[/email]

ciao
bb[/QUOTE]
 Happy to do it.  You'll have to post your public key though.  run the following command

$ gpg --armor --export [email="da.brickbat@gmail.com"]da.brickbat@gmail.com[/email] 

and paste the text that is output into this thread.

Cheers,
Josh

The way that the encryption works is that anyone can use your public key to encrypt stuff, and you can send it to anyone you like.  Only you can use your private key (which stays on your machine) to decrypt.

---

### Post by brickbat on 2005-04-16
Thanks Josh.  Here it is.  But enigmail says my public key is already published.  If i have to post this everywhere, what is the point of a public key server?

ciao
bb

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.2.5 (GNU/Linux)

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
=Vy+C
-----END PGP PUBLIC KEY BLOCK-----

---

### Post by joshmachine on 2005-04-16
[QUOTE=brickbat]Thanks Josh.  Here it is.  But enigmail says my public key is already published.  If i have to post this everywhere, what is the point of a public key server?

ciao
bb

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.2.5 (GNU/Linux)

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
=Vy+C
-----END PGP PUBLIC KEY BLOCK-----[/QUOTE]
 Well, a keyserver can be useful, but there is a whole web of trust metaphor that is at work here.  

i.e you send it to your friend, and over some other means of communication verify that it is indeed your key (through the key fingerprint) 
Your friend then uses his/her key to sign your public key.  You then re-import your public key into your keyring and it will show it as being signed.  You also submit you new signed public key to the keyserver. then if anyone really trusts your friend, they will be "assured" that you did indeed create this key and it is legit, and that they should nominally trust your key and keys that you sign.  I'm not sure that the web of trust thing has really taken off in all but the most geekiest circles, but it's a nice idea.

Additionally there are many keyservers and you didn't post which one enigmail is configured to use.

Encrypted email is on it's way.

Cheers

---

