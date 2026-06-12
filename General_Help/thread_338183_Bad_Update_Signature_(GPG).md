---
title: "Bad Update Signature (GPG)"
date: 2007-01-14
forum: General Help
---

### Post by hbomb on 2007-01-14
hey all, when i run sudo apt-get update i get these errors, how do i fix this?

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

Any help would be greatly appreciated :)

Thanks :) 

hbomb

---

### Post by bapoumba on 2007-01-14
hello :)

Usually, repos have an authentication key you need to install.

For wine, I did not find it on the site you are downloading from. So I do not know. If you trust them, then ...
[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

For Opera, the gpg key is there : [http://deb.opera.com/]("http://deb.opera.com/")

For [medibutu,]("http://medibuntu.sos-sts.com/fr/index.php") it's all in french for now. I made a little translation, with the exact commands to get the authentication key :
[http://bapoumba.free.fr/?p=13]("http://bapoumba.free.fr/?p=13")

---

### Post by hbomb on 2007-01-14
hey thanks for the quick response. That fixed everything but wine...

Failed to fetch [http://deb.opera.com/opera/dists/etch/Release](http://deb.opera.com/opera/dists/etch/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

And im using the repositories from [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb). I cant seem to find the gpg key for it either.

And im assuming the index files error is a issue with the site (that just now started).

Is there a way to tell apt-get not to check for signatures?

hbomb

---

### Post by bapoumba on 2007-01-14
Well two things :

1- may be contact the repo maintainer to have her/him sign the repos
2- If you trust them, go ahead and do the install. The message is a warning, it won't prevent you from using the repos (not using wine, may be check the forum or the wiki doc to see if they are "official" repos for wine)

---

### Post by hbomb on 2007-01-14
ok, ill try that and thanks for the help, it is most appreciated. :-D

---

### Post by sotdem on 2007-02-05
I just found the solution for the NO_PUBKEY 58403026387EE263. Open a terminal and write these two commands:

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 58403026387EE263
gpg --armor --export  387EE263 | sudo apt-key add -

```

That should fix the problem.

---

### Post by TWO on 2007-12-17
> **sotdem said:**
> I just found the solution for the NO_PUBKEY 58403026387EE263. Open a terminal and write these two commands:

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 58403026387EE263
gpg --armor --export  387EE263 | sudo apt-key add -

```

That should fix the problem.

I know that this was posted some time ago but I wonder if you (or anyone else) could tell me what that command actually does? I am experiencing the exact same problem at the moment, after having added a GPG key for Wine.

Thanks

TWO

---

### Post by FuturePilot on 2007-12-17
For Wine try this
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
This will add the gpg to your trusted sources. Now update the apt sources
```
sudo apt-get update
```

---

