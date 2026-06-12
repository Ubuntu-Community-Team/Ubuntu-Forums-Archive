---
title: "Installing a kmuddy debian binary"
date: 2005-08-22
forum: General Help
---

### Post by Tokugawa on 2005-08-22
I just tried installing a Kmuddy Debian binary and it failed. There were multiple packages that are not installed and version mismatches. Is there a testing repository that I can change my apt-source file to grab the latest packages?

Below is the errors I received.

dpkg -i kmuddy_0.7.1-3_i386.deb
(Reading database ... 58885 files and directories currently installed.)
Preparing to replace kmuddy 0.7.1-3 (using kmuddy_0.7.1-3_i386.deb) ...
Unpacking replacement kmuddy ...
dpkg: dependency problems prevent configuration of kmuddy:

kmuddy depends on kdelibs4 (>= 4:3.4.1-1); however:
Version of kdelibs4 on system is 4:3.4.0-0ubuntu3.4.

kmuddy depends on libaa1 (>= 1.2); however:
Package libaa1 is not installed.

kmuddy depends on libartsc0 (>= 1.4.1-1); however:
Version of libartsc0 on system is 1.4.0-0pre1ubuntu3.

kmuddy depends on libasound2 (>> 1.0.9); however:
Version of libasound2 on system is 1.0.8-1.

kmuddy depends on libc6 (>= 2.3.5-1); however:
Version of libc6 on system is 2.3.2.ds1-20ubuntu14.

kmuddy depends on libfontconfig1 (>= 2.3.0); however:
Version of libfontconfig1 on system is 2.2.3-4ubuntu7.

kmuddy depends on libgcc1 (>= 1:4.0.1); however:
Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.

kmuddy depends on libglib2.0-0 (>= 2.7.1); however:
Version of libglib2.0-0 on system is 2.6.3-1.

kmuddy depends on libidn11 (>= 0.5.18); however:
Version of libidn11 on system is 0.5.2-3.

kmuddy depends on libmxp0; however:
Package libmxp0 is not installed.

kmuddy depends on libncurses5 (>= 5.4-5); however:
Version of libncurses5 on system is 5.4-4.

kmuddy depends on libqt3c102-mt (>= 3:3.3.4); however:
Version of libqt3c102-mt on system is 3:3.3.3-7ubuntu3.

kmuddy depends on libsdl-mixer1.2 (>= 1.2.6); however:
Package libsdl-mixer1.2 is not installed.

kmuddy depends on libslang2 (>= 2.0.1-1); however:
Package libslang2 is not installed.

kmuddy depends on libsmpeg0c2; however:
Package libsmpeg0c2 is not installed.

kmuddy depends on libstdc++6 (>= 4.0.1); however:
Package libstdc++6 is not installed.

kmuddy depends on libsvga1; however:
Package libsvga1 is not installed.

kmuddy depends on libvorbis0a (>= 1.1.0); however:
Version of libvorbis0a on system is 1.0.1-1.

kmuddy depends on libvorbisfile3 (>= 1.1.0); however:
Version of libvorbisfile3 on system is 1.0.1-1.

kmuddy depends on libxrender1 (>> 1:0.9.0-1); however:
Version of libxrender1 on system is 0.9.0-0ubuntu4.

