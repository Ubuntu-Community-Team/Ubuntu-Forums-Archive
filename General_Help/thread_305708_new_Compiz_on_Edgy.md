---
title: "new Compiz on Edgy"
date: 2006-11-23
forum: General Help
---

### Post by kimro on 2006-11-23
Compiz seem to have released a new version and repos seem to have changed.
Since the change, I can't get the Compiz install to work following this directions:  [http://lunapark6.com/?p=2501&cp=2#comments]("http://lunapark6.com/?p=2501&cp=2#comments")

I've tried changing the repository link as described on: 
[http://gandalfn.wordpress.com/2006/11/22/compiz-034-is-out-edgy-repos-change/#comment-401]("http://gandalfn.wordpress.com/2006/11/22/compiz-034-is-out-edgy-repos-change/#comment-401")
But 
[I]gpg –keyserver hkp://wwwkeys.eu.pgp.net –recv-keys 0×483170E9
gpg –export -a 0×483170E9 | sudo apt-key add -[/I]
gives me the following message:

[I]usage: gpg [options] [filename]
gpg: no valid OpenPGP data found. [/I]

Can someone help me set this up or point out what I'm doing wrong ](*,) ? Thank you in advance!!

---

### Post by gborzi on 2006-11-23
The problem is that the gpg command you copied from gandalfn's blog to your console has a single long dash (&#8211;) instead of the correct -- and a "times sign" (×) instead of an x in the key. It worked on my system with
> 
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x483170E9
gpg --export -a 0x483170E9 | sudo apt-key add -

I hope it will work on your system too.

---

### Post by zgornel on 2006-11-23
Worked for me without any keys ... :-k

---

### Post by gborzi on 2006-11-23
> **zgornel said:**
> Worked for me without any keys ... :-k
The key is needed in order to authenticate the packages. You should have read a warning from apt-get (or synaptic) about installing "unverified packages" (or something like that).

---

### Post by kimro on 2006-11-23
Mark on gandalfn (not sure if a visitor or member of Compiz team) posted the following line, which allowed me to get the proper key :D 

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x483170E9 ; gpg --export -a 0x483170E9 | sudo apt-key add -

However, ](*,)  I'm now getting the following message upon sudo apt-get update
Get:5 [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/stable Packages [2456B]
Fetched 2460B in 0s (3610B/s)
Failed to fetch [http://gandalfn.club.fr/ubuntu/dists/edgy/stable/binary-i386/Packages.bz2](http://gandalfn.club.fr/ubuntu/dists/edgy/stable/binary-i386/Packages.bz2) MD5Sum mismatch
Reading package lists&#8230; Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Is this something on my end? or Compiz's end?
If anyone can help, it would be greatly appreciated again.

/or/

Does anyone have a link to tutorial on how to setup Edgy + Compiz besides for [Lunapark6]("http://lunapark6.com/?p=2501")? Lunapark6's tutorial worked perfectly until Compiz changed their repos a few days ago.

PS [Compiz 0.3.4]("http://gandalfn.wordpress.com/2006/11/22/compiz-034-is-out-edgy-repos-change/#comment-409") is the gandalfn link.

---

### Post by RAOF on 2006-11-23
That problem is temporary - gandalfn just needs to update his repository index with the right MD5Sum.  It should work again, just like before.

Incidentally, if you want most of the flashy effects from Beryl but using Compiz, you can use Gandalfn's edgy-dev repository and install the **compiz-freedesktop-extra** and **gnome-compiz-manager-extra** packages.

---

### Post by kimro on 2006-11-24
Thanks RAOF, I'll wait and try again later I guess.

This is my first time attempting to setup Linux for my daily desktop use.
Every other install of apps seem pretty straight forward using apt-get as far as I can see.
But installing 3D Desktop environment has been a bit of work. Is this always the case with Compiz or Beryl? or am I just having some bad luck & timing issue right now?

---

### Post by zgornel on 2006-11-24
> **gborzi said:**
> The key is needed in order to authenticate the packages. You should have read a warning from apt-get (or synaptic) about installing "unverified packages" (or something like that).

True

---

### Post by RAOF on 2006-11-25
> **kimro said:**
> Thanks RAOF, I'll wait and try again later I guess.

This is my first time attempting to setup Linux for my daily desktop use.
Every other install of apps seem pretty straight forward using apt-get as far as I can see.
But installing 3D Desktop environment has been a bit of work. Is this always the case with Compiz or Beryl? or am I just having some bad luck & timing issue right now?

Just bad luck and timing, really.

---

