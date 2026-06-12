---
title: "Compiling C programs using gcc"
date: 2007-04-13
forum: General Help
---

### Post by stchman on 2007-04-13
Hello all, I was recently trying to compile a few C and C++ programs.  I use Visual C++ here at work and wanted to take them home on a USB key and work on them over a weekend.

I figured that since Ubuntu has gcc and gedit (syntax highlighting) that I was golden.  Well I got home and opened up the program listing.  I made a few changes and then typed this in the command line:

gcc -o ./program ./program.c -lm

Well, the darn thing would not compile.  gcc was telling me there was no <stdio.h> library.  I was frustrated to say the least.  gcc is an integral part of Linux.  I did a little bit of web surfing and it turns out that you need to install the following:

sudo apt-get install build-essential

Once I did that the C program would compile and run.  I was then very happy.

My question is what person thought that that should not be installed by default?  A lot of programs and drivers are built using the make command which then compiles C programs.  That and:

sudo apt-get install nautilus-open-terminal

is another example of something that needs to be installed by default.

just my rant.

Does anyone know if Ubuntu has a free C/C++ debugger through apt-get?

Thanks

---

### Post by rai4shu2 on 2007-04-13
There were some security concerns over default install of gcc, plus it isn't really "noob" friendly to have to compile drivers and such.

I think there is gdb and various gdb-like programs you can get for debugging.

---

### Post by stchman on 2007-04-13
> **rai4shu2 said:**
> There were some security concerns over default install of gcc, plus it isn't really "noob" friendly to have to compile drivers and such.

I think there is gdb and various gdb-like programs you can get for debugging.

I understand that n00bs don't want to compile drivers.  What of the folks that want to write programs?  Unless you sudo I don't see the security concern.

---

### Post by Maestro23 on 2007-04-13
Linux App Finder: [http://linuxappfinder.com/development/compilers](http://linuxappfinder.com/development/compilers)

---

### Post by rai4shu2 on 2007-04-13
I think there was concerns of potential problems that ordinary users might run into. I don't really see it, but that's how I remember it last I checked on that.

If you're into writing programs, I think you've progressed far beyond that particular concern.

---

### Post by DoubleQuadword on 2007-04-13
> **stchman said:**
> My question is what person thought that that should not be installed by default?  A lot of programs and drivers are built using the make command which then compiles C programs.

That's true, and in fact, I absolutely agree with you. I think that some packages like 'build-essential' should be installed along with the OS.

> **rai4shu2 said:**
> There were some security concerns over default install of gcc, plus it isn't really "noob" friendly to have to compile drivers and such.

I don't think so. Despite that, if you analyze the situation you might see that newbies rarely interact *directly* with **gcc**. That's because most programs follow the 'standard' install sequence: "Run configure, then make (or make install).", so knowing how to do that it's, indeed, quite enough for installing a program.

Regards.

---

### Post by stchman on 2007-04-14
> **DoubleQuadword said:**
> That's true, and in fact, I absolutely agree with you. I think that some packages like 'build-essential' should be installed along with the OS.



I don't think so. Despite that, if you analyze the situation you might see that newbies rarely interact *directly* with **gcc**. That's because most programs follow the 'standard' install sequence: "Run configure, then make (or make install).", so knowing how to do that it's, indeed, quite enough for installing a program.

Regards.

Exacty.  N00bs might not even know what gcc is.  Unless you surf the net on a root account then you should be safe.  Also ther are nearly zero viruses, malware, spyware for Linux.

---