dpkg: error processing kmuddy (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
kmuddy

---

### Post by Takis on 2005-08-22
[QUOTE=Tokugawa]I just tried installing a Kmuddy Debian binary and it failed. [/QUOTE]
You've nailed your problem in the first line. Debian binaries are not the same as Ubuntu binaries. They use the same format but will not necessarily work on each other's platforms - you'll need to compile the program from source (ask us how if you need to!). If you've added Debian repositories to your /etc/apt/sources.list file, I highly recommend you remove these to avoid breaking your system.

---

### Post by Tokugawa on 2005-08-22
Ok, that's good to know. 

I did not change my sources.list file as I knew that might not be a good idea.

I did try and compile kmuddy before trying the Debian binary and things did not go well. 

I am game to try it further with some help. I'll get the source later today and then post the errors that are generated.

Thanks for the help.

---

### Post by Tokugawa on 2005-08-22
When I run the configure file I get the following error:

checking for Qt... configure: error: Qt (>= Qt 3.1.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!

I did notice I have qt3 in the following directories:

/usr/include/qt3
/usr/lib/qt3
/usr/share/lintian/overrides/libqt3-mt-dev

I ran configure with the following command which I thought would tell the configure script where to find qt:
./configure --with-qt-includes=/usr/include/qt3 --with-qt-libraries=/usr/lib/qt3 

Anyone know how to fix this so I can compile?

Thanks

---

### Post by arnieboy on 2005-08-23
[QUOTE=Tokugawa]When I run the configure file I get the following error:

checking for Qt... configure: error: Qt (>= Qt 3.1.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!

I did notice I have qt3 in the following directories:

/usr/include/qt3
/usr/lib/qt3
/usr/share/lintian/overrides/libqt3-mt-dev

I ran configure with the following command which I thought would tell the configure script where to find qt:
./configure --with-qt-includes=/usr/include/qt3 --with-qt-libraries=/usr/lib/qt3 

Anyone know how to fix this so I can compile?

Thanks[/QUOTE]
it needs qt 3.1.0 and u have some earlier version installed  possibly. thats whats causing the dependency problem.

---

### Post by Tokugawa on 2005-08-23
Can I update my sources.list file to get the latest Qt so I can compile the source?

---

### Post by CzarAlex on 2005-09-06
[QUOTE=Takis] you'll need to compile the program from source (ask us how if you need to!). [/QUOTE]

I appear to be in the same boat. I can obtain the source package and am unsure how to compile it to work with Ubuntu and Gnome. Please enlighten me.

Will doing this fix all those nasty dependency errors that Tokugawa and I receive? or will I need to install some other libraries after i compile from source to allow the KDE based prog to run in gnome?

Yes... I am noobish :( But getting better. :)

---

### Post by thom_raindog on 2007-04-10
My ./configure dies cause it doesn't find what it calls "libz".
Anyone had this problem  and solved it?

---

### Post by CzarAlex on 2007-04-10
is that libz a package you need to install? What happens when you:

```

sudo apt-get install libz

```

Perhaps that`ll install it.

---

### Post by thom_raindog on 2007-04-10
libz doesn't seem to be a package. At least
```

sudo apt-get install libz

```
results in "Can't find packet libz"

---

### Post by CzarAlex on 2007-04-10
It may be called libz-dev instead. Open up synaptic package manager and search for anything entitled libz. Perhaps adding those`ll help.

---

### Post by Takis on 2007-04-11
Couple of cool little code snippets for you.

List all files that have the string 'libz' in the name:
```
taki@mrflibble:~$ locate libz
/usr/lib/libz.so.1
/usr/lib/libz.so.1.2.3
taki@mrflibble:~$
```

Which one do I want? Fortunately, the first result just points to the second:
```
taki@mrflibble:~$ ls -l /usr/lib/libz.so.1
lrwxrwxrwx 1 root root 13 2007-02-25 09:32 /usr/lib/libz.so.1 -> libz.so.1.2.3
taki@mrflibble:~$
```

(dpkg is the backend to apt) Tell me what package owns the file /usr/lib/libz.so.1.2.3:
```
taki@mrflibble:~$ dpkg -S /usr/lib/libz.so.1.2.3
zlib1g: /usr/lib/libz.so.1.2.3
taki@mrflibble:~$
```

Therefore you probably need to install zlib1g:
```
sudo apt-get install zlib1g
```

---

### Post by CzarAlex on 2007-04-11
Takis,
   Thank you very much for the helpful code -**AND**- for explaining what it does in simple to understand terms. Its people like you who go out of their way to educate those in need that make (k)ubuntu accessible to the masses.

:popcorn:

---

### Post by Vadi on 2007-10-11
A new deb package for 0.8 version of kmuddy, made by getdeb.net, is now avialable :)

---

