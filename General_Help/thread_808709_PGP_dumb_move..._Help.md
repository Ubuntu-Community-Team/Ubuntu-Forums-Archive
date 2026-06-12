---
title: "PGP dumb move... Help?"
date: 2008-05-26
forum: General Help
---

### Post by sparrowkc on 2008-05-26
So with its placement in 8.04, I recently discovered PGP encryption. I quickly created a key before I really knew what they were for, and later deleted it. The next key I created got uploaded to some keyservers, which I didn't really understand.  When the openssh news hit, I didn't know the difference between ssh keys and pgp keys, so I deleted both... oops...

So now I have a pgp key on a keyserver for which I do not have the private key.  I also have one that I am going to be responsible with, but I'm afraid that for instance if people send encrypted email to me they will find my old key.

So...

Am I screwed on this? I fully accept that this was my own dumb fault.

Bad key id is 3A0BDE6A
Good key id is F2D6D71B

---

### Post by sparrowkc on 2008-05-26
Please?

---

### Post by aos101 on 2008-05-27
I think you're kind of screwed as far as I can see.  If you had generated a revocation certificate when you created the key you could use that, but I assume you didn't.

---

### Post by sparrowkc on 2008-05-27
Where are PGP keys stored, and is there any chance that it got deleted to the lost and found and/or I could recover it with a undeleter type thing?

---

### Post by wootah on 2008-05-27
Probably was not moved to Lost and Found. That directory is for recovered files discoverd my fsck (afaik). I believe pgp keys are stored in ~/.pgp

---

### Post by sparrowkc on 2008-05-27
~/.gnupg

---

### Post by wootah on 2008-05-27
I don't know if I would really consider it a big deal. Just create a new key and reupload it. This time, make sure to create a revocation cert as well (just in case:))

---

### Post by sparrowkc on 2008-05-27
But If someone encrypts an email to me and their email client just searches for my email address, will it encrypt it for the old key that I don't have, or just both?

---

### Post by chrisccoulson on 2008-05-27
It depends on whether it gets your old pubilc key or now. Basically, as someone else pointed out - you're pretty screwed. I'm not even sure you can revoke a key if you don't have the private key. Once you've deleted the private key, then there's no going back. You just need to create a new key pair and upload the new public key

---

### Post by johnl on 2008-05-27
If you specified an expiration date for your old key, you'll be fine as soon as it expires :)

---

### Post by sparrowkc on 2008-05-27
Nope, it never expires...

As I'm thinking about this, what happens if some random person decides to make a fraudulent key in someone else's name?  Is the real one just determined by web of trust?  Are there any authorities that I could get to sign my good key?

---

