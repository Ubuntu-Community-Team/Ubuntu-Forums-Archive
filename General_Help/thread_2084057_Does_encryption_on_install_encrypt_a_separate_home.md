---
title: "Does encryption on install encrypt a separate home partition?"
date: 2012-11-14
forum: General Help
---

### Post by aridus on 2012-11-14
Ubuntu 12.10 has the option to encrypt the new installation for security. I have separate partitions for / and /home. If I choose to encrypt the new installation will it encrypt the whole drive (i.e. including /home) or only the partition on which I have /
?

With grateful thanks

---

### Post by Cheesemill on 2012-11-14
If you choose to encrypt at the partitioning stage it will encrypt the entire drive.

You can also choose to just encrypt your home folder at the screen where you enter your user details.

---

### Post by aridus on 2012-11-14
Many thanks - most helpful. My particular concern is securing my data in case my laptop is stolen. As my data is on /home it seems therefore that I only need to encrypt /home. Is there any reason why one would choose to encrypt the whole drive as opposed to just /home? I am trying to ensure that I make the correct choice(s) beforehand.

A related question - can the encryption password be the same as my login password (I would prefer not to have to remember two passwords)?

With grateful thanks

---

### Post by Cheesemill on 2012-11-14
In your situation then just encrypting /home is probably good enough.

I do use full disk encryption on some of my systems but these tend to be servers where the data isn't stored in /home. When using this method the password can be whatever you want, including being the same thing as your logon password.

If you just go for home folder encryption then your encryption passphrase is always the same as your logon password. Your home folder gets automatically unlocked when you log on.

---

### Post by aridus on 2012-11-14
Thank you - I think that sorts it out. But it caused me to think of a further situation. If my laptop (with only /home encrypted) is stolen the thief will not be able to access my data (unless he/she can figure out the pwd of course). However, they could install ubuntu on the latop, choosing to install to my root partition. In this situation I presume that they still would not be able to access my /home partition without the original pwd?

Again, with grateful thanks.

---

### Post by Cheesemill on 2012-11-14
> **aridus said:**
> In this situation I presume that they still would not be able to access my /home partition without the original pwd?
Correct.

---

### Post by aridus on 2012-11-14
...and a final question (sorry!). If I choose to encrypt the whole drive at installation rather than just /home would this prevent installation of ubuntu on the laptop? (I am thinking that, if it does, it would be best to simply encrypt the whole drive, as I can't see, as the only user of the system, that it makes any difference to me compared to encrypting only /home.

Thanks!

---

### Post by jonnyboysmithy on 2012-11-25
If you encrypt, they can still overwrite data, encryption won't stop that. They will be able to install what they like. The advantage of encrypting / is that its going to be hard to stick any malware on it, where as with only an encrypted /home anybody can chroot your / and install whatever they like.
sounds to me like encrypting your /home is enough, but why not do the whole thing if you're going to do it. I'd recomend making a backups of your machine and don't loose your password!! :)Otherwise its as good as gone.

---

