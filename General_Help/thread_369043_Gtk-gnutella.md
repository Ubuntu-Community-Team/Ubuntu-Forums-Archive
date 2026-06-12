---
title: "Gtk-gnutella"
date: 2007-02-24
forum: General Help
---

### Post by icehammer on 2007-02-24
I wish to install the latest version of gtk-gbutella.. So i downloaded the platform independent .tar.gz file from the site, so that i could compile it on my own. i extracted it, and in the terminal typed:

```
configure
```

and i got:
PS : I chose default options for every question.

```
icehammer@icehammer:~/Desktop/gtk-gnutella-0.96.3$ ./Configure
 
Beginning of configuration questions for gtk-gnutella.
 
Checking echo to see how to suppress newlines...
...using \c
The star should be here-->*
 
First let's make sure your kit is complete.  Checking...
Looks good...
 
We'll use '
' to transliterate a newline.
 
Would you like to see the instructions? [n] 
 
Locating common programs...
awk is in /usr/bin/awk.
cat is in /bin/cat.
chgrp is in /bin/chgrp.
chmod is in /bin/chmod.
chown is in /bin/chown.
cp is in /bin/cp.
echo is in /bin/echo.
expr is in /usr/bin/expr.
grep is in /bin/grep.
make is in /usr/bin/make.
mkdir is in /bin/mkdir.
mv is in /bin/mv.
rm is in /bin/rm.
sed is in /bin/sed.
sort is in /usr/bin/sort.
touch is in /usr/bin/touch.
tr is in /usr/bin/tr.
uniq is in /usr/bin/uniq.
 
Don't worry if any of the following aren't found...
ar is in /usr/bin/ar.
I don't see bison out there, offhand.
I don't see byacc out there, either.
cpp is in /usr/bin/cpp.
date is in /bin/date.
egrep is in /bin/egrep.
I don't see gmsgfmt out there, either.
ln is in /bin/ln.
msgfmt is in /usr/bin/msgfmt.
msgmerge is in /usr/bin/msgmerge.
nm is in /usr/bin/nm.
nroff is in /usr/bin/nroff.
test is in /usr/bin/test.
uname is in /bin/uname.
xgettext is in /usr/bin/xgettext.
Substituting msgfmt for gmsgfmt.
Using the test built into your sh.
 
Checking compatibility between /bin/echo and builtin echo (if any)...
They are not compatible!  You are probably running ksh on a non-USG system.
I'll have to use /bin/echo instead of the builtin, since Bourne shell doesn't
have echo built in and we may have to run some Bourne shell scripts.  That
means I'll have to use '-n' to suppress newlines now.  Life is ridiculous.

The star should be here-->*
 
Symbolic links are supported.
 
Checking how to test for symbolic links...
Your builtin 'test -h' may be broken.
Trying external '/usr/bin/test -h'.
You can test for symbolic links with '/usr/bin/test -h'.
 
Good, your tr supports [:lower:] and [:upper:] to convert case.
Using [:upper:] and [:lower:] to convert case.

Configure uses the operating system name and version to set some defaults.
The default value is probably right if the name rings a bell. Otherwise,
since spelling matters for me, either accept the default or answer "none"
to leave it blank.

Operating system name? [linux] 
 
Operating system version? [2.6.17-10-generic] 

I can compile gtk-gnutella for a so-called "official build".  That means
a build whose generated programs should not refer back to the place
where the sources for gtk-gnutella are located.  In other words, no
mention of the current source directory:

        /home/icehammer/Desktop/gtk-gnutella-0.96.3

should make its way into the generated scripts and programs.  Because
that would be useless, and to protect your privacy.

When compiling for local use, it usually makes sense to allow gtk-gnutella
to access your sources, in case you don't want to make a full install
and wish to rely on some configuration file or other data file present
in the sources.

Is this producing an official build [n] 

Gtk-gnutella can run without any GUI interface in so-called "headless" mode.
Therefore, monitoring of operations for gtk-gnutella will have to be done
without relying on any GUI, and the configuration is done via files only.

Run without any GUI interface [n] 

Gtk-gnutella has a raw remote control service.

Currently you can create searches, connect to nodes, and print and 
set the values of properties as well as read the 'tooltips'.  It is
not completely functional, but you may choose to enable it here at
compile time.  The feature will need activation from the GUI.

For more information, see doc/other/remote-shell.txt

Enable remote control service [y] 
 
I can compile for the GTK+ 1.x version or for the GTK+ 2.x version.
The GTK1 frontend will use much less CPU than the GTK2 one, so if you
have a slow CPU, you are encouraged to choose GTK1.

Use which GTK toolkit (1 or 2) [1] 
 
I can set things up so that your shell scripts and binaries are more portable,
at what may be a noticable cost in performance.  In particular, if you
ask to be portable, the following happens:

     1) Shell scripts will rely on the PATH variable rather than using
        the paths derived above.
     2) ~username interpretations will be done at run time rather than
        by Configure.

Do you expect to run these scripts and binaries on multiple machines? [n] 

By default, gtk-gnutella will be installed in /usr/local/bin, manual
pages under /usr/local/man, etc..., i.e. with /usr/local as prefix for
all installation directories. Typically set to /usr/local, but you
may choose /usr if you wish to install gtk-gnutella among your system
binaries. If you wish to have binaries under /bin but manual pages
under /usr/local/man, that's ok: you will be prompted separately
for each of the installation directories, the prefix being only used
to set the defaults.

Installation prefix to use? (~name ok) [/usr/local] 
 
AFS does not seem to be running...
 
Pathname where the public executables will reside? (~name ok)
[/usr/local/bin] 
 
System manual is in /usr/share/man/man1.

Gtk-gnutella has manual pages available in source form.
If you don't want the manual sources installed, answer 'none'.
 
Where do the manual pages (source) go? (~name ok) [/usr/share/man/man1] 

There are some auxiliary files for gtk-gnutella that need to be put into a
private library directory that is accessible by everyone.

Pathname where the private library files will reside? (~name ok)
[/usr/local/lib/gtk-gnutella] 
 
Hmm...  Looks kind of like a GNU/Linux system, but we'll see...
 
Congratulations.  You aren't running Eunice.
 
It's not Xenix...
 
Nor is it Venix...
 
Hmm...  Doesn't look like a MIPS system.

Some systems have incompatible or broken versions of libraries.  Among
the directories listed in the question below, please remove any you
know not to be holding relevant libraries, and add any that are needed.
Say "none" for none.

Directories to use for library searches? [/usr/local/lib /lib /usr/lib] 

On some systems, shared libraries may be available.  Answer 'none' if
you want to suppress searching of shared libraries for the remainder
of this configuration.

What is the file extension used for shared libraries? [so] 
 
Use which C compiler? [cc] 
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
Uh-oh, the C compiler 'cc' doesn't seem to be working.
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
Uh-oh, the C compiler 'cc' doesn't seem to be working.
You need to find a working C compiler.
Either (purchase and) install the C compiler supplied by your OS vendor,
or for a free C compiler try http://gcc.gnu.org/
I cannot continue any further, aborting.

```



