---
title: "Help On Intel Fortran"
date: 2005-08-13
forum: General Help
---

### Post by Nekrataal on 2005-08-13
Anyone knows how to get intel fortran 9.0 to work on ubuntu Hoary. i have this issue when i try to compile it says this:

```
ifort: error: could not find directory in which g++ resides
```

Obviously i have g++ in its lates version installed so i dont know what could it be. Any help will be apreciated.

---

### Post by Nekrataal on 2005-08-13
Well I get it working, all i have to do was do this two commands:
```
export LC_ALL=C
export LD_LIBRARY_PATH=/opt/intel/fc/9.0/lib

```
The first is because my system is in spanish, the second one, is for the libraries. ah, and make a symbolic link to ifort in /usr/bin
ive wrote a tutorial on my home page for this [http://www.udec.cl/alum/carloinostroza](http://www.udec.cl/alum/carloinostroza) i hope it helps someone.

---

### Post by aev on 2005-10-10
Hi , 

I cannot get it working too. Convert first rpms do deb (i use only the i386 rpms). Then install with dpkg. I followed the instructions on your website but didnt work. Has anyone else tried to install intel fortran?:(  Thanks.

---

### Post by aev on 2005-10-11
:) 

i got it running. It was simple.

just extract the archive and type

```
./install.sh
```

and then follow instructions. If you already have the license file sent in the email use it. If you choose the internet option it may not connect.

then I set up the environment variables in my /home/.bashrc file:
```

source /opt/intel/fc/9.0/bin/ifortvars.sh (.csh)
source /opt/intel/idb/9.0/bin/idbvars.sh (.csh)
```

but then I get this if want to type help:

```

$ ifort - help
ifort: Command line warning: ignoring unknown option '-sTdIn_'
IPO link: can not find "help"
ifort: error: problem during multi-file optimization compilation (code 1)
```

any ideas what this is all about? Thanks.

---

### Post by kleeman on 2005-10-11
You mis-typed:
You need
ifort -help
NOT
ifort - help

---

### Post by aev on 2005-10-11
yeah ... I saw that. Thanks anyway.:D 

BTW also tried the debugger. Looks neat. One must have the 'libXft' libraries for the GUI...

ps: Still a newbie in linux.

---

