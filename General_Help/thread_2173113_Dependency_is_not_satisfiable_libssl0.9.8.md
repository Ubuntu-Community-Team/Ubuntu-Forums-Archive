---
title: "Dependency is not satisfiable: libssl0.9.8"
date: 2013-09-08
forum: General Help
---

### Post by DeMus on 2013-09-08
[COLOR=#333333][FONT=Lucida Grande]I am trying to install a package using a deb file and get the error message as written in the subject. I do however have libssl1.0.0 installed, which as far as I can tell, is a newer version.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]How do I tell the installer to use the 1.0.0 version which is installed?[/FONT][/COLOR]

---

### Post by HiImTye on 2013-09-08
that depends on the error. if it tells you it depends on a version greater than a specific version, you can probably force install it. if it depends on a specific version (displayed with an equals sign), then you'll have to find another work around.

before we get there, can you paste the output you're getting?

---

### Post by DeMus on 2013-09-08
[ATTACH=CONFIG]246099[/ATTACH]

This is the warning I get. As I wrote in the original message I have libssl1.0.0 installed. This installation obviously needs an older version. Question is how to do that? How do I tell the installer that I have a newer version, or how do I install the older version (as well)?

---

### Post by HiImTye on 2013-09-08
ah, you're using the graphical installer, instead use dpkg
```
dpkg -i <file>.deb
```

---

### Post by DeMus on 2013-09-08
sudo dpkg -i spotlite-amd64.deb
[sudo] password for xxx: 


Selecting previously unselected package spotlite.
(Reading database ... 147258 files and directories currently installed.)
Unpacking spotlite (from spotlite-amd64.deb) ...
dpkg: dependency problems prevent configuration of spotlite:
 spotlite depends on libssl0.9.8; however:
  Package libssl0.9.8 is not installed.


dpkg: error processing spotlite (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 spotlite

libssl1.0.0 is installed.

Any idea how to make this work? I would be very grateful.

---

### Post by HiImTye on 2013-09-08
I see, it's a separate package, not just an incrimental version difference. check if it's available in your repos
```
apt-cache search libssl
```
and if it is, install it
```
sudo apt-get install libssl0.9.8
```
if no other errors, install the .deb

---

### Post by DeMus on 2013-09-08
I did a Google search and ended up at the Debian site where I could download a package of libssl0.9.8. Installation went well, and afterwards installing the other program as well.
Thank you very much for all your help.

---

