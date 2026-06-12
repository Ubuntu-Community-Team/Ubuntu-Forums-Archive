---
title: "How run 32 bits programs in 64 bits ?"
date: 2020-07-19
forum: General Help
---

### Post by aug7744 on 2020-07-19
I will test Lubuntu in next minutes.
Is the 64 bits version.
How run 32 bits programs ?
Need add any package or components ?
If yes is possible download and install in offline avoiding download again allways that I need reinstall Linux ?
I pay for each GB in my internet access and avoid it.
Hmm all packages and any other software is possible download and backup the package in local disk ?
Thanks very much for reply.

---

### Post by guiverc on 2020-07-19
I'll answer some of your questions

Lubuntu has both *amd64* (64-bit) and *i386* (32-bit) installs for x86, both are offered with Lubuntu 18.04 LTS (LTS = *long term support*).  Later releases such as Lubuntu 20.04 LTS however only has *amd64* ISOs, ie. 64-bit.

(Also note it's called *amd64* for both intel or amd cpu's, because AMD created the compatible *op-set* now used by both companies, intel's (IA64) was not x86 compatible, and the marketplace liked the compatible AMD version so it's now called *amd64*)

On an AMD64 (64-bit) architecture, you can add a second *compatible* architecture (eg.32-bit) with a command like

```
sudo dpkg --add-architecture i386
```

FYI:  The kernel uses the terms i386, i486, i586 & i686 to refer to different levels of 32-bit processors, however Debian (& thus Ubuntu) don't distinguish between them, calling them all i386.  i386 & i486 are now obsolete, and i386 assumes i686 for Lubuntu 18.04 LTS.

You can download Lubuntu, and install it off-line.  To download Lubuntu, you can get it from Lubuntu's site, ie. [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

Some of your other questions I don't know how to answer, eg. I don't know what you mean by all packages.  The Lubuntu ISOs include many programs already, what other programs you'll need I don't know As an example with myself,  I use NFS (*network file storage*), thus the package `nfs-common` for me is a must so I download after installation. If you have requirements like that, you'll need to grab them as well as the ISO.

For a clue as to what's included, I'd look in [https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop) which lists packages you'll find on the Lubuntu desktop ISO (20.04 or focal)

As for what release to grab. I'll provide the following.

If you are using 32-bit (x86 or i386) you'll have to use Lubuntu 18.04 LTS with it's LXDE interface. It has full support until 2021-April (most of a year yet).  The main part of it will still receive updates until 2023-April, but that's only part of the system.  Upgrades for this system will require re-installation (as later releases use the LXQt desktop)

Lubuntu 20.04 LTS has the newer/modern LXQt interface. It was released in 2020-April (thus 20.04) with 3 years of full support, 5 years for parts only.  It's the better option for most use-cases if you can use it, but we don' know your end use-case. If you're off-line, security matters less though.

---

### Post by Dennis N on 2020-07-19
Yes 64-bit releases of Ubuntu and its flavors can run 32-bit programs by default. No extra steps or settings are necessary. However, you need to install the necessary 32-bit libraries to support the 32-bit applications. For now at least, you can still install 32-bit libraries from the Ubuntu repositories through the package manager.

To install or reinstall Linux, I believe you need an internet connection to get required packages.

It's probably accurate to say that the majority of users do backups to some local storage.

---

### Post by Holger_Gehrke on 2020-07-19
If the program you want to run is in the repositories, then it probably is available in a 64 bit version. If you've got 32 bit programs they are probably either closed source and possibly quite old or they are 32 bit windows applications you're trying to run through wine.

32 bit programs obviously need 32 bit libraries. So you'll first have to tell the package management that 32 bit packages are acceptable by running 'dpkg --add-architecture i386'. After that you can install the libraries you need for an old program with 'apt install packagename:i386'. The problem is in finding out what the program needs. 'ldd' will tell you what libraries a program uses. You can then use the search on [http://packages.ubuntu.com](http://packages.ubuntu.com) to find them.

Wine should mostly take care of things automatically for windows-programs once it's installed, but you might have to create a separate 32 bit prefix by running something like 'WINEARCH=win32 WINEPREFIX=newDirectoryForSimulatedWindowsEnvironment wine boot' (Don't worry about the error you'll get about not finding boot.exe; you can use whatever you want after 'wine', you just have to give it a reason to actually prepare the prefix; running a non-existant program like 'boot' in the prefix gives wine a reason to initialize it).

Downloading all packages is not a good idea. There's a lot there (at a guess I'd say a few Terabytes; the packages are stored in a 'pool' for all supported versions, so there versions for 16.04 ,18.04, 19.10 and 20.04 all in one directory hierarchy; what packages is for which version of Ubuntu is not stored there but in various other files elsewhere on the server) and most of it you'll never need. It is possible to set up your own mirror of the Ubuntu repositories, but the tools do that are geared towards experienced administrators working for an organization with hundreds of machines; and in that situation it actually makes sense to download **everything** once (and downloads all updates to one machine only) and distribute to all the others internally.

