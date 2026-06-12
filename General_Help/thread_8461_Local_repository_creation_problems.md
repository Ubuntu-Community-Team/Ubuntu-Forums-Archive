---
title: "Local repository: creation problems"
date: 2004-12-17
forum: General Help
---

### Post by paradox on 2004-12-17
For fast line problem reason i must download *.deb and install packages later.

I insert in sources.list this line:

deb file:/path ./

and later i create Packages list like this command (from root...):

$ apt-ftparchives packages /path > /path/Packages

$ sudo apt-get update

this command work correctly and resolve dependencies offline...but after this i obtain this error:

err file: ./ libartsc0 1.2.3-1 File not found

(i try install kppp...)  

Where i wrong?

TNX!

---

