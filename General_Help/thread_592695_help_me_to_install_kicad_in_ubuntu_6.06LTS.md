---
title: "help me to install kicad in ubuntu 6.06LTS"
date: 2007-10-26
forum: General Help
---

### Post by prasad_pari on 2007-10-26
I am getting the below error when i try to down load and install kicad.




W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277

Please help to install kicad in ubuntu 6.06LTS 


thanks in advance 
Prasad

---

### Post by az on 2007-10-26
Debs are not binary-compatible across distros or even across releases.  

What I suggest you do is try to backport it yourself.

Add the ubuntu source repository for Gutsy Universe.  Do not add any other gutsy repos to your list - you don't want to have mixed sources in your list.

The update and run

sudo apt-get build-dep kicad
and it should install the things you will need to build it from source.  Then install the source and compile it.

sudo apt-get source kicad.

It should get the source from gutsy, but build a binary for Dapper.


Good luck.

Don't forget to remove the source repository from your list afterwards.

---

### Post by prasad_pari on 2007-10-27
thanks a lot for your reply,

but, I am totally a new B to ubuntu.

I have to know how to add gutsy repositories and build the binary.

kindly help me to do this.

And when i tried to add repository, I am getting below error message

E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_pool_universe_dists_gutsy_universe_source_Sources - open (2 No such file or directory)


thanks in advance
Prasad

---

### Post by az on 2007-10-29
See this:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by prasad_pari on 2007-11-23
Sir,

I am still struggling to compile kicad source code. there is no configuration file in kicad folder.

Please please help me to solve the issue


thanks in advance 
Prasad

---

### Post by woody_green on 2008-02-05
> **az said:**
> Debs are not binary-compatible across distros or even across releases.  

What I suggest you do is try to backport it yourself.

Add the ubuntu source repository for Gutsy Universe.  Do not add any other gutsy repos to your list - you don't want to have mixed sources in your list.

The update and run

sudo apt-get build-dep kicad
and it should install the things you will need to build it from source.  Then install the source and compile it.

sudo apt-get source kicad.

It should get the source from gutsy, but build a binary for Dapper.


Good luck.

Don't forget to remove the source repository from your list afterwards.

I tried doing that, but it just didn't work for me. Kicad depends on libwxbase and libwxgtk, which in turn depend on the newest versions of certain libraries, such as libc6, which are ideally available in Gutsy. I even tried to backport from Feisty (because there's also a version of Kicad there) but because of the dependencies I gave up. So I upgraded from Dapper to Gutsy and used Synaptic to install Kicad. Maybe upgrading from Dapper to Edgy and then backporting from Feisty would be another solution but I think it's easier to upgrade to either Gutsy or Feisty.

---

