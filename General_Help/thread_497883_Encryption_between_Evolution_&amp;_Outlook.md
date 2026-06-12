---
title: "Encryption between Evolution &amp; Outlook"
date: 2007-07-10
forum: General Help
---

### Post by casperlingus on 2007-07-10
I have looked around a bit and have not found any obvious solutions.  I have apt-get installed seahorse (though I've used the command line gpg, before) and created a 2048-bit PGP/GPG key. 

Evolution seems really good about using your key to encrypt messages -- I didn't have to do anything--I just composed an email to myself and clicked Security-->PGP Sign and Security-->PGP Encrypt, Send, done.  (of course, it had my PGP key on file).

I can easily export my public key, and import others' public keys.  However, I'm unclear how I'm going to get this to work with Windows.  I found a plugin for Outlook for PGP/GPG, but only for Outlook 2003 SP2 or SP3.

1) Is anyone familiar with a plugin for MS Outlook that will use PGP/GPG and be compatible with the Evolution process?  That would be the simplest solution, if it exists.  I've looked around and nothing pops out.

2) I notice S/MIME signing/encryption is also available, and I believe that might be more Windows-friendly.   But I'm not clear how to set up a certificate.  Does Outlook have a built-in S/MIME layer?  Or will that require a separate plugin too?

I am the lone ranger at work, running Linux while everyone else is running Windows.  If only I could convert all 4000 people and all our sponsors to Evolution, then this would be trivial!  :)

-Casper

---

### Post by casperlingus on 2007-07-12
Well after a long couple days, I finally understand just about everything there is to know about signing/encryption (maybe an exaggeration, but I do know a lot, now).

1)  It looks like there is a program called GPGOE, which is a program for Outlook Express that I guess will do what I'm looking for.  I haven't actually tried it, because of #2:

2)  I realized that I had already been issued an S/MIME certificate by my company.  I was able to boot into windows and easily export my S/MIME certificate, then import it into Evolution.  This certificate is signed by VeriSign, and technically more secure than PGP/GPG with keys exchanged online (although the necessity of that extra security is questionable [at least for this application]).  

However, I can now encrypt *or* sign emails, but not both.  At least not when the receiving end is using MS Outlook 2003.  

All this encryption stuff is pretty neat, if you care.  If you don't care, then just know that GPG is plenty secure for most applications.  It just so happened my company provides the slightly higher level of security for S/MIME.

-Casper

---

### Post by Junping on 2008-05-21
There is a lot to know about S/MIME ...

For S/MIME based encryption, it's pretty straight forward. The sender uses the receiver's public key to encrypt it, and the receiver uses its own private key to decrypt it.

For S/MIME based signing, you can do either do clear-text signing or opaque signing. The latter case is tricky since it involves using the private key to decrypt the wrapper.

I think you should be able to encrypt & sign at the same time since encryption is the outmost wrapper. Try opaque signing as well to see if that causes you any problems.

Cheers.

- Junping

---

