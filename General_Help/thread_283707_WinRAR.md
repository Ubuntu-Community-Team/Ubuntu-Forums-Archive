---
title: "WinRAR"
date: 2006-10-24
forum: General Help
---

### Post by Zeek00 on 2006-10-24
Hey,

I recently downloaded the newest version of America's Army. However the oh so nice people at Filecloud decided to package it using winrar. Winrar is unfortunately not understood by linux.

Is there a version of winrar that is compiled for linux? Is there an alternate program I can use that is capable of reading and unpackaging a winrar file? Will winrar, windows version, run using Cedega? or only WINE?

Zeek ;)

---

### Post by ayoli on 2006-10-24
```
sudo aptitude install unrar
```
then use file-roller (under gnome) to unpack you files

---

### Post by Zeek00 on 2006-10-24
Is fileroller a command line application? or is it a separate program? If it is separate from command line then I do not have such a program. I have Archive Manager.

---

### Post by Zeek00 on 2006-10-24
I downloaded the latest version of File Roller for GNOME and tried to install it:

```

/Desktop/file-roller-2.2.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

Any help?

---

### Post by ~LoKe on 2006-10-24
```
sudo apt-get install gcc
```

---

### Post by tronica on 2006-10-24
fileroller should already be installed

just go to Application - Accessories - Archive manager

or just right click on the .rar and hit extract all.

or to use unrar from the cmd line, cd to the directory with the .rar, and do

> sudo unrar e filename.rar

---

### Post by Zeek00 on 2006-10-24
Thankyou, now I have the program configured. In the install document for File Roller they say to do this:

```
./configure
```
To Configure file

```
make
```
to compile. When I type `make' into the command line I get this error message:

```
bash: make: command not found
```

Whats going on exactly and how can I get around this?

---

### Post by ~LoKe on 2006-10-24
```
sudo apt-get install build-essential make checkinstall && ./configure && sudo checkinstall
```

---

### Post by PriceChild on 2006-10-24
```
sudo apt-get install build-essential
```
I also reccomend the use of "sudo checkinstall" instead of "sudo make install" as it creates a deb package for easy management.

---

### Post by CatKiller on 2006-10-24
> **Zeek00 said:**
> Whats going on exactly and how can I get around this?

You've already got file-roller installed, and you're attempting to compile it from source to install it again. You can't compile it because you haven't installed the **build-essential** package.

---

### Post by ~LoKe on 2006-10-24
> **PriceChild said:**
> I also reccomend the use of "sudo checkinstall" instead of "sudo make install" as it creates a deb package for easy management.

Seconded.

```
sudo apt-get install build-essential make checkinstall && ./configure && sudo checkinstall
```

---

### Post by Zeek00 on 2006-10-24
> **tronica said:**
> fileroller should already be installed

just go to Application - Accessories - Archive manager

or just right click on the .rar and hit extract all.

or to use unrar from the cmd line, cd to the directory with the .rar, and do

First part, I have no Archive Manager in the Accessories menu. Second, when I open up command prompt and type `unrar' I get an unknown command error. the same message comes up when I type:

```
$sudo unrar e AmericasArmy_Generic_part1.rar
```

---

### Post by tronica on 2006-10-24
you must have unrar installed. its real simple

> sudo apt-get install unrar

then lets say the .rar is in your home directory

> cd /home/yournamehere

then untar it

> sudo unrar e filename.rar

your done.

---

### Post by Zeek00 on 2006-10-24
Typed:

```
sudo apt-get install unrar
```

error:

```
~$ sudo apt-get install unrar
Password:
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

```

I do not have unrar on my machine, if I did, when i type `sudo unrar e filename.rar' it should have unpacked no? but instead i get `~$ command not found'

So to put an end to the you have unrar there it is for you. I downloaded ARK and tried it from there and got this error message:

> The utility unrar is not in your PATH.

---

### Post by tronica on 2006-10-24
go here to get it

[ftp://194.88.54.245/pub/debian/pool/non-free/u/unrar-nonfree/unrar_3.5.2-0.1_i386.deb](ftp://194.88.54.245/pub/debian/pool/non-free/u/unrar-nonfree/unrar_3.5.2-0.1_i386.deb)

just download it and doubleclick it to install it

---

### Post by Zeek00 on 2006-10-24
Thankyou, made it alot easier than what everyone else was making it out to be. But I extend a thankyou to everyone else for you efforts in helping me get this working.

---

