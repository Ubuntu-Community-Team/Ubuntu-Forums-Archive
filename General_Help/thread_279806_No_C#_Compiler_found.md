---
title: "No C# Compiler found"
date: 2006-10-18
forum: General Help
---

### Post by stopsatgreen on 2006-10-18
Hi,

I'm trying to install a package, but when I run ./configure I get the message:

configure: error: No C# compiler found

I've installed build-essential, mono, gcc... everything I can think of. But still I get stuck here. Any suggestions?

I'm on Edgy, BTW.

---

### Post by taurus on 2006-10-18
Install it with

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by PriceChild on 2006-10-18
```
sudo apt-get install build-essential
```Will sort out your problems :)

---

### Post by dannyboy79 on 2006-10-18
a gogle search returned this, GCC - the GNU Compiler Collection includes C, C++, Java and Fortran. No C# 
compiller.
For C# compiler install mono project - 
------------------------------------------------------------------------------------------------
/usr/ports/lang/mono/pkg-descr reads:

An open source implementation of .NET Development Framework.

This is a development release leading to the next production milestone.

WWW: [http://www.mono-project.com/](http://www.mono-project.com/)

good luck

---

### Post by stopsatgreen on 2006-10-18
Sorry, I'm not sure I understood your reply. I have the GCC & Mono packages installed already.

---

### Post by taurus on 2006-10-18
And ./configure says that you don't have gcc on your machine!  What does this say at the prompt?

```
gcc -v
```

---

### Post by stopsatgreen on 2006-10-18
```
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
```

---

### Post by justin whitaker on 2006-10-18
The compiler for mono should be included, if not, you can get it here:

[http://www.mono-project.com/CSharp_Compiler#Obtaining_MCS](http://www.mono-project.com/CSharp_Compiler#Obtaining_MCS)

---

### Post by Totzo on 2006-10-18
which package are you trying to build? If a version of it is in the repositories you could try doing this, for example, if the package you are trying to build was gimp:

```
sudo apt-get build-dep gimp
```

then do the ./configure thing

---

### Post by stopsatgreen on 2006-10-18
I had mono-mcs installed, but needed mono-gmcs. Thanks.

I'm trying to build the latest version of Banshee; however, after hours of downloading packages, there seems to be an XML file missing which stops the build :(

---

### Post by Totzo on 2006-10-18
check this page out, maybe it will work if you follow the build from source instructions.

[http://banshee-project.org/Distributions/Ubuntu]("http://banshee-project.org/Distributions/Ubuntu")

---

### Post by wickerman1413 on 2007-12-10
Running the command
[INDENT]sudo apt-get install mono-gmcs[/INDENT]
resolved the problem for me.

I already had a working system that allowed me to build f-spot from the latest source, but I guess somewhere during the upgrade from Ubuntu 7.04 to 7.10 mono-gmcs was removed

---

### Post by BhRaviKiran on 2008-03-06
HI team,
                   Plz clarify this. I  have installed Ubuntu 6.06 Dapper drake on Intel machine. 

While trying to install mono as 
"sudo apt-get install mono-gmcs mono" I get the error
           "Couldn't find the package mono-gmcs". I have downloaded from the ubuntu site and burnt the iso image.

Any solutions.

Thanks & Regards,
Ravi Kiran.

---

### Post by taurus on 2008-03-06
> **BhRaviKiran said:**
> HI team,
                   Plz clarify this. I  have installed Ubuntu 6.06 Dapper drake on Intel machine. 

While trying to install mono as 
"sudo apt-get install mono-gmcs mono" I get the error
           "Couldn't find the package mono-gmcs". I have downloaded from the ubuntu site and burnt the iso image.

Any solutions.

Thanks & Regards,
Ravi Kiran.

Are you sure you have all the repos enable in /etc/apt/sources.list?

[http://packages.ubuntu.com/dapper-updates/mono-gmcs](http://packages.ubuntu.com/dapper-updates/mono-gmcs)

```
cat /etc/apt/sources.list
```

---

### Post by BhRaviKiran on 2008-03-07
Thanks for the early reply.

The sources.list do not have any information of the mono runtime reference. Does any hyperlink reference to be added.

I'm new to the world of Ubuntu. Can u plz clarify where i can download the packages and how to unpack the same and run the winform applications.

We are under huge pressure to make this at any cost.

Thanks in advance.
Thanks & Regards,
Ravi.

---

### Post by BhRaviKiran on 2008-03-27
HI Team,
                   I have installed Ubuntu 7.10 and trying to install the Mono 1.2.2.1. I Would like to know what mono packages i can install to run winforms. Is there any possibility of getting the installer file that install all the necessary mono packages.


Plz help us . We are in pressure situation. 

Thanks in advance.
B. Ravi Kiran.

---

### Post by BhRaviKiran on 2008-04-04
Any replies. Is ubuntu has support for Mono?

---

### Post by BhRaviKiran on 2008-04-09
HI All,
          For the foreigners into Ubuntu 7.10, willing to run .net applications follow these steps:

1) Uninstall the existing mono package or try to update the missing libraries. I have uninstalled and constructed the mono package from the Source than depending on the Mono binary files. I have used mono1.2.4-source files to be compiled into binary.

2) Proper version of Libgdiplus is mandatory for running the winform applications. The Site that supplied the mono source should also have supplied libgdiplus source. I luckily found the libgdiplus .deb file for the mono version 1.2.4 and installed. 

3)Compilation of Mono source overcame the reinstallation of Ubuntu OS. During the installation of mono packages thru binary, i couldn't settle the circular dependencies. So had to depend on the mono source.

4) Constructing the mono from source consumes longer time but better than depending on repository update.

Get back to me for any queries. Mono winform execution on Ubuntu 7.10 had shown me hell and I dont want others to suffer. Get back to me for any queries. Mono 1.2.4 winform may not offer silver bullet solution to all winform problems but there are UI issues that need to be addressed by Mono.

Thanks & Regards,
Ravi.

---

