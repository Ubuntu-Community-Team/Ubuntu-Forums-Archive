---
title: "How do you add a repository key"
date: 2007-03-18
forum: General Help
---

### Post by trcmag on 2007-03-18
I am installing gshowtv ([http://gshowtv.sourceforge.net/](http://gshowtv.sourceforge.net/)) and I added the repository to synaptic now I get the following error

W: GPG error: [http://debian.vakevainen.fi](http://debian.vakevainen.fi) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2BFAFC26585DECB0 

I was told to do the following

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 585DECB0
sudo apt-key add <the>

when I try to add a key it asks me for a file.  I tried to find one on the site and I don't know what I am looking for or how to get it.  I tried to put the above into my terminal and it gave me an error.

where do I type the above or what do I do with the above line??

---

### Post by confused57 on 2007-03-18
Maybe this will work for you:
[http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773](http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773)

---

### Post by sgtbob on 2007-03-27
I have the same problem with Ubuntu and trying to enter a repository.  Here is the error message I got with no follow-on instructions:

[COLOR="Blue"]W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263[/COLOR]


Can someone advise what/how to proceed?

Bob:confused:

---

### Post by madjo on 2007-09-02
I created a small script to solve that problem
```
#!/bin/sh
gpg --keyserver subkeys.pgp.net --recv $1
gpg --export --armor $1 | sudo apt-key add -
```
save this script to a file and give that file executable powers. (chmod 755 for instance and place it somewhere in the 'PATH')
and now when you encounter that problem, call the script with the code behind the "NO_PUBKEY" like this:
```
$ aptkeys 58403026387EE263
```

---

