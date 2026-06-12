---
title: "trevino sources list issue"
date: 2007-01-17
forum: General Help
---

### Post by tchoklat on 2007-01-17
After adding Trevino's sources list I now get thirteen instance of;

GPG error: [COLOR=SandyBrown]http://www.whatever etc etc.com[/COLOR] Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A714EB87D1B1F415

Is this a probem?
Can I fix it?

tchoklat

---

### Post by hikaricore on 2007-01-17
You need to download/install the signed security key for each repository.  Most of them are listed on his page that contains the repo list.

[http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

> # Treviño&#8217;s Ubuntu Edgy Sources list
# [http://download.tuxfamily.org/3v1deb/blog/?page_id=13](http://download.tuxfamily.org/3v1deb/blog/?page_id=13)
#
# Firstly made on source-o-matic ([http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)) list
# Added many extra repository
#
[B]# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
#  gpg &#8211;keyserver subkeys.pgp.net &#8211;recv KEY
#  gpg &#8211;export &#8211;armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
#  wget URL &#8211;quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
#  sudo apt-key add FILE[/B]

---

### Post by tchoklat on 2007-01-17
thanks, therefore for the message;

W: GPG error: [http://cle.linux.org.tw](http://cle.linux.org.tw) i386/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E59C36EB476A8659


I should enter the command;
**  gpg &#8211;keyserver subkeys.pgp.net &#8211;recv **E59C36EB476A8659

if so, I receive this message;

usage: gpg [options] [filename]


tchoklat

---

### Post by tchoklat on 2007-01-18
B 
U
M 
P

---

### Post by David Eikelenboom on 2007-01-19
Hi tchoclat

In this case you should do this

```
wget http://cle.linux.org.tw/candyz/Ubuntu/candyz.key
sudo apt-key add candyz.key

```

Good luck,
David.

---

