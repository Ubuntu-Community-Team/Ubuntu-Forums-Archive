---
title: "PLS help me!:("
date: 2007-03-04
forum: General Help
---

### Post by ~&#730;JaZ&#730;~ on 2007-03-04
Hi! 
I am a linux (ubuntu 6.10) rookie:)...and i have a problem with my updates and installing files..and i could need a little help with figuring out my problem and salving it!) so here is it:

when i try to run Update manager an error pops up saying:

[CENTER]Software index is broken[/CENTER]

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

so when i try the terminal with sudo apt-get install -f i get some errors about unsolved dependences with fontconfig-config (= 2.3.2-7ubuntu2)  and that some packages have been held back wen i try to use the synaptic it shows that an package is broken when i find it (libfontconfig 1) i cant fix it or reinstal in or delet it - nothing.

I also tried sudo apt-get update and it starts normaly but at the end i get:

W: GPG error: [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I realy need to install some programs for my work and i cant lose any data (to big for burning on a disc)!..So if somebody could help me out with that...and i realy dont know much about linux so any details -how to- would be realy helpful! TNX

Z!

---

### Post by Kateikyoushi on 2007-03-04
The following should solve the key problem. Replace KEY with your key.

```
gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -
```

---

### Post by ~&#730;JaZ&#730;~ on 2007-03-04
no it doesnt do it....i still get the same error...

jaz@pandora:~$ gpg --keyserver subkeys.pgp.net --recv 58403026387EE263
gpg: requesting key 387EE263 from hkp server subkeys.pgp.net
gpg: key 387EE263: public key "Scott Ritchie <scott@open-vote.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
jaz@pandora:~$ gpg --export --armor KEY | sudo apt-key add - 58403026387EE263

any other ideas?

---

### Post by Kateikyoushi on 2007-03-04
You did not write the key to the right place.

> gpg --keyserver subkeys.pgp.net --58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -

---

### Post by ~&#730;JaZ&#730;~ on 2007-03-04
Me again :) ...it stil doesnt work... this is what i get:

jaz@pandora:~$ gpg --keyserver subkeys.pgp.net --58403026387EE263
gpg: Invalid option "--58403026387EE263"
jaz@pandora:~$ gpg --export --armor 58403026387EE263 | sudo apt-key add -
OK

---

### Post by Kateikyoushi on 2007-03-04
It was my turn for a typo. this should work.

```
gpg --keyserver subkeys.pgp.net --recv 58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -
```

---

### Post by ~&#730;JaZ&#730;~ on 2007-03-04
hm..the command worked but i still cant update, same error:(...

---

### Post by Kateikyoushi on 2007-03-04
Try to reinstall the problematic packages.

```
sudo aptitude reinstall packagename
```

---

### Post by ~&#730;JaZ&#730;~ on 2007-03-04
Finaly!!! Thank u! I was trying to solve it for 3 weeks by my self! and at the end it was just this one line!!:) hehe...i realy cant thank u enough!

---

### Post by Kateikyoushi on 2007-03-04
I am actually surprised that it worked, in my similar case it did not.

---

### Post by ~&#730;JaZ&#730;~ on 2007-03-04
i think i messed it up when i was trying to install adesklets...i was following some instructions on the internet...and then suddenly it stopped working..i also deleted a part of my sourcelist but i managed to replace it:)! tnx again!

---

