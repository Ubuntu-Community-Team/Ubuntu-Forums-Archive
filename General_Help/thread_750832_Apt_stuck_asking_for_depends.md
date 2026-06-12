---
title: "Apt stuck asking for depends"
date: 2008-04-09
forum: General Help
---

### Post by TheForkOfJustice on 2008-04-09
I'm trying to install a homemade desktop package (built on ubuntu-desktop) but due to an error in my control file it insisted on installing packages I didn't want.

I remade the deb package and am trying to install it but I get the same error asking for the packages I didn't want to install with the first version.  It suggest typing in:

```
apt-get -f install
```

but doing that doesn't do a thing and I get the same old apt-error again if I try to install the newer  package.

How do I get rid of the old error so I can install the new package?

---

### Post by simonn on 2008-04-10
Just speculation, but your package might have been copied to apt's cache.

Try running:

```

$ sudo apt-get clean

```

And then try installing it again.

---

### Post by TheForkOfJustice on 2008-04-10
> **simonn said:**
> Just speculation, but your package might have been copied to apt's cache.

Try running:

```

$ sudo apt-get clean

```

And then try installing it again.

That doesn't work.

I believe since I used dpkg originally to install the deb from my hard drive that it may be causing some conflict with apt-get.

I tried the following dpkg commands with no luck:

```
dpkg --forget-old-avail
dpkg --clear-avail
dpkg --clear-selections

```

Any more suggestions?

---

