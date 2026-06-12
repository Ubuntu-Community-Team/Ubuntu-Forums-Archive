---
title: "Apache 2.2.2 checkinstall fails"
date: 2006-12-03
forum: General Help
---

### Post by mwells on 2006-12-03
Hi all,

I'm currently trying to compile apache 2.2.2 on edgy using [this]("http://doc.gwos.org/index.php/Latest_Apache_and_PHP") guide.

When I get to running checkinstall the program ends with;
```

cp: setting permissions for `/usr/local/apache2/modules/httpd.exp': No such file or directory
cp: preserving ACL for `/usr/local/apache2/modules/httpd.exp': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/matthew/Desktop/src/httpd-2.2.2/support'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
```

Anybody have any clues why it would be terminating here? I havnt tried running 'install' as I was ideally wanting to make the .deb. and I'm not entirely sure how I would go about removing it all easily with install

Many thanks indeed

~Matt

---

