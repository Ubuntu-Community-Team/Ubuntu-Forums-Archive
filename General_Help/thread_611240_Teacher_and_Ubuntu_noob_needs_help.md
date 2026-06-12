---
title: "Teacher and Ubuntu noob needs help"
date: 2007-11-12
forum: General Help
---

### Post by nMantas on 2007-11-12
Just to clean up my goal here.  I'm a teacher and want to use this software in my forensics class:

[http://prdownload.berlios.de/dpfp/dpfp-driver-0.1.2.tar.bz2](http://prdownload.berlios.de/dpfp/dpfp-driver-0.1.2.tar.bz2)

I'm getting an error while compiling about LIBUSB not being present.......LIBUSB from synaptic doesn't do any good(unless I have to change settings or something).

---

### Post by 1337455 10534 on 2007-11-12
> 
Seems like I just need to know how to compile and use his driver and firmware cutter.

Well I have no idea what you are really talking about, but compiling on Ubuntu is simple;
(open a terminal; "#"'s mean omit, and i use them to signify an example, each line is a separate command)
```

cd [enter in the file path of your source directory]
# cd /home/family/Desktop/foresenics_source
./configure
make
sudo make install

```
during the ./configure, if it displays an error message, install the missing packages it may direct you to..
It also alway helps to read the Install.txt in the source..

---

### Post by nMantas on 2007-11-13
ok thanks for the reply

I got an email from the author and he said all I have to do is compile the library and I'm set "just as you said".  Unfortunately the compiling hits an error and near the end and the make operation has no chance:


nicholas@HP:~$ cd /home/nicholas/Desktop/libdpfp
nicholas@HP:~/Desktop/libdpfp$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
nicholas@HP:~/Desktop/libdpfp$ make
make: *** No targets specified and no makefile found.  Stop.
nicholas@HP:~/Desktop/libdpfp$

---

### Post by 1337455 10534 on 2007-11-13
yikes!
try this:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gawk

```
"checking for C compiler default output file name... configure: error: C compiler cannot create executables"
You have a broken compiler...
Try searching Synaptic for "g++"..

---

### Post by nMantas on 2007-11-14
I REALLY appreciate the help.  The g++ did the trick BUT I hit a new error.  There is a massive list of checking and compiling.....but when I hit libusb I error out.  I entered libusb in synaptic and it says I already have libusb 0.1-4.  I just copy/pasted a little of the bottom where the ./configure errors out



checking for LIBUSB... configure: error: Package requirements ("libusb") were not met:

No package 'libusb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBUSB_CFLAGS
and LIBUSB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

nicholas@HP:~/Desktop/libdpfp$ make
make: *** No targets specified and no makefile found.  Stop.
nicholas@HP:~/Desktop/libdpfp$

---

### Post by 1337455 10534 on 2007-11-14
Ahh!
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Find your library in the package search and try getting it from there...

---

### Post by bodhi.zazen on 2007-11-14
If you want to compile, install build essential :

```
sudo apt-get install build-essential
```

---

### Post by nMantas on 2007-11-14
I cleaned up the original post just so everyone is clear on what I want to do.

I feel I'm so close yet so stuck.  I still can't get past the libusb error on the compiling even though it seems I should have it installed.  I wonder if the libusb I'm supposed to use is this older version: [http://libusb.sourceforge.net/download.html#stable](http://libusb.sourceforge.net/download.html#stable) which I also get a compiling error while trying to install.,.. go figure.  I still get the libusb error on the fingerprint softwarecompiling and I get this error from the older libusb compiling that I'm trying to install:


nicholas@HP:~$ cd /home/nicholas/Desktop/libusb
nicholas@HP:~/Desktop/libusb$ ./compile
./compile: No command.  Try `./compile --help' for more information.
nicholas@HP:~/Desktop/libusb$ ./compile --help
Usage: compile [--help] [--version] PROGRAM [ARGS]

Wrapper for compilers which do not understand `-c -o'.
Remove `-o dest.o' from ARGS, run PROGRAM with the remaining
arguments, and rename the output as expected.

If you are trying to build a whole package this is not the
right script to run: please start by reading the file `INSTALL'.

Report bugs to <bug-automake@gnu.org>.

---

### Post by 1337455 10534 on 2007-11-15
nMantas
*THREE IMPORTANT THINGS:*
1) What version of Ubuntu do you run? 6.06(Dapper)? 7.04(Feisty)? 7.10 (Gutsy)? 
1a) Are you trying this on an Apple computer? Are you trying this on a 64 bit comp? Or Is this an x86 computer? If you're not sure, go for x86. 
2) You **must** go to [http://packages.ubuntu.com/gutsy/libs/](http://packages.ubuntu.com/gutsy/libs/) (if you are on Gutsy. otherwise, I will give you a link to the correct version.)
3) In this package list, there are 2 libusb libs: libusb++-0.1-4c2 (2:0.1.12-7), and libusb-0.1-4 (2:0.1.12-7). Pick the one you need and I will give you a better link.

To clarify, the "./" prefix means "run"...
If there is no file named "compile" in that directory, nothing will happen, because what you have instructed to work... Does not exist...

P.S: Hope your class goes well! :)

EDIT>>> The ReadME:
DPFP LINUX DRIVER README
[http://dpfp.berlios.de](http://dpfp.berlios.de)

NOTE
This is ALPHA software. [B]It is incomplete, not very clean, and may have
bugs.[/B] Bug reports are welcome (write to our mailing list) but please don't
expect things to work at this stage, and please don't expect them to be fixed
quickly. I'm a busy person.
At this stage, the driver isn't intended for general usage. If you don't
understand the instructions in this file, you should wait a few weeks until
we are at a later stage in development.

REQUIREMENTS
Linux 2.6.16-rc6 with USB support (older/newer may work too)
[B]libdpfp and dpfp-firmware-cutter (separate downloads)
Device firmware in your hotplug firmware directory[/B]

USAGE
Compile this driver using the provided Makefile.
Extract the firmware using the dpfp-firmware-cutter script.
Place the extracted firmware in your hotplug firmware directory (usually
/lib/firmware).
Load the dpfp.ko driver using insmod.

In order to actually obtain fingerprints, you need to use a program based on
libdpfp. libdpfp comes with an example application to scan a fingerprint into
a PGM image file.

Actual fingerprint recognition must be done through external software.

---

### Post by 1337455 10534 on 2007-11-15
Please try:
```

sudo apt-get install build-essential libusb-0.1-4 libc6 libusb++-0.1-4c2 libgcc1 gcc-4.2-base libstdc++6 module-init-tools udev

```
**It's all one line, copy and paste into the terminal!!**
If that failed, do a package search for them!
Now, 
```

cd [enter in the file path of your source directory]
# cd /home/family/Desktop/foresenics_source
./configure
make
sudo make install

```

Working? I'm pessimistic (sorry, but, I tried).

---

### Post by nMantas on 2007-11-19
Thanks for all the help.  I never could get it but the new Griaule windows software gives you a 90 day limitless trial.  They used to have their ads across the images in trial mode but now they are ad-less.
  
So I'm good to go and am doing the lab tomorrow with the kids.

Thanks again.


> **1337455 10534 said:**
> Please try:
```

sudo apt-get install build-essential libusb-0.1-4 libc6 libusb++-0.1-4c2 libgcc1 gcc-4.2-base libstdc++6 module-init-tools udev

```
**It's all one line, copy and paste into the terminal!!**
If that failed, do a package search for them!
Now, 
```

cd [enter in the file path of your source directory]
# cd /home/family/Desktop/foresenics_source
./configure
make
sudo make install

```

Working? I'm pessimistic (sorry, but, I tried).

---

### Post by CatKiller on 2007-11-19
Often when you are compiling your own software, you need the -dev versions of the dependencies. There are libusb-dev and libusb++-dev that might have the files that you need.

---

### Post by jespdj on 2007-11-20
> **1337455 10534 said:**
> 
To clarify, the "./" prefix means "run"...

No, it doesn't. "." means "the current directory" and "/" is just the path separator. If you type "./configure" it means: look for a script named "configure" in the current directory.

---

### Post by 1337455 10534 on 2007-11-20
I'm sorry, I assumed this because;
```

family@Purple-Blanket:~$ cd /home/family/Desktop
family@Purple-Blanket:~/Desktop$ ./Ubuntu_Utilities
family@Purple-Blanket:~/Desktop$ ./Ubuntu_Utilities.py
Ubuntu Utilities: FOSS by 1337455 10534 of Ubuntu Forums
Designed to be useful... Contact at vminch@gmail.com.

1: Secure File & Directory Shredding
2: md5sum Checking
3: Update & Upgrade
4: Autoclean
#------------------
0: Quit
Choose [1,2,3,4 or 0] and press Enter:

```
so I assumed that it meant "run".

Unfortunately; 
```

./thunderbird

```
does nothing so you are correct.
Oops.

---

### Post by geirha on 2007-11-20
Typing anything in the bash shell means "run", unless it's identified as a builtin command like "if", "then", "while", "do", etc., and if it is immediately followed by = then it's a variable assignment and so forth.

If you type a command with no prefix, like "configure" it will search all directories in the $PATH variable and run the first hit, or give you an error of no such file or directory.

if you specify a path in front of the command, the command will be looked for only in that path, and "./" is of course the current directory.

---

