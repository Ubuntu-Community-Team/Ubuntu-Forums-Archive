---
title: "Compiling 101"
date: 2007-06-12
forum: General Help
---

### Post by Bablefish on 2007-06-12
I am into gaming and look to add XMESS to the KXMAME frontend I installed through the Synaptic Program Manager. According the the Docs at XMESS it has to be complied as I figure this would also help with some other installs I like to do. IS there any place on the web that will help me learn to compile?

---

### Post by iAlta on 2007-06-12
Lost of places, 

mostly it's something like this

```
./configure

make

make install
```

More info  : [http://www.aboutdebian.com/compile.htm](http://www.aboutdebian.com/compile.htm)

---

### Post by infol on 2007-06-12
compilation of a program is not as hard as you seem to think. normally, you'd start with downloading the source files of the program you wish to compile. the source code generally comes in a zipped tarball, i.e. the file extention ends in .tar.gz or .tar.bz2

what you do next is to unpack the sourcecode - e.g. 
```
tar xzsf filename.tar.gz 
OR
tar xjsf filename.tar.bz2
```
(for more info on the different flags for the "tar" command, use linux's built-in manual - write "man tar" at the command line interface)

then move into the directory where the source code was unpacked - i.e. "cd directoryname\"

now we move on to compilation...

many (if not most) developers provide a configuration script with the source code that will check that you have prerequired packages/libraries installed before moving on to compilation; the configuration script also determines what type of arch (or kernel) you are using, and will set the right parameters for you if you run the script, by invoking 
```
./configure
``` 
Please note that you have to put the dot and slash "./" before the word configure. This phase can take a couple of seconds, to a couple of minutes, depending on the size/compexicity of the program you are trying to compile.

then we go on to actually compiling. type:
```
make
```
at the cli. this may take a little longer than the configuration phase.

the last step is to install the program you just compiled. due to linux' nature as  a secure os, only users with root access are allowed to do this (as this is the phase where you might modify already installed stuff). hence, type
```
sudo make install
``` and then enter your password to install the program. this is by far the longest phase of the compilation process and can range from seconds (for small programs) to hours (for bigger ones)..   (the kde-base meta-package will probably take 8-12 hours on most hardware...)   ;)

for more info, look to compile-based linux-distros such as gentoo, [www.gentoo.org](www.gentoo.org) or LFS, [www.linuxfromscratch.org](www.linuxfromscratch.org) 

compilation is always good to know, as not all programs might be readily available as a binary for the system you are using (or, at least, the latest "cutting edge" software might not be, in the case of ubuntu)..

Good luck!!

---

### Post by bukwirm on 2007-06-12
On Ubuntu, you need to install the *build-essential* package to compile stuff.

---

### Post by chili555 on 2007-06-12
...as well as linux-headers

---

### Post by bukwirm on 2007-06-12
You only need the linux-headers if you want to compile kernel modules, I believe.

---

### Post by Keisad on 2007-06-15
Disclaimer : I'm a total n00b.

Ok, so I'm having some problems. Specifically, a media program called "aqualung" which requires me to download and compile it, but I have no idea what to do. I unpackage the thing fine, but my progress seems to halt once I try to configure. I know the required file is there, but it won't let me do anything with it. So,

1. Help?

2. Suggestions for other playback programs that let me keep a library, and have multiple music format support (ogg, mp3, wma etc.) that are already compiled.

Thanks,

"rips hair out"

---

### Post by chili555 on 2007-06-15
I just downloaded, configured and made the program. The only unusual things I have installed are *build-essential* and *linux-headers.* Even though the INSTALL file says 'configure,' the actual command is ```
./configure
```Please try ./configure followed by make followed by sudo make install.

Let us know where you get stuck.

---

