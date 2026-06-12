---
title: "Quassel Core won't open SSL Cert"
date: 2017-08-20
forum: General Help
---

### Post by Krause on 2017-08-20
Anyone use Quassel core on Ubuntu? I went nuts last night trying to figure out why it would always say it could not open the cert at the location with "error: 5" after I created it (with an exact copy and paste of the command in the Quassel info page on their site).

I tried the version in the repos, the PPA version (same version number though) and the PPA GIT version. All the same result.

The server runs fine, I can get clients to connect, it functions. But I can not get it to open the cert pem file.

I then tried the Statically linked core version from the Quassel site, which is an x86 all dependencies included version and that read the SSL cert in the default location perfectly. So I thought maybe something is wrong with my ubuntu install so I tried it in a newly created ubuntu Virtualbox VM (using the latest Dev snapshot just incase the issue was something with my specific version of Ubuntu). The repo version still could not open the cert, same error.

I'm now using a version I compiled from source (which reads the cert fine) but I really would rather just be able to use the version from the repos in the future. Anyone know what's wrong, or if I'm doing something wrong? And if im not, why do the prebuilt repo/PPA versions wont open the cert files?

---

