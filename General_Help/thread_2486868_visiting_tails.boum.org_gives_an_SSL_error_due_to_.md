---
title: "visiting tails.boum.org gives an SSL error due to self signed certificate"
date: 2023-05-15
forum: General Help
---

### Post by Drenriza on 2023-05-15
Hi all
I am not really sure where i can ask this question, since i cannot access tails official website without receiving an SSL / TLS warning stating that the
certificate used for the site is self signed.

Does anyone know what this is all about?
It seems kinda strange that a secure Linux distribution, has an insecure website.

Anyone has any insight into this that they can share with me?

Thank you in advance
Best regards

---

### Post by Holger_Gehrke on 2023-05-15
That is strange. When I open [https://tails.boum.org/](https://tails.boum.org/) I don't get any warnings (Firefox 113.0.1 on XUbuntu 22.04). Looking at the details of the certificate in use for this site shows they are using a certificate issued by 'Let's Encrypt'. If I ask for the IP-address of tails.boum.org using the command 'host tails.boum.org' I get 204.13.164.63.

Holger

---

### Post by ActionParsnip on 2023-05-15
What is the output of:
```

lsb_release -a; uname -a

```
Thanks

---

