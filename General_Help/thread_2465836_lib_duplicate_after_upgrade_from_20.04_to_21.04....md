---
title: "lib duplicate after upgrade from 20.04 to 21.04..."
date: 2021-08-12
forum: General Help
---

### Post by alain.roger on 2021-08-12
Hi,

after upgrade from ubuntu 20.04 to 21.04 I get the following error:

```
[FONT=monospace][COLOR=#000000]Setting up usrmerge (24ubuntu3) ...[/COLOR]

FATAL ERROR:
Both /bin/systemd-tmpfiles and /usr/bin/systemd-tmpfiles exist.

You can try correcting the errors reported and running again
/usr/lib/usrmerge/convert-usrmerge until it will complete without errors.
Do not install or update other Debian packages until the program
has been run successfully.

dpkg: error processing package usrmerge (--configure):
 installed usrmerge package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 usrmerge
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/FONT]
```

I tried [FONT=monospace]/usr/lib/usrmerge/convert-usrmerge but without success.

Any idea how to solve that issue ?
thx[/FONT]

---

### Post by alain.roger on 2021-08-12
so I found the solution. Just try:

```
[FONT=var(--ff-mono)]cd /var/lib/dpkg/info
[/FONT]sudo rm usrmerge.*
[FONT=var(--ff-mono)]sudo apt-get -f install[/FONT]
```

---

