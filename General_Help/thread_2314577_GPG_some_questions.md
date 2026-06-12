---
title: "GPG: some questions"
date: 2016-02-22
forum: General Help
---

### Post by t0p on 2016-02-22
Hi, just created a GPG key-pair, and I have a few questions:

1.  How does one go about getting folk to sign my key?  Nearly all my computer-scene friends, who would use GPG, are online friends.  And I live in UK, they mostly live in USA.  How would one set-up an online key-signing party?

2.  I'm still using 12.04LTS and will soon upgrade to the latest LTS version.  How do I go about exporting my GPG keys from 12.04 and importing them into the new OS version?

3.  What are the best key servers I could use to post my public key?

4. Some of my online friends use Windows and PGP.  Will GPG play nicely with PGP?  Also, I have a Windows 8.1 laptop (that I have found impossible so far to put Ubuntu on). Is is there a GPG Windows version?  It'd be nice if I could encrypt/decrypt messages on my laptop rather than waiting to get home to my home pc to do it.  Especially as my home machine has tarted to continually whirr in an ominous "I'm gonna die soon!" kind of way...

Sorry if these are n00b questions.  Also sorry if I posted this in the wrong forum.

Cheers!

---

### Post by t0p on 2016-02-24
A bit of a bumpity-bump in the hope that someone knows what I want to know!

One thing in particular: there are a few Windows GnuPG installers links at [https://www.gnupg.org/download/index.html](https://www.gnupg.org/download/index.html).  Will these work for Windows 8.1?

Thanks.

---

### Post by Habitual on 2016-02-24
Have a look at [https://fedoramagazine.org/gpg-using-your-key/](https://fedoramagazine.org/gpg-using-your-key/) 
As for WinGPG systems, see [https://www.gnupg.org/download/supported_systems.html](https://www.gnupg.org/download/supported_systems.html)

---

### Post by jim_deadlock on 2016-02-24
> **t0p said:**
> 1.  How does one go about getting folk to sign my key?  Nearly all my computer-scene friends, who would use GPG, are online friends.  And I live in UK, they mostly live in USA.  How would one set-up an online key-signing party?

The point of key signing parties is that people meet face-to-face which gives them extra verification that the key belongs to the person. Online key signing parties are pointless really, but if these are friends you know from a common place, for example a gaming site, then you could organise a signing party in a chatroom there just for the fun of it. You could also simply email each other your keys for signing.

> **t0p said:**
> 2.  I'm still using 12.04LTS and will soon upgrade to the latest LTS version.  How do I go about exporting my GPG keys from 12.04 and importing them into the new OS version?

If you're upgrading then you don't need to do anything, your keys will not be affected.

> **t0p said:**
> 3.  What are the best key servers I could use to post my public key?

Whichever app you're using GPG with, it probably has a few key servers in it that you can upload to. Doing that is only necessary if people who you don't know want to make initial contact with you securely, for example if you're a member of a large online community that encrypts email by default. Sadly, GPG has not been adopted by the general population so nobody will go looking for your key online before contacting you. My key has been on the servers for 20+ years and nobody has ever downloaded it.

> **t0p said:**
> 4. Some of my online friends use Windows and PGP.  Will GPG play nicely with PGP?

Yes, they are both apps that use the same key formats.

  > **t0p said:**
> Also, I have a Windows 8.1 laptop (that I have found impossible so far to put Ubuntu on). Is is there a GPG Windows version? It'd be nice if I could encrypt/decrypt messages on my laptop rather  than waiting to get home to my home pc to do it.  Especially as my home  machine has tarted to continually whirr in an ominous "I'm gonna die  soon!" kind of way...

GPG is traditionally the Linux version of PGP. Windows users normally have PGP apps, but as I said it will work just fine as they use the same keys.

---

