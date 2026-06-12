---
title: "Openssl-devel"
date: 2008-05-26
forum: General Help
---

### Post by carla19 on 2008-05-26
Bonjour,

Je débute en faite avec ubunto et j'aimerai installer le openssl-devel.
Tout d'abord, comment vérifier si un package est installé ou non?

Et pour openssl-devel je ne trouve que des RPMs, je pense que je ne peux pas installer des RPMs sous Ubunto, alors comment je fais?
S'il y a un lien qui peut m'aider, voulez me le passer SVP?

Merci

---

### Post by Gunman1982 on 2008-05-26
Je t'aim?
Could someone translate? (Not my misspelled crappy try to write french)

---

### Post by carla19 on 2008-05-26
I am sorry.

I am a beginner with Ubunto and I want to install the openssl-devel package.
First, how to verify that a package is installed or not?

And for openssl-devel, I find only RPMs and I think that we can't install RPMS on Ubunto, so how should I do?

If there any link that can help, I ll be grateful.
THX so much

---

### Post by Gunman1982 on 2008-05-26
Open synaaptic and search for openssl, it should give you libssl-dev package or something. Just tick it and install.
Or open a console and execute 'sudo apt-get install libssl-dev'

---

### Post by Monicker on 2008-05-26
The package you want is libssl-dev, and it is not installed by default.  You can see if its already installed by checking in Synaptic, or doing the following from a terminal:

```
dpkg --get-selections|grep libssl-dev
```

---

