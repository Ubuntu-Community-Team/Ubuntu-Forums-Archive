---
title: "Unable to convert OpenSSH private key to private key PEM!"
date: 2020-04-26
forum: General Help
---

### Post by roachk71 on 2020-04-26
Howdy, everybody,

I'm having a wrath-inspiring problem converting a private OpenSSH (SSH2) key to a *private* PEM file. I have two Android devices which need a PEM file to access the OpenSSH server on my Ubuntu 20.04 LTS box, and OpenSSL can't convert SSH2 keys. Additionally, ssh-keygen only generates *public* key conversions.

In Ubuntu 18.04, I was able to use OpenSSL to convert id_rsa to a private PEM, but no longer can. None of the (old) solutions I've managed to find online work, either. I'm completely stumped. Since I access the server remotely, password authentication is out of the question.

I'd greatly appreciate a working solution to this problem that doesn't require installing Wine and PuTTY. Can anybody help?

Thank you in advance.

---

### Post by roachk71 on 2020-04-28
**UPDATE (04-28):** [I]While this issue remains unsolved, I've had to switch back to Xubuntu 18.04 for the time being. 20.04's repositories are missing several of the development libraries I need to build VICE from source (among others,) and I need one of these emulators to develop software for THE C64 (Mini.)

Please post a working solution if one is found, as I would still be most grateful.

Thank you

05-14: I've had to return to Kubuntu almost immediately, due to Xubuntu's random font rendering issues...Bleh!
[/I]

---

