---
title: "Can not build RPM/DEB packages"
date: 2005-04-19
forum: General Help
---

### Post by anton123 on 2005-04-19
Hello,

First of all, I am very new to Linux I recently downloaded the tarball for gxine 0.4.3 and have decided to tweak the graphics in the pixmaps folder so that they resemble the 0.3.3 version (I replaced them under the exact same version 0.4.3 names with those of the 0.3.3 version for the play, pause, stop, etc. buttons) since I disliked the new style. This is not the real issue though. The issue is that I can not compile the new modified tarball by following the instructions provided at the official xine web page. When running "rpmbuild -ta -v gxine-0.4.3.tar.gz", I get this error:

root@AMD600BOX:/home/user/Desktop # rpmbuild -ta -v gxine-0.4.3.tar.gz
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open rpm database in /var/lib/rpm

What is "db3"? Finding the path to "/var/lib/rpm" returns that it does not exist. Is this normal?

root@AMD600BOX:/home/user/Desktop # cd /var/lib/rpm
bash: cd: /var/lib/rpm: No such file or directory

Last of all, out of curiosity, finding the path of the gcc compiler returns that it does not exist, but Synaptic states that it is installed (it has the green icon):

user@AMD600BOX:~$ whereis gcc
gcc:

What am I doing wrong when compiling the gxine package? Why is gcc absent?

Thank you

---

### Post by Burgundavia on 2005-04-20
Ubuntu uses teh DEB packaing format, so build RPM's is not particularly useful.

For building debs, I would recommend you gander through [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/) first to see if it answers you question.

To get the source to any Ubuntu package, simply go to a command line and type
'apt-get source $package' where $package is the name, in this case gxine. This will download the package and grab the package and extract it under a dir on the name of the package.

I would aslo check out using pbuilder [https://www.ubuntulinux.org/wiki/PbuilderHowto](https://www.ubuntulinux.org/wiki/PbuilderHowto)

However, as a caveat, I have no idea what you are really trying to do, and if you really actually need to rebuild the package to do it.

Corey

---

### Post by anton123 on 2005-04-20
Hello Corey,

Thank you for your input. What I really try to do is the following. I already have the source package of gxine in tarball format(gxine-0.4.3.tar.gz). I have extracted the package to a folder and then navigated to it to the pixmaps folder. There, I have replaced the 0.4.3 icons with those from the 0.3.3 version because I liked those ones much better (that's the good thing about GNU/Linux software versus proprietary software, users are free to modify it the way it works for them. i strongly support that.) Then, I rebuilt the tar.gz package and have went over to xine's website to follow the instructions to build an rpm package from that tarball. Following their instructions, I got the error messages I reported and this is not due to the fact that I have replaced some PNG graphics. Sure, I would like to better build a DEB package so that I can easily install/remove gxine by using Synaptic instead of doing a "make install" and then to manually navigate to each folder to erase all traces of gxine should I want to uninstall it (it reminds me of Windows and its registry too). My questions are: Is there a problem with Ubuntu itself that I get those two error messages? Am I doing anything wrong? I am a complete newbie to Linux but I enjoy it much better than Windows, especially XP which is a pile of bloated crap.

---

### Post by speedman on 2005-04-20
gcc is not installed by default on Ubuntu.  After you install it add checkinstall from the universe repository as well to your system.

Then do the regular ./configure && make in the source directory for the app you are compiling, but instead of issuing the make install command use checkinstall to build a .deb package of your compiled app.

More information can be found on checkinstall here:

[http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

Btw, Ubuntu is a Debian based distro and therefore does not use RPMs as the packaging format.  While you can convert some RPMs to .debs with alien it is always better to use a .deb rather than gambling on a converted package built for a different distribution/platform.


Regards,

SM

---

### Post by anton123 on 2005-04-20
Thank you for the reply. I have installed checkinstall. Unfortunately, I have more problems. GCC is installed, but executing the ./configure script from the gxine source, I get an error:

[email]root@AMD600BOX:/home/user/Desktop/gxine-0.4.3.tar.gz[/email]_FILES/gxine-0.4.3 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Why can't the compiler make an executable? Therefore I can not execute "make". This is extremely frustrating.

Out of curiosity I tried the same steps from within a Knoppix CD session. This is what I got:

root@ttyp1[gxine-0.4.3]# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out

"checking for C compiler default output file name... a.out" is what I should see but i don't. Why?

---

### Post by anton123 on 2005-04-20
Ok, I don't know what the hell is going on here but if someone can solve this mystery, I would be glad. Here is what I did. I went into MEPIS and still I had plenty of adventures. After nearly one hour of gcc complaining about missing packages and opening/closing KPackage to get the needed packages, I managed to compile my customized gxine, version 0.4.3 but another blessing came my way, an error (towards the very end of the "make" command by using and also by not using "checkinstall"):

gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../include -I/usr/local/
include -I../pixmaps    -I/usr/include -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/
lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/p
ango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in
clude   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DLOCALED
IR=\"/usr/local/share/locale\"  -c `test -f 'engine.c' || echo './'`engine.c
engine.c: In function `engine_init':
engine.c:116: error: `XINE_ENGINE_PARAM_VERBOSITY' undeclared (first use in this function)
engine.c:116: error: (Each undeclared identifier is reported only once
engine.c:116: error: for each function it appears in.)
make[2]: *** [engine.o] Error 1
make[2]: Leaving directory `/home/user/Desktop/gxine-0.4.2/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/user/Desktop/gxine-0.4.2/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

WHAT? WHY? gxine 0.4.2 does the same thing (it is a stable release). IS THIS AN ERROR ON THE PART OF THE AUTHOR WHO CODED GXINE (HE FAILED TO DECLARE THE DATA TYPE FOR `XINE_ENGINE_PARAM_VERBOSITY' VARIABLE? AM I A BLOODY IMBECILE OR WHAT? I would prefer a member of the Ubuntu team who contributed to the creation of the gxine 0.4.1 package in the Universe repository to clarify to me the trick of the trade, namely, of how he, as a magician, pulls a rabbit out of an empty hat. I followed the steps but it simply does not work and I feel terribly frustrated.

---

### Post by anton123 on 2005-04-22
Did anyone find a solution or a reason as to why gxine can not be compiled under Ubuntu?

---

