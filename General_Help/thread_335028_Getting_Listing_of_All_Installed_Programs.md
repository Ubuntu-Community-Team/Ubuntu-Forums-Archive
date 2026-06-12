---
title: "Getting Listing of All Installed Programs"
date: 2007-01-09
forum: General Help
---

### Post by fireboxtester on 2007-01-09
I'd like to get a list of all packages I currently have installed so I can easily get them installed again on a new Ubuntu install.

Does apt-get offer this, or maybe Synaptic, or something else?

Much thanks. :KS

---

### Post by raul_ on 2007-01-09
open synaptic and then click in the "state button" down on the left and then "installed"

---

### Post by bodhi.zazen on 2007-01-09
```
dpkg --get-selections | grep -v deinstall > installed-files
```

This makes a list of all installed applications, except those you installed from source, in a file "installed-files"

You can view the list with the editor of choice:

```
gedit installed-files
```

And you can use the list to re-install your applications on a fresh install:

```
sudo apt-get update

sudo apt-get dist-upgrade

dpkg –-set-selections < installed-files
```

---

### Post by tuedel on 2007-01-10
Is there a way to exclude packages from this list that were installed through the meta packages of (k)ubuntu's standard installation, thus leaving only the packages that were manually installed?

---

### Post by fireboxtester on 2007-01-10
> **bodhi.zazen said:**
> ```
dpkg --get-selections | grep -v deinstall > installed-files
```

This makes a list of all installed applications, except those you installed from source, in a file "installed-files"

You can view the list with the editor of choice:

```
gedit installed-files
```

And you can use the list to re-install your applications on a fresh install:

```
sudo apt-get update

sudo apt-get dist-upgrade

dpkg –-set-selections < installed-files
```

Thanks, Bodhi.  This looks like the way to go.  Now two follow up questions:
1. What does apt-get dist-upgrade do?
2. Can I make this method only give me a listing of things I've installed on my free will?  It seems to have a lot of entries that I dont' remember installing e.g., xserver wacom.

---

### Post by bodhi.zazen on 2007-01-10
> **fireboxtester said:**
> Thanks, Bodhi.  This looks like the way to go.  Now two follow up questions:
1. What does apt-get dist-upgrade do?[quote]

apt-get dist-upgrade updates your OS

[quote]2. Can I make this method only give me a listing of things I've installed on my free will?  It seems to have a lot of entries that I don't remember installing e.g., xserver wacom.

Yes, but not so easily. I think you can use the file as is and I would figure apt-get will ignore packages already installed.

If you must, go ahead and do a fresh install

then:
```
dpkg --get-selections | grep -v deinstall > base-files
diff base-files installed-files > my-files
```I think should do the trick ... [-o<

[man diff](http://www.die.net/doc/linux/man/man1/diff.1.html)

---

