---
title: "installing program from files"
date: 2020-07-18
forum: General Help
---

### Post by wannabe-programmer on 2020-07-18
I'm trying to install Denemo. I downloaded the .tar.gz file from [http://ftp.gnu.org/gnu/denemo/](http://ftp.gnu.org/gnu/denemo/)
I typed "**tar xvzf denemo-2.4.0.tar.gz**" into the terminal and it worked, but I'm not sure what the next step is. 
It left me with a directory titled **denemo-2.4.0** with bunch of folders and files in it and I'm not sure where to start.
I don't even know what to google because I don't know if this is installing from source, or installing from binary file, etc. 
Could someone point me in the right direction?
Some of the folders in the directory are titled "actions", "build", "libs", "src", "ui", etc.
Then it has a bunch of files like "compile", "config.h.in", "Makefile.am", etc.

---

### Post by gsahli on 2020-07-18
OK, so the filenames compile and Makefile are red flags - you downloaded the source code which would need to be compiled.
I'd try the downloads page where it says to download for Debian (Ubuntu is a Debian derivative). Click on the link that says packages. On the next page, click on Daily. Then download all the files that match --
denemo-data_2.4.2_all.deb ; denemo-doc_2.4.2_all.deb ; denemo_2.4.2_amd64.deb ; ttf-denemo_2.4.2_all.deb	(If you don't find all these you're in the wrong place.)
Now double-clicking on these one-by-one, will bring up the GDebi package installer - install each
Now try running it.

---

### Post by CatKiller on 2020-07-19
> **wannabe-programmer said:**
> I'm trying to install Denemo. I downloaded the .tar.gz file from [http://ftp.gnu.org/gnu/denemo/](http://ftp.gnu.org/gnu/denemo/).

If you want to do the first thing there's no reason to do the second thing. Use the package manager to install software. That software is in the Universe repository. Enable that if it isn't already and then use

```
sudo apt update
sudo apt install denemo
```

---

### Post by wannabe-programmer on 2020-07-19
> **CatKiller said:**
> If you want to do the first thing there's no reason to do the second thing. Use the package manager to install software. That software is in the Universe repository. Enable that if it isn't already and then use

```
sudo apt update
sudo apt install denemo
```

oh thanks, I didn't know it was in the repository. That worked.

---

### Post by wannabe-programmer on 2020-07-19
> **gsahli said:**
> OK, so the filenames compile and Makefile are red flags - you downloaded the source code which would need to be compiled.

yeah, that's what I thought after I looked into it a little more. You wouldn't recommend compiling the source code and installing that way? It seems like a good thing to know how to do.
But I don't need to for this program, it's in the repository.

---

### Post by CatKiller on 2020-07-19
> **wannabe-programmer said:**
> You wouldn't recommend compiling the source code and installing that way?

Compiling from source is an *interesting* thing to learn how to do in its own right, so many users will give it a try at some point. And, obviously, if you're writing your own programs you'll need to compile them yourself. Different projects will use different build systems, so you'd need to use methods appropriate to whichever build system they're using: there'll generally be build instructions as part of the project documentation.

For day-to-day software that you're just wanting to use, though, there's no reason to compile it yourself. That's why we have package managers and package maintainers.

---

