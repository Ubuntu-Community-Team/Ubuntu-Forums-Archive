---
title: "apt-mirror Does Not Download x32 Folder on x64 Machine"
date: 2013-08-21
forum: General Help
---

### Post by fobos3 on 2013-08-21
Hi,

I downloladed a repository mirror with apt-mirror. I prettry much pasted what was in the sources.list in the apt-mirror configuration file and everything downloaded propely. The problem I am having is that when I run apt-get update it throws:
```
W: Failed to fetch http://127.0.0.1/rep/archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages  404  Not Found
```

My sources list has only one line so far:
```
deb http://archive.canonical.com/ubuntu precise partner
```

On closer inspection I can confirm that, indeed, the binary-i386 folder is not present but the amd64 is. So my question is: How can I make apt-mirror to download the 32-bit folder?

P.S.
apt-get reports a hit on amd64. Here is the full output:
```
Hit http://127.0.0.1 precise Release.gpg
Hit http://127.0.0.1 precise Release
Hit http://127.0.0.1 precise/partner amd64 Packages
Ign http://127.0.0.1 precise/partner TranslationIndex
Err http://127.0.0.1 precise/partner i386 Packages
  404  Not Found
Ign http://127.0.0.1 precise/partner Translation-en_GB
Ign http://127.0.0.1 precise/partner Translation-en
W: Failed to fetch http://127.0.0.1/rep/archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages  404  Not Found
```

E: Some index files failed to download. They have been ignored, or old ones used instead.

Update
Adding the line
```
deb-i386 http://archive.canonical.com/ubuntu precise partner
```
seems to have fixed the problem, but isn't the deb identifier supposed to tell apt-mirror to download both?


Regards

---

### Post by jjaison-daniel on 2013-08-22
Yes, default apt-mirror only download the OS architecture binary if your OS is x64 bit then default it will only download x64 bit binaries.
Similarly if your OS is x86 bit then you have to use deb-amd64 to download x64 bit, otherwise it will only download x86(32 bit x86) binary. Similarly for other architecture.

---

