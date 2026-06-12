---
title: "Help with GCC cross compiler to MMIX?"
date: 2007-11-10
forum: General Help
---

### Post by pqnelson on 2007-11-10
I'm trying to write some C code targeting the MMIX theoretical architecture, so I was looking into cross compilers. My gut instinct was the cross compiler tools [http://www.kegel.com/crosstool/](http://www.kegel.com/crosstool/) but it doesn't support MMIX!

So is there any easy way on ubuntu to install a GCC cross compiler to MMIX? Or do I have to do it all manually? I would really prefer not doing it manually...

[edit]: Also, I have installed the latest version of the MMIX tools (mmmix, mmix, mmixal, etc.) and have them in my /usr/bin/ directory. So all I need to do really is to "merely" have the MMIX cross compiler for the GCC...any script/etc. would be great.

---

### Post by pqnelson on 2007-11-10
I wrote a script for ubuntu gutsy that I think should work, but if anyone sees something wrong please post a revised version of the script:

```
#!/bin/sh

# this installs the mmixware from Knuth, then it installs the GCC C compiler,
# the binutils, and some dependency called the newlib
make_binutils()
{
	sudo apt-get install texinfo
	sudo apt-get install build-essential
	# get the gnu binutils
	wget ftp://mirrors.kernel.org/gnu/binutils/binutils-2.17.tar.gz
	mv binutils-2.17.tar.gz /usr/src/

	# untar, then configure, make, make install the binutils
	sudo tar -xvzf /usr/src/binutils-2.17.tar.gz --directory /usr/src/

	# configure the compiler...
	mkdir tmp1
	cd tmp1
	/usr/src/binutils-2.17/configure --target=mmix
	make /usr/src/binutils-2.17/Makefile.in all
	make /usr/src/binutils-2.17/Makefile.in install
	cd ..
}

make_gcc() 
{
	make_binutils

	# get the gnu c compiler
	wget ftp://mirrors.kernel.org/gnu/gcc/gcc-4.2.0/gcc-core-4.2.0.tar.bz2
	mv gcc-core-4.2.0.tar.bz2 /usr/src/
	# get the newlib
	wget ftp://sources.redhat.com/pub/newlib/newlib-1.15.0.tar.gz
	mv newlib-1.15.0.tar.gz /usr/src/

	# now we'll work on the new library
	tar -xzf /usr/src/newlib-1.15.0.tar.gz --directory /usr/src/

	# now we'll rename it to "unify" the library and the gcc...
	mv /usr/src/newlib-1.15.0/ /usr/src/gcc-4.2.0

	# now we'll untar the gcc
	tar -xjf /usr/src/gcc-core-4.2.0.tar.bz2 --directory /usr/src/

	# make a tmp directory...
	mkdir tmp2
	cd tmp2
	# configure the gcc for mmix...
	sudo /usr/src/gcc-4.2.0/configure --target=mmix

	sudo make /usr/src/gcc-4.2.0/Makefile.in all
	sudo make /usr/src/gcc-4.2.0/Makefile.in install
	cd ..
}
mkdir src
cd src
make_gcc
cd ..
sudo rm -rf src

```

I have thoroughly tested this and it works :)

To call the gcc to compile for mmix, simply type mmix-gcc in the command line :)

Also, here is a script to install the latest version of Knuth's mmixware:
```
#!/bin/bash

# this should download and install the cweb utility, if you 
# already have it then this does nothing
sudo apt-get install texlive-extra-utils

echo "Installing the MMIXware.\n"	
# get the mmixware source code
wget http://www-cs-faculty.stanford.edu/~knuth/programs/mmix-20060918.tar.gz
tar -xvf mmix-20060918.tar.gz
# we don't need the archive anymore, get rid of it to free space up
rm mmix-20060918.tar.gz
cd mmix-20060918
make all
sudo mv mmixal /usr/bin/
sudo mv mmix /usr/bin/
sudo mv mmotype /usr/bin/
sudo mv mmmix /usr/bin/
echo "MMIXware installation complete.\n"
make clean
```

Just some stuff for people who are lazy like me...

---

