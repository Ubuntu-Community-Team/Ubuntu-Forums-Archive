---
title: "Error on CLI, libdvd-pkg: using apt-get"
date: 2015-11-13
forum: General Help
---

### Post by qkzoo on 2015-11-13
So short story is, I installed a bunch of different dvd ripping software trying to find one that I liked and worked.  Eventually I found one, but now I get this error whenever I do an apt-get operation.  To be honest, I'm not even sure what I installed prior to this, as I wasn't having much luck until I finally found k9copy.

```

libdvd-pkg: Package libdvdcss2-1.3.99-1 was removed, stop processing...

```

I'm not sure where to go with this, but I'd like to get rid of this error.  My apt-get operations still seem to be working just fine, I can still install and update, etc.

Thanks in advance for any assistance!

I'm running Lubuntu on a Toshiba Satellite.

---

### Post by matt_symes on 2015-11-14
Hi

> **qkzoo said:**
> So short story is, I installed a bunch of different dvd ripping software trying to find one that I liked and worked.  Eventually I found one, but now I get this error whenever I do an apt-get operation.  To be honest, I'm not even sure what I installed prior to this, as I wasn't having much luck until I finally found k9copy.

```

libdvd-pkg: Package libdvdcss2-1.3.99-1 was removed, stop processing...

```

I'm not sure where to go with this, but I'd like to get rid of this error.  My apt-get operations still seem to be working just fine, I can still install and update, etc.

Thanks in advance for any assistance!

I'm running Lubuntu on a Toshiba Satellite.

You're running Lubuntu 15.10 ? libdvd-pkg is a new package that builds libdvdcss2 from source and replaces libdvdread. 

libdvdcss2 allows you to play encrypted dvds.

I'm not sure what pulled it in as, on my Xubuntu 15.10 installation, nothing seems to depend on it.

```
matthew@matthew-Standard-PC-i440FX-PIIX-1996:~$ apt-cache rdepends libdvd-pkg
libdvd-pkg
Reverse Depends:
matthew@matthew-Standard-PC-i440FX-PIIX-1996:~$
```

Something pulled it in though.

You could remove it but you would not be able to play encrypted DVDs. 

Another option is to run the command below to attempt to download the libdvdcss2 source and get libdvd-pkg to build it for you.

```
sudo dpkg-reconfigure libdvd-pkg
```

Select the option to download the source and build it.

When it asks if you want to install the APT hooks, i would select the option "yes".

Post back on efficacy.

Kind regards

---

### Post by qkzoo on 2015-11-14
Well, I went ahead and followed your suggestion for downloading and building libdvd-pkg, because, why not?

In any case, I did a quick apt-get update && apt-get upgrade and I'm no longer seeing that error message, so thanks!

---

### Post by matt_symes on 2015-11-14
Hi

I glad it's fixed. I'll mark this thread as [solved] for you.

Kind regards

---

