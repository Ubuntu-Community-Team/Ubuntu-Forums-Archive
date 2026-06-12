---
title: "swi-prolog Java interface (JPL)"
date: 2007-05-18
forum: General Help
---

### Post by leonidas666 on 2007-05-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/swi-prolog/+bug/90031](https://bugs.launchpad.net/ubuntu/+source/swi-prolog/+bug/90031) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, 

I would like to install swi-prolog with the jpl extension. So far i encountered the following problems:
- even though  jpl is a standard package of swipl as per the swi-prolog homepage, it does not seem to be included in the swipl-package in synaptic. There are some extra pacjkages for some swipl extensions like swi-prolog-xpce, but there is no ubuntu-package for jpl. Also, somebody filed a bug asking for  jpl to be included:
[https://bugs.launchpad.net/ubuntu/+source/swi-prolog/+bug/90031](https://bugs.launchpad.net/ubuntu/+source/swi-prolog/+bug/90031)
so i guess it is really not there. 
- The xpce package does not seem to work: Jan Wielemaker wrote me this in an email:
> Ubuntu has made a packaging error by renaming swi-prolog that makes it
impossible to find the XPCE graphics system. Go to /usr/lib/pl-<version>
and rename pl.rc to swipl.rc (if I recall properly SWI-Prolog is called
swipl on Ubuntu). 
. xpce is not really my concern tright now, it's just that it would be useful to get info about the installed packages.
- Since the ready-made ubuntu package didn't work, i tried installing from source. Compiling swipl itself was not so difficult, but getting the packages to compile required installing a load of libXYZ-dev packages. But ultimately i didn't get jpl to work. The readme file says something about a required dll, i guess i can skip this part...I have the feeling the Readme is for the windows version. Maybe i did not put jpl.jar in the right place, i tried putting it in the same directory as one of the example programs, i fiddled around with the --classpath option but in the end i always got the error message that the java interpreter could not find the jpl package (which is sitting in the jpl.jar, i suppose).

So is anybody using swi-prolog and jpl on ubuntu? How did you install it? Was it as painful as my experience...?

---

### Post by leonidas666 on 2007-05-18
So i got it finally to work...

The main clues:
- The equivalent of jpl.dll under linux is libjpl.so. To add confusion, there is also one file jpl.o created during compiling, and the java-interpreter is only complaining that it cannot find the library "jpl" (so that when one is looking for some file named "jpl" one will find jpl.o, and not libjpl.so. Needless to say, it does NOT work with jpl.o). Also finding the directory where to put this libjpl.so was not so easy, i wrote myself a small java-program which outputs the contents of the java.library.path property...some quite obscure paths. In my case, i used
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client

- I got fed up with the jpl.jar and the classpath problems, so i just unpacked the jar (it's just a zip-file) and put it in the folder together with the other java-files.

- In some Readme file there was also a command to be invoked in prolog so that prolog could find the necessary jpl prolog modules. Somehow i am not able to locate this readme file now...

---

### Post by iperez on 2008-01-02
Didn't work form me :(

I'm recompiling swi-prolog to see if it works.

---

### Post by jyrinx on 2008-01-19
Did you ever get it to work, iperez? I'd love to get this running ...

---

### Post by nickmeet on 2008-05-14
The following steps work on my ubuntu 8.04 :

wget [http://gollem.science.uva.nl/cgi-bin/nph-download/SWI-Prolog/binaries/pl-5.6.54-319.i586.rpm](http://gollem.science.uva.nl/cgi-bin/nph-download/SWI-Prolog/binaries/pl-5.6.54-319.i586.rpm)
sudo apt-get install alien
sudo alien -d pl-5.6.54-319.i586.rpm
sudo apt-get install swi-prolog			# to get dependencies
sudo apt-get remove swi-prolog			# do not sudo apt-get auto-remove before the next command takes place
sudo dpkg -i pl_5.6.54-319_i386.deb		# the package is named pl

open netbeans -> file -> new project -> java -> give name -> right click -> properties -> run
-> VM options -> -Djava.library.path="/usr/lib/pl-5.6.54/lib/i386-linux"

The dynamic library is /usr/lib/pl-5.6.54/lib/i386-linux/libjpl.so
The file that you have to import in your project is /usr/lib/pl-5.6.54/lib/jpl.jar
Although, I didn't use the location of the prolog file for the JPL package of swi-prolog, it is /usr/lib/pl-5.6.54/library/jpl.pl

---

### Post by oguillaume on 2008-07-24
JPL 1.0.1 **Don't make the same mistake : **
I got my sources from sourceforge BUT this is an OLD version of JPL (1.0.1). Still it works : I successfully compiled it under Ubuntu 8.04. 

**Rather get the sources from SWI-Prolog repository** at [URL="ftp://gollem.science.uva.nl/SWI-Prolog/[/URL]. From there you can extract JPL under the package folder. Ubuntu users, the current Prolog version in the repository is pl-5.6.47 and doesn't have the packages hence packages/jpl directory.

---

The procedure I used to compile JPL 1.0.1
[LIST=1]
[*] I first obtained the jpl-1.0.1.tar.gz from SourceForge :[http://sourceforge.net/project/showfiles.php?group_id=8899]("http://sourceforge.net/project/showfiles.php?group_id=8899") and then tar xzvf jpl-1.0.1.tar.gz
[*]Secondly, install Ubuntu prerequisites (compilers, libraries) ```
sudo apt-get install swi-prolog swi-prolog-* build-essential  libreadline5-dev sun-java6-bin
``` should do the trick
[*] Thirdly, changes to ```
rules.mk
``` (a) ```
JAVA_HOME = /usr/lib/jvm/java-6-sun
``` (b) ```
PL_HOME = /usr/lib/swi-prolog
``` (c) ```
PLATFORM_LIB = i386
``` (d) line 104 should read ```
CIFLAGS=-I. -I$(SRCROOTPATH)/include -I$(PL_HOME)/include -I$(JAVA_HOME)/include -I$(JAVA_HOME)/include/$(PLATFORM_INCLUDE)
``` (e) line 110 should read : ```
LDLIBS = -L$(PL_HOME)/lib/$(PLATFORM_LIB) -lpl -ldl -lreadline -ltermcap -lm
```
[*] ```
make
``` and hope for the best. Normally it should give you ```
 ls -r lib
libjpl.so  jpl.zip  jpl.jar  classes
```
[*] then copied lib/libjpl.jar files in current working directory along my java project and the libjpl.so to /usr/lib/jvm/java-6-sun/jre/lib/i386
[/LIST]

Note : Under Ubuntu, SWI-Prolog is installed under ```
/usr/lib/swi-prolog/
```, NOT under /usr/lib/pl-5.6.47/ and the include folder is directly under the root (not under /usr/lib/pl-5.6.47/lib/include/5.6.47 ).

---

### Post by oguillaume on 2008-07-24
I got Java programs to work with JPL 3.0.3 and it should even work with the previous version.

Only needed to ```
sudo apt-get install libgmp3-dev
``` to pass the ./configure and then compile.

Then copy the compiled files:
[LIST]
[*]libjpl.so to /usr/lib/swi-prolog/bin/i386
[*]jpl.jar to/usr/lib/swi-prolog/bin/i386
[*]jpl.pl to /usr/lib/swi-prolog/library
[/LIST]

Go into examples/java/Test
```

java -Djava.library.path=/usr/lib/swi-prolog/lib/i386/ -cp ./:../../../jpl.jar Test

```

Note:
If you are having an Exception like the following one :
```

Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjpl.so: /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjpl.so: undefined symbol: __gmpz_init

```
then that's because you need to use java -Djava.library.path=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/ for example to precise the **java.library.path**.
Also it's best to leave the JPL libraries in SWI-Prolog rather than in the Java folders (to find further dependencies like libpl.a)

success

---

