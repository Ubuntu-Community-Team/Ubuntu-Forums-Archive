---
title: "Listing installed files from a package?"
date: 2007-01-20
forum: General Help
---

### Post by zanglang on 2007-01-20
Does anyone know how to get a list of installed files from a package in the repository, preferably from the command line?
I know you can use Synaptic, but you have to start it, enter a password, browse through the list and so on so it's a tad troublesome.

---

### Post by featherking on 2007-01-21
If you already have the package you can run

```
dpkg-deb -c (package_name)
```

that should list the contents of the package, you could also run it with the -x switch to extract the files to a folder so you can look through and see whats in there

EDIT: if you dont have the package you can should be able to run 'apt-get -d install (package_name)' from the command line to download the package only, then you could run the dpkg command to list the contents

---

### Post by zanglang on 2007-01-21
Thanks for the reply. Are there other ways though, especially if I don't have the .deb and 'd just like to look up the apt entries? It would seem a little troublesome if, say, I'd want to look for a library packaged with OpenOffice and have to download the 10mb .deb just to do that.

---

### Post by adam_89 on 2008-06-06
You should use this
```

dpkg -L package_name

```

---

