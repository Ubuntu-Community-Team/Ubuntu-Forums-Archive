---
title: "gpg: [stdin]: clearsign failed: secret key not available"
date: 2007-12-14
forum: General Help
---

### Post by jonwatson on 2007-12-14
Hi All,

I am setting up my system to try out some Ubuntu package maintenance. I am following the directions here

[https://wiki.ubuntu.com/PackagingGuide/Recipes/PackageUpdate](https://wiki.ubuntu.com/PackagingGuide/Recipes/PackageUpdate)

And am running into problems with signing the package which is part of step 6. When I run debuild -S -sa, I get this error (snipped);

...
dpkg-source -b brasero-0.6.1
dpkg-source: building brasero using existing brasero_0.6.1.orig.tar.gz
dpkg-source: building brasero in brasero_0.6.1-0ubuntu1.diff.gz
dpkg-source: building brasero in brasero_0.6.1-0ubuntu1.dsc
 dpkg-genchanges -S -sa
dpkg-genchanges: including full source code in upload
dpkg-buildpackage (debuild emulation): source only upload (original source is included)
Now signing changes and any dsc files...
 signfile brasero_0.6.1-0ubuntu1.dsc Jon Watson <me@jonwatson.ca>
gpg: skipped "Jon Watson <me@jonwatson.ca>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1174:
running debsign failed

My key exists:

$ gpg --list-secret-keys
/home/jdw/.gnupg/secring.gpg
----------------------------
sec   1024D/0D3B813E 2006-11-01
uid                  Jon Watson (Valid from 1 Nov 2006) <me@jonwatson.ca>
ssb   2048g/E2CAED45 2006-11-01

And it is exported into the GPGKEY environment variable

$export | grep GPGKEY
declare -x GPGKEY="0D3B813E"

Does anyone know what I'm missing?

Thanks

Jon

---

### Post by jonwatson on 2007-12-15
No one?

Is there somewhere else I might post this and have better luck?

---

