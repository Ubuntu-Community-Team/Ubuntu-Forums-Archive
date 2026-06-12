---
title: "Problem Compile Brasero 3.11.0"
date: 2014-10-03
forum: General Help
---

### Post by michael210 on 2014-10-03
Hallo everyone.

I'm trying to compile Brasero (3.11.0) in my Home Folder and i cannot understand what i'm doing wrong here.
I have Ubuntu 14.04.1 64BIT.
i will explain the staps i tryed.
1
```

mkdir -p $HOME/User-Install/Sources 
mkdir -p $HOME/User-Install/usr/bin
mkdir -p $HOME/User-Install/usr/lib
mkdir -p $HOME/User-Install/usr/include

```
2
```

cd $HOME/User-Install/Sources

```
3
```

wget https://download.gnome.org/sources/brasero/3.11/brasero-3.11.0.tar.xz

```
4
```

tar -xJvf brasero-3.11.0.tar.xz

```
5
```

cd brasero-3.11.0/

```
6
```

export PATH=$PATH:$HOME/User-Install/usr/bin
export LD_LIBRARY_PATH=$HOME/User-Install/usr/lib
export PKG_CONFIG_PATH=$HOME/User-Install/usr/lib/pkgconfig 

```
7
```

./configure --prefix=$HOME/User-Install/usr

```
8
```

make -j2

```
9
```

make install

```
.
Well, everithing is ok with CONFIGURE und MAKE but when i type make install, i get this:
> 
----------------------------------------------------------------------
 /bin/mkdir -p '/usr/share/gir-1.0'
 /usr/bin/install -c -m 644 BraseroMedia-3.1.gir '/usr/share/gir-1.0'
** /usr/bin/install: cannot create regular file &#8216;/usr/share/gir-1.0/BraseroMedia-3.1.gir&#8217;: Permission denied**
make[2]: *** [install-girDATA] Error 1
make[2]: Leaving directory `/home/michi/User-Install/Sources/brasero-3.11.0/libbrasero-media'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/michi/User-Install/Sources/brasero-3.11.0/libbrasero-media'
make: *** [install-recursive] Error 1

.
.
Here are the all Results of CONFIGURE, MAKE, MAKE INSTALL and configure.log:
[CONFIGURE]("http://pastebin.com/raw.php?i=4uQgnPv2")
[MAKE]("http://pastebin.com/raw.php?i=5QN9eahx")
[MAKE INSTALL]("http://pastebin.com/raw.php?i=aHz2yr61")
[CONFIGURE.LOG]("http://pastebin.com/raw.php?i=znCqQzgL")
.
Thank you all.

---

### Post by steeldriver on 2014-10-03
I suspect you're not doing anything wrong, it looks like a glitch in the configure script that's causing your --prefix specification not to get passed down to the install command for the BraseroMedia-3.1.gir file - you may need to go into the generated Makefile and edit the path (or modify the configure script)

I guess it's *possible* that it's falling back to /usr/share for  the gir-1.0 components because you didn't explicitly create a share  subdirectory in your local tree

```

mkdir -p $HOME/User-Install/usr/share

```
(but really it should be smart enough to create the subdirs)

There is also a --datarootdir=DIR parameter that is supposed to default to PREFIX/share but I guess you could try setting that explicitly as well

```

./configure --prefix=$HOME/User-Install/usr --datarootdir=$HOME/User-Install/share

```

I'd probably try those 2 things before hacking into the Makefile / configure script.

---

### Post by michael210 on 2014-10-04
> **steeldriver said:**
> 

```

mkdir -p $HOME/User-Install/usr/share

```
```

./configure --prefix=$HOME/User-Install/usr --datarootdir=$HOME/User-Install/share

```
This two made no differents, hacking configure script or MakeFile its not an option for me, thank you for your help.
.
I partialy fixed with:
```
ln -s $HOME/User-Install/Sources/brasero-3.11.0/src/brasero $HOME/User-Install/usr/bin/
```
Of course its not a FIX here, but until i get another solution i will work with this.
If someone has time to try installing brasero form source code (in HOME FOLDER), please share it.
Thank you all.

---

### Post by Bucky Ball on 2014-10-04
Any reason you didn't simply install from the Software Centre or there is some reason you want the most recent?

---

### Post by michael210 on 2014-10-04
The only things which are going inside my box are through repositories (apt-get).
Other Things goes inside $HOME/User-Install, i do this like 8 years now,
I never add a PPA, i never install .deb (i use dpkg-deb -x) files and ai never install compiled sources others than &HOME/User-Install.
I am a happy guy with no System Crashes at all.

In this category goes all my curiosity of trying new apps before goes to repository.
Also here i can check bugfixes and another stuffs.
.
So the all questions here are not why i'm doing this....
I have that problem and i need a fix, that's all.
Thank you

---

### Post by Bucky Ball on 2014-10-04
> **michael210 said:**
> 
.
So the all questions here are not why i'm doing this....
I have that problem and i need a fix, that's all.
Thank you

Cool. Message received and understood. Perhaps, if you have the disk space for a new partition to install 14.10 development version, try that. It will probably have the Brasero you are after available in the repos. If not now, fairly soon. It may still show 14.04 when you install the dev release, but that will change shortly. Any probs with that, post in 'Ubuntu +1' sub-forum. ;)

---

### Post by michael210 on 2014-10-09
hi again,
well i think the Brasero TEAM never intended to let you install their app other then as ROOT.
Of course you can hack Makefile file.
I just tryed this time Brasero-3.10 to compile and i got the same results:
> 
 /bin/mkdir -p '/usr/share/gir-1.0'
 /usr/bin/install -c -m 644 BraseroMedia-3.1.gir '/usr/share/gir-1.0'
/usr/bin/install: cannot create regular file &#8216;/usr/share/gir-1.0/BraseroMedia-3.1.gir&#8217;: Permission denied
make[2]: *** [install-girDATA] Error 1
make[2]: Leaving directory `/home/michi/User-Install/Sources/brasero-3.10.0/libbrasero-media'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/michi/User-Install/Sources/brasero-3.10.0/libbrasero-media'
make: *** [install-recursive] Error 1

At least i can build it and link the executables to my User-Install Folder.
If someone finds out that it is possible to install Brasero in $HOME, please let us know.
.
.
L.E:
I just repleaced
```
make install
```
with
```
sudo make install
```
because i had to check if "make install" works, and brasero installed succesfuly inside $HOME/User-Install, and of course belongs to ROOT :))
Thank You All.

---

