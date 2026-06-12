---
title: "No such file or directory?  Really?"
date: 2016-09-22
forum: General Help
---

### Post by john_ladasky on 2016-09-22
You know the old saying, a picture is worth two kilobytes...

[ATTACH=CONFIG]271305[/ATTACH]

Why am I unable to execute arm-none-eabi-gcc (the highlighted file)?  I have carefully checked the spelling of the path and file name, and they match.  My user account does not own the file, root does.  But my user account does have read permissions, and the "allow execution" box is checked.  I don't ever remember needing to own a file in order to run it. 

I had this same executable set up correctly once before under Ubuntu 15.04. I may have skipped a step on my new 16.04 installation.

Any advice is appreciated, thanks!

---

### Post by &amp;KyT$0P# on 2016-09-22
I have seen this when trying to run 32-bit executables on a 64-bit system that didn't have 32-bit libraries installed.  Use [FONT=Courier New]file[/FONT] on it to check whether this is what is happening to you.

---

### Post by john_ladasky on 2016-09-22
Thanks for your reply, halogen2.  You're right, the program appears to be a 32-bit executable:

```
john@xxx:~$ file /usr/local/gcc-arm-none-eabi-4_9-2015q1/bin/arm-none-eabi-gcc
/usr/local/gcc-arm-none-eabi-4_9-2015q1/bin/arm-none-eabi-gcc: ELF 32-bit LSB executable,
Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for
GNU/Linux 2.6.8, stripped

```

The repository for the particular version of GCC ARM Embedded that I'm using is [here]("https://launchpad.net/gcc-arm-embedded/4.9/4.9-2015-q1-update").  The page states that both Linux 32-bit and 64-bit are supported. As I said, I had this executable working on Ubuntu 15.04 and I'm having trouble getting it to work now on 16.04.  It may be that some files that were bundled in the 15.04 distro are no longer included?  I will investigate.

---

### Post by &amp;KyT$0P# on 2016-09-22
This from their readme -
> * Installing executables on Linux *
Unpack the tarball to the install directory, like this:
$ cd $install_dir && tar xjf gcc-arm-none-eabi-*-yyyymmdd-linux.tar.bz2

For 64 bit system, 32 bit libc and libncurses are required to run the tools.
In addition, if you want to use gdb python build (arm-none-eabi-gdb-py), you'd
install 32 bit python2.7. Please refer to
[https://answers.launchpad.net/gcc-arm-embedded/+faq/2601](https://answers.launchpad.net/gcc-arm-embedded/+faq/2601) 

For some Ubuntu releases, the toolchain can also be installed via
Launchpad PPA at [https://launchpad.net/~terry.guo/+archive/gcc-arm-embedded](https://launchpad.net/~terry.guo/+archive/gcc-arm-embedded).

So, you can either install 32-bit libraries, or download the source and try to build a 64-bit version yourself.

---

### Post by john_ladasky on 2016-09-22
Yes, I just found [this link]("https://answers.launchpad.net/gcc-arm-embedded/+question/355434") which says essentially the same thing.

---

### Post by john_ladasky on 2016-09-22
From my Synaptic history:
```
Installed the following packages:
lib32ncurses5 (6.0+20160213-1ubuntu1)
lib32tinfo5 (6.0+20160213-1ubuntu1)
libc6-i386 (2.23-0ubuntu3)
```

I selected **lib32ncurses5** and **libc6-i386** for installation, **lib32tinfo5** was a dependency identified by Synaptic.

And... it works!

Thank you, halogen2, for spotting the fact that this was a 32-bit vs. 64-bit issue.  I don't know whether future revisions of Linux can be coaxed into telling us that more explicitly.  A "no such file" error was baffling.

---

### Post by &amp;KyT$0P# on 2016-09-22
You're welcome!  :KS

---

