---
title: "Intalling scheme got error - a newbie"
date: 2014-01-17
forum: General Help
---

### Post by adityakarki on 2014-01-17
I'm new to linux as well as scheme. I tried to install "mit scheme" on my ubuntu 12.04 LTS - 64 bit OS, but got an error and then tried the answers at this thread "**[ MIT-Scheme does not work, compiled but won't install"]("http://ubuntuforums.org/showthread.php?t=778034")**

I tried the installation through procedure given at this page ["http://www.gnu.org/software/mit-scheme/liarc-build.html"]("http://&quot;http://www.gnu.org/software/mit-scheme/liarc-build.html&quot;")  and after doing these


[LIST=1]
[*]Download the portable C source package [mit-scheme-c-9.1.1.tar.gz]("http://ftp.gnu.org/gnu/mit-scheme/stable.pkg/9.1.1/mit-scheme-c-9.1.1.tar.gz").
[*]Unpack the source package:tar xzf mit-scheme-c-9.1.1.tar.gz
cd mit-scheme-c-9.1.1/src
[*]Build the package:etc/make-liarc.sh
[/LIST]

there was no problem until here but 

[COLOR=#35382A][FONT=sans-serif]4. Install the program:[/FONT][/COLOR]make install 

while doing this step i got error msg:

/bin/bash ./microcode/mkinstalldirs /usr/local/lib/mit-scheme-c
mkdir /usr/local/lib/mit-scheme-c
mkdir: cannot create directory `/usr/local/lib/mit-scheme-c': Permission denied
make: *** [install-auxdir-top] Error 1

I ran this as mentioned in one of the thread : sudo sysctl -w vm.mmap_min_addr=0 
but still it gives the same error message. 

(if any solution can you provide me it in detail as I am new to Linux and scheme )

---

### Post by steeldriver on 2014-01-17
Hello and welcome to the forums

Version 9.1-1 of mit-scheme is available from the 12.04 repository - there should be no need to compile it

```

$ apt-cache policy mit-scheme
mit-scheme:
  Installed: (none)
  Candidate: 9.1-1
  Version table:
     9.1-1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages

```

If you still think you need to install it from source then the error is because **make install **needs to write to the /usr/local/lib directory - which is owned by root. You would need to run **sudo make install**.

---

### Post by adityakarki on 2014-01-17
So that means it is already in my system? As I said earlier I'm new to linux and scheme. How can I install it and run it. It would be very helpful.

---

### Post by steeldriver on 2014-01-17
You should be able to search for / install it via the Ubuntu Software Center (or other package manager such as synaptic), or you can install it from the command line using apt-get

```

sudo apt-get update

sudo apt-get install mit-scheme

```

---

### Post by adityakarki on 2014-01-17
I did 

sudo apt-get install mit-scheme

and it gave this error:


The following packages have unmet dependencies:
 mit-scheme:i386 : Depends: libmhash2:i386 but it is not going to be installed
                   Recommends: mime-support:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by steeldriver on 2014-01-17
My apologies, it appears that mit-scheme cannot be installed from the repository on a 64-bit system --> [https://bugs.launchpad.net/ubuntu/+source/mit-scheme/+bug/373018](https://bugs.launchpad.net/ubuntu/+source/mit-scheme/+bug/373018)

It looks like installation of mit-scheme-c from source (like you originally tried) is the recommended method - so I suggest you try it again but using 'sudo' for the final 'make install' command

---

### Post by adityakarki on 2014-01-17
Thank you. The sudo make instal worked fine :)

---

### Post by dkinzer on 2014-05-23
I was having a similar issue, and I noticed that I could compile on travis-ci.org but not locally.  I was building on a basic travis-ci machine which uses Ubuntu 12.04LTS; which uses the following build toolchain:

**Compilers & Build toolchain [#]("http://docs.travis-ci.com/user/ci-environment/#Compilers-%26-Build-toolchain")**

[COLOR=#595959][FONT=Source Sans Pro]GCC 4.6.x, Clang 3.2.x, make, autotools, cmake, scons.

[/FONT][/COLOR]I was missing cmake and clang. Once I installed those via apt-get I was able to compile the src without issues.

---