If you're talking about keeping the package files for programs you installed, apt actually does that already to a certain degree. All packages and updates to packages you install end up in '/var/cache/apt/archives'. So making a copy of the content of that directory as a backup before cleaning out that cache with 'apt clean' will give you installable packages you don't need to download again. Getting those to install might get a bit interesting, I've never really tried it beyond trivial cases.

Holger

---

### Post by Dennis N on 2020-07-19
>  So you'll first have to tell the package management that 32 bit packages are acceptable by running 'dpkg --add-architecture i386'
We don't need to do this anymore. That support is now enabled by default.

Verify i386 is supported by dpkg on Ubuntu 64-bit system:
```
dmn@Tyana-vm:~$ dpkg --print-foreign-architectures
i386
```

---

### Post by aug7744 on 2020-08-02
@guiverc
"On an AMD64 (64-bit) architecture, you can add a second compatible architecture (eg.32-bit) with a command like"
That command will download files from internet ?

@Dennis N
"Yes 64-bit releases of Ubuntu and its flavors can run 32-bit programs by default"
Lubuntu 20.04 also ?

@Holger_Gehrke
"ldd' will tell you what libraries a program uses."
Use ldd NAMESOFTWARE ?

"Downloading all packages is not a good idea. There's a lot there (at a guess I'd say a few Terabytes; the packages are stored in a 'pool' for all supported versions, so there versions for 16.04 ,18.04, 19.10 and 20.04 all in one directory hierarchy; what packages is for which version of Ubuntu is not stored there but in various other files elsewhere on the server) and most of it you'll never need."
Is better use that command ldd than see reference information about libraries in repositories web site ?

---

### Post by Dennis N on 2020-08-02
Lubuntu supports 32-bit. You can verify this yourself with the command in post #5. It will output 'i386'.

From my notes, to get a 32-bit program to work, first step was Install: **lib32z1** and **libc6:i386**.

Then, what I generally did was attempt to start the program from the termimal. If there is some library needed, you get an error message as to what it is. Then, you track down the package that provides it (not the same as the library!) and install it. Then repeat until the errors are gone.

Example of an error message:
```
error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory
```

---

### Post by Holger_Gehrke on 2020-08-02
> **aug7744 said:**
> @guiverc
"On an AMD64 (64-bit) architecture, you can add a second compatible architecture (eg.32-bit) with a command like"
That command will download files from internet ?


No, it just tells the package manager that packages for an additional compatible processor architecture are allowed.

> **aug7744 said:**
> 
@Dennis N
"Yes 64-bit releases of Ubuntu and its flavors can run 32-bit programs by default"
Lubuntu 20.04 also ?


LUbuntu is a flavour of Ubuntu, so yes.

> **aug7744 said:**
> 
@Holger_Gehrke
"ldd' will tell you what libraries a program uses."
Use ldd NAMESOFTWARE ?

'ldd' is a low level tool that works directly on the executable file for the program. For example 'ldd /usr/bin/clementine' on my system will list all the libraries my music player uses (all 153 of them ...). The output is one line per library, beginning with the name of the library as stored in the program, followed by '=>' and then the path and name of the file the library is stored in. If you were missing a library the program needs, it would be rather obvious. You could then do a search on packages.ubuntu.com for the library.

> **aug7744 said:**
> 
"Downloading all packages is not a good idea. There's a lot there (at a guess I'd say a few Terabytes; the packages are stored in a 'pool' for all supported versions, so there versions for 16.04 ,18.04, 19.10 and 20.04 all in one directory hierarchy; what packages is for which version of Ubuntu is not stored there but in various other files elsewhere on the server) and most of it you'll never need."
Is better use that command ldd than see reference information about libraries in repositories web site ?

Read the second sentence of my post again. I assumed that you had a 32-bit program already in your 64-bit system, possibly downloaded from somewhere and not installed through the package manager. If you install things through the package manager, dependencies (needed libraries or data files in separate packages or ...) should be downloaded and installed automatically. 'ldd' is useful for finding dependencies if you have a program that isn't from a package; if something comes from a package than the dependency information stored in the package is easier to use and interpret. If you use synaptic, it will show you what packages it wants to download before doing so. I assume muon does something similar. If you're using apt or apt-get then adding the switch '-s' or '--dry-run' to the command will simulate the installation and you can see what would get downloaded. Only if you're trying to install a package using dpkg will you ever need to take care of dependencies and downloading the packages yourself (which is the main reason apt etc were developed).

Holger

---

### Post by aug7744 on 2020-08-13
Thanks for all replies :)

---

