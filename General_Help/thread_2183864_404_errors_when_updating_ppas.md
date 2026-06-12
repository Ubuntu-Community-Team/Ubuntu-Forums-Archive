---
title: "404 errors when updating ppas"
date: 2013-10-26
forum: General Help
---

### Post by ShinigamiH4ck3r on 2013-10-26
these two ppas seem to be giving me 404s since my upgrade to 13.10 from 13.04.
they seem important, so i dont want to just disable them. wondering if this is just a temp problem or should i remove the ppas

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages
  404  Not Found

---

### Post by Bashing-om on 2013-10-26
ShinigamiH4ck3r; Hi !

Standard operating procedure is to disable the 3rd party PPAs prior to upgrading, and upon completion, re-enable those PPAs if they are supported in the new version.
To see what is going on - and to see the entire address -
post back the outputs of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]the tale will be told
[/INDENT][/INDENT]

---

### Post by ShinigamiH4ck3r on 2013-10-26
Those are third party ppas? and yes i know i did disable the third party ones. but ill still post back the results you want...

---

### Post by grahammechanical on 2013-10-26
All PPAs are third party software. Personal Package Archive. So, the software is not in the normal Ubuntu archives or repositories. The upgrade process changes the addresses of the repositories from raring to saucy and it has changed the addresses of the PPAs from raring addresses to saucy addresses which do not exist. Hence, the error messages.

---

