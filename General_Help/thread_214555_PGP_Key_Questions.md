---
title: "PGP Key Questions"
date: 2006-07-12
forum: General Help
---

### Post by j_baer on 2006-07-12
I have two computers and I use Ubuntu 6.06 on both. I successfully registered my PGP key to Launchpad and now I have a question.

My question is ...

Can I use that key on my other computer?

If so, how do I install it?

Thanks

---

### Post by stimpsonjcat on 2006-07-13
how did you create the key? assuming you used gpg, the answer is gpg --export-secret-keys
to export you private key to a file (you can specify a filename with the --output option)
and then use gpg --import on the target machine.

see man gpg for detailed instructions.

you could also use a graphical front-end for gpg like seahorse (gtk) or kgpg (kde).

---

### Post by mlind on 2006-07-13
You probably want to export armored version of your secret key
```

gpg --export-secret-keys -ao secrets.gpg

```

---

### Post by j_baer on 2006-07-13
Thanks for the info. I'll give it a try.

Cheers ...

---

