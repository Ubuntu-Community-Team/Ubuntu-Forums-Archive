---
title: "problem running libreoffice"
date: 2013-11-25
forum: General Help
---

### Post by Jpox on 2013-11-25
Hi,

I have a big problem with libreoffice (on Kubuntu 12.04)

I wanted to add libreoffice-pdfimport to my suite and so I typed:

```
sudo apt-get install libreoffice libreoffice-pdfimport
```

It was my error because, in this way, i reinstalled libreoffice too. But now I have a problem bacause libreoffice doesn't run any more.

when I type 

```
libreoffice
```

I get

```
/usr/lib/libreoffice/program/soffice.bin: error while loading shared libraries: libjvmaccesslo.so: cannot open shared object file: No such file or directory


```

I tried to remove and reinstall libreoffice again, but now I always get this error.

Can anybody help me please? I need libreoffice for my work

Thank you

---

### Post by vanadium on 2013-11-25
I suggest purging your libreoffice install and then reinstalling it from the standard Ubuntu 12.04 LTS repositories.

---

### Post by Jpox on 2013-11-25
Ok, but how can I install it from standard Ubuntu 12.04 LTS repositories?

Because I typed in my terminal as suggested on the web

```
sudo add-apt-repository ppa:libreoffice
```

but then libreoffice doesn't work.

---

### Post by ccmiller12 on 2013-11-25
It might be better to install libreoffice from the software centre. Just search libreoffice and download what app you need (Writer, Calc, Impress, ect...).

---

### Post by Jpox on 2013-11-25
I tried to install from Muon Software Center but nothing todo, I still get the same error when I try to launch libreoffice:


```
/usr/lib/libreoffice/program/soffice.bin: error while loading shared libraries: libjvmaccesslo.so: cannot open shared object file: No such file or directory

```

What others solutions could I try?

---

### Post by bapoumba on 2013-11-25
[https://answers.launchpad.net/ubuntu/+question/238453](https://answers.launchpad.net/ubuntu/+question/238453)

As everyone said. remove the ppa and reinstall from the regular ubuntu repos.

---

### Post by Jpox on 2013-11-25
ok, I removed the repository.

But how can I now install libreoffice from the regular ubuntu repos.? Colud you explain me, please?

---

### Post by bapoumba on 2013-11-25
Once the ppa removed, update the sources.list and install libreoffice
```
sudo apt-get update
sudo apt-get install libreoffice
```

libreoffice is a metapackage, all the other packages wil be installed with it.

---

### Post by Jpox on 2013-11-25
Ok I did this but now i can't install libreoffice any more.

I get this after typing sudo apt-get install libreoffice:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.5.7~) but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by vanadium on 2013-11-26
There is a procedure described here ([http://www.thepowerbase.com/2012/04/how-to-fix-broken-packages-in-ubuntu-or-debian/](http://www.thepowerbase.com/2012/04/how-to-fix-broken-packages-in-ubuntu-or-debian/)) which involves the use of ppa purge. This does not only remove the repositoory, but also downgrades the packages from the archive.

You just have removed the PPA. Presumably, not all packages introduced by your custom PPA were downgraded.

You could try the following.
1) Reinstate the offending PPA
2) "sudo apt-get update"
3) Now follow the procedure outlined in the link I gave. It involves removing the offending PPA using PPA purge, which should revert all affected packages to the standard packages of Ubuntu. After that, you should be able to install libreoffice without error.

---

### Post by bapoumba on 2013-11-26
Thanks vanadium, I overlooked the fact libreoffice from the ppa had not been removed.

---

### Post by Jpox on 2013-11-29
Thank you very much, I follow this last advise and I was able to reinstall the version 3.5.7 of Libre Office.

There is just a thing that I can't understand and this is, why before I was able to install the new version of LO, and later I had all these problems?

Thank you and have a nice weekend!!

---

### Post by bapoumba on 2013-12-01
> **Jpox said:**
> Thank you very much, I follow this last advise and I was able to reinstall the version 3.5.7 of Libre Office.

There is just a thing that I can't understand and this is, why before I was able to install the new version of LO, and later I had all these problems?

Thank you and have a nice weekend!!

A Linux distribution ties up packages. Some depend on others according to their versions through the dependency system also called the dependency tree. LO is written by a team, it performs some specific tasks, but relies on other packages written and maintained by other developers (why write again stuff that is made available ?). The package manager can read the necessary info in packages when it installs, removes, updates and such and requires that all the packages are at the correct version level.

Using a ppa is either to incorporate packages that are not readily available in the repositories of said distribution, or to install newer versions. But in that case, some libraries or other kind of packages have to be upgraded too, and do not match the distribution scheme. A ppa should handle this nicely. In some cases, it creates dependency problems or even [dependency hell]("https://en.wikipedia.org/wiki/Dependency_hell") in the worst cases. The package manager complains or can get stuck.

When removing a ppa, all the modified dependencies should be returned back to their distribution level so that the package manager remains happy. This is what you did with the ppa purge procedure.

---

### Post by Jpox on 2013-12-01
Ah ok!!

Thank you very much for your explanation!! :)

---

### Post by bapoumba on 2013-12-01
You are very welcome :)

---

