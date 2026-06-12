---
title: "Can't get Tor signing key"
date: 2013-10-30
forum: General Help
---

### Post by MorrisseyJ on 2013-10-30
Hi, 

I am busy trying to install Tor, following the instructions from here: [https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)

All goes fine, until i get asked to add the signing key
> 
 We provide a Debian package to help you keep our signing key current. It is recommended you use it. Install it using 

apt-get install deb.torproject.org-keyring


Entering

> sudo apt-get install deb.torproject.org-keyring 

gives:
> E: Unable to locate package deb.torproject.org-keyring
E: Couldn't find any package by regex 'deb.torproject.org-keyring'


Everything else seems fine as i am able to install Tor with: sudo apt-get install tor. 

Can anyone tell me what is wrong with the signing key?

I am running 13.10, 64 bit. 

Thanks, 

j

---

### Post by Lars Noodén on 2013-10-30
There are three steps there.  

1. modify sources.list, according to the version of Ubuntu you are using by adding something like the following:

deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) saucy main

2. add the gpg key used to sign the packages in Tor's repository

```

gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
sudo apt-get update
sudo apt-get install deb.torproject.org-keyring

```

3. install Tor from the repository


These steps have to be done in order.

---

### Post by MorrisseyJ on 2013-10-31
Yes, i did exactly that but, 

>  	 		 			 			 				sudo apt-get install deb.torproject.org-keyring 			 		

 	
 

still returns:

> E: Unable to locate package deb.torproject.org-keyring
E: Couldn't find any package by regex 'deb.torproject.org-keyring' 			 		

Any ideas?

---

### Post by Lars Noodén on 2013-10-31
I get the same error, but seeing as two other steps added the repository key, it may not matter.

Just be sure to edit the config file very carefully before starting up.

---

### Post by MorrisseyJ on 2013-11-01
@ Lars Noodén: Yes, i can load it fine. What do you mean about editing the config file?

j

---

### Post by Lars Noodén on 2013-11-01
There is a configuration file for Tor:

/etc/tor/torrc

I was thinking in particular that you have checked the exit policy to be sure that you have set it up as a bridge, relay or exit node *on purpose* and not left anything to chance.

---

### Post by MorrisseyJ on 2013-11-04
Ok, thanks. 

j

---