i have gcc installed, it even shows the version num as:

```

icehammer@icehammer:~/Desktop/gtk-gnutella-0.96.3$ gcc -v

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

```


what to do??

---

### Post by chggr on 2007-02-24
Where it says: "Use which compiler:", I think you should type in gcc instead o cc.

---

### Post by icehammer on 2007-02-25
tried that, still no go...

---

### Post by EscapeCharacter on 2007-03-25
> 
I wish to install the latest version of gtk-gbutella.. So i downloaded the platform independent .tar.gz file from the site, so that i could compile it on my own. i extracted it, and in the terminal typed:

Code:

configure

and i got:
PS : I chose default options for every question.




You need to go to the top of your source tree and read the "README.Debian" file. 

It tells you how to compile the package to a .deb that you can install on your Ubuntu system.

Worked fine for me first time.

cheers

EC

---

### Post by dwfox2002 on 2007-03-25
Why compile it when you can get it from the repository? I ran

sudo aptitude install gtk-gnutella

in a terminal window and wala! Or is this not the latest version?
gtk-gnutella/0.96.3-12293 (2006-11-09; GTK2; Linux i686)

---

### Post by westli on 2007-03-25
The only version I have been able to get is 0.96.1, even using the exact command as above.  And it is described as "too ancient" and won't even run unless a force it via a change in the config file.

This is very strange.

---

### Post by Andrew Booth on 2007-06-09
> **dwfox2002 said:**
> Why compile it when you can get it from the repository? I ran

sudo aptitude install gtk-gnutella

in a terminal window and wala! Or is this not the latest version?
gtk-gnutella/0.96.3-12293 (2006-11-09; GTK2; Linux i686)

I ran this on ubuntu 7.04 and it appears to have worked. Thankyou.

---

