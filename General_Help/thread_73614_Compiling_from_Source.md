---
title: "Compiling from Source"
date: 2005-10-09
forum: General Help
---

### Post by Comrade on 2005-10-09
I want to compile certain programs from source. However, I know that apt-get only works with the binaries, so I don't have easy access to the source code. Is there a simple way to download the source and compile any application that's in synaptic without using a web browser to navigate to the application's source code.

For example, I want to compile Python from source. Is there any easy way of doing this, besides download the tarball, which always ends up in cryptic make errors?

---

### Post by Hairy_Palms on 2005-10-09
apt-build is avaialable i beleive if you have the souce repositorys but its experimental iirc

---

### Post by Comrade on 2005-10-09
Is there a command to get the source for an application? Or do I have to manually look for it on the internet?

Like apt-get source or something , even though I know that's not a legal command.

---

### Post by jamesstansell on 2005-10-10
[QUOTE=Comrade]Is there a command to get the source for an application? Or do I have to manually look for it on the internet?

Like apt-get source or something , even though I know that's not a legal command.[/QUOTE]

Actually, it is a legal command.  From the manpage:

```
       source source causes apt-get to fetch source packages. APT will examine

              the  available packages to decide which source package to fetch.
              It will then find and download into the  current  directory  the
              newest available version of that source package.
```

---

### Post by Zotova on 2005-10-10
[QUOTE=Comrade]I want to compile certain programs from source. However, I know that apt-get only works with the binaries, so I don't have easy access to the source code. Is there a simple way to download the source and compile any application that's in synaptic without using a web browser to navigate to the application's source code.

For example, I want to compile Python from source. Is there any easy way of doing this, besides download the tarball, which always ends up in cryptic make errors?[/QUOTE]

The best way I find is to go to the developers website and download the source code as you will get the most recent version.

If you are getting errors are you 100% sure you have all the dependencies and tools required to compile and install the program?

---

### Post by dcraven on 2005-10-10
Good guess. The "apt-get source" command is the one you want. Please read the man pages for more detailed info.
```
man apt-get
```
Cheers,
~djc

---

