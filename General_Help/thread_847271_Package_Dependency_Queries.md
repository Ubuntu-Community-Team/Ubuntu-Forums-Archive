---
title: "Package Dependency Queries"
date: 2008-07-02
forum: General Help
---

### Post by professorYaffle on 2008-07-02
I'm still climbing up the learning curve for apt/dpkg etc.. I'm trying to work out how to find out what packages depend on a given package.

Preferably at the command line; also with the option to scan either just installed packages or all available packages in the currently configured repositories.

(I can see a crude way to do the former: fire up adept_manager or similar, select package for deletion and see what else would be deleted as well. but that's not very elegant!)

Could someone point me in the right direction please?

---

### Post by sdennie on 2008-07-02
> **professorYaffle said:**
> I'm still climbing up the learning curve for apt/dpkg etc.. I'm trying to work out how to find out what packages depend on a given package.

You could use apt-cache for this

To get all the packages that directly depend on a package:
```

apt-cache rdepends some_package

```

The recursively get that data:

```

apt-cache rdepends --recurse some_package

```

To do the reverse (get all the things that some_package depends on), just replace "rdepends" with "depends".

> 
Preferably at the command line; also with the option to scan either just installed packages or all available packages in the currently configured repositories.


The above commands show anything in the repos.  To limit it to just installed, just add "--installed" to either command.

---

### Post by professorYaffle on 2008-07-02
Excellent, Just what I needed.

Many thanks.

---

