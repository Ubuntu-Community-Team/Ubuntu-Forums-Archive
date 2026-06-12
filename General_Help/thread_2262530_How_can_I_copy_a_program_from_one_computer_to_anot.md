---
title: "How can I copy a program from one computer to another?"
date: 2015-01-25
forum: General Help
---

### Post by Ralf_Hutter on 2015-01-25
Hello everybody, computer A has a program that computer B hasn't. How do i get it from A to B? Do i just need to copy the folder(s), and if yes, where are they? In this case, i'm talking of the program Ripper X. Additionally: Could it be problem that A runs Lubuntu and B runs MX ([http://www.mepiscommunity.org/mx)?](http://www.mepiscommunity.org/mx)?)

---

### Post by Holger_Gehrke on 2015-01-25
Bad news: Linux does things **very** differently from Windows. Almost all programs go into one directory, the libraries all go into another one, system wide configuration files all into a third. Only **very** large programs -- often badly behaved commercial multiplatform applications -- go into directories of their own, usually inside the directory '/opt'

There is a system that keeps this potential chaos under control, and that's the package manager. It keeps a record of what file which program installed, which other packages (libraries or programs or data) it needs (and during installation installs the dependencies of a program before the program itself) and dozens similar things. 

You really should try to simply find a package for mepis. Failing that, you could try building from source and installing into '/usr/local', thats what that directory hierarchy is for.

What you're proposing is in theory doable, but would result in quite some  chaos on the target machine. Ripper X is basically a graphical front end for the cdparanoia library and various command line encoders (mp3, ogg, flac ...) so there could be hundreds of files it needs to work. The package manager on mepis would not know about the files you copied, deinstalling or keeping it up to date would be completely your own responsibility.

Since both Mepis and Ubuntu are Debian based, you could try to get the package from Ubuntu and install it on Mepis, but I would expect a lot of trouble with dependencies. And again, his could seriously impact the package management on mepis.

---

### Post by Ralf_Hutter on 2015-01-25
Ok, thanks. I understand from your answer, that even between exactly the same distributions it is not recommended or not even really practicable to just copy folders. The only reasonable way to get a program is the internet?

---

### Post by ajgreeny on 2015-01-25
If you have problems downloading the installation files, for whatever reason, you could copy all the ***package*.deb** files from **/var/cache/apt/archives **of computer A to the same folder in computer B using a flash drive or similar, and save yourself some downloads, but this will depend on the two machines running the same architecture (32bit vs 64bit) and version of OS.

---

