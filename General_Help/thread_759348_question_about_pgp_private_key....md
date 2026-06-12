---
title: "question about pgp private key..."
date: 2008-04-19
forum: General Help
---

### Post by Mia_tech on 2008-04-19
are pgp private key attached to a specific computer, or you can generate a private key in one computer and imported into another as private key..... I'm asking this question b/c I basically use two computer my personal pc and a laptop at work... but the email account are the same in both computer, can I use the same private key to open emails at both computers?

thanks

---

### Post by kevdog on 2008-04-19
The pgp private key is simply a file.  You are free to make copies of this and place it on as many computers as you want.  The problem with this strategy is that the pgp private key is the "glue" to the whole entire security model of pgp/gpg.  That means if one of the copies of the keys is stolen or falls into nefarious hands, then basically you are screwed (or at least another person is able to decrypt anything of yours they are able to get their hands on).  

Two things you might want to consider in your case are to:
1. Just keep one copy on a USB stick or some other media and use this to transport the private key (still subject to loss).
2. Generate a master private signing, (the encryption private key is actually a subkey). Then generate multiple private signing and encryption subkeys (one subkey combination for each computer).  

Here is a basic tutorial on gnupg: [http://ubuntuforums.org/showthread.php?t=687173](http://ubuntuforums.org/showthread.php?t=687173)
I never got around to finishing it unfortunately!!

---

