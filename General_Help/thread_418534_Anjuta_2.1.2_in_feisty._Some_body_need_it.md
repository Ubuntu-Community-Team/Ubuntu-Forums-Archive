---
title: "Anjuta 2.1.2 in feisty. Some body need it?"
date: 2007-04-22
forum: General Help
---

### Post by klaim on 2007-04-22
Hi *

just mail me if some body would use it. unfortunately i haven't place to put it on inet.

[FONT="Courier New"]$ ls -1 -s -h ./*.deb
2.2M ./anjuta-common_2.1.2-1_all.deb
240K ./anjuta-dev_2.1.2-1_i386.deb
1.9M ./anjuta_2.1.2-1_i386.deb
232K ./gnome-build_0.1.5-1_i386.deb
 92K ./libgdl-1-0_0.7.3-1_i386.deb
116K ./libgdl-1-common_0.7.3-1_all.deb
 32K ./libgdl-1-dev_0.7.3-1_i386.deb
 28K ./libgdl-gnome-1_0.7.3-1_i386.deb[/FONT]

---

### Post by Burkey on 2007-04-23
Me!  I sent you an ICq request.  I am a KDevelop fan, so am interested to see if a newer version of Anjuta can satisfy me.  In particular I want to see how good it's GTKmm integration is (GTK2.4 for instance)

---

### Post by klaim on 2007-04-23
How i can send you? can you give me an email?

---

### Post by GWolf77 on 2007-04-24
I'm interested and would have some inet-space available to host the Source-Files.

---

### Post by chiefofthejojos on 2007-04-24
me too! :)

---

### Post by klaim on 2007-04-24
get it from [ftp://ghost.corbina.net](ftp://ghost.corbina.net)
but this is my laptop. i'll not poweroff for u :) u have 1 day for do it.
please, post here an url for other ppls.

---

### Post by klaim on 2007-04-24
forget... u'll need a manual hack :)
#ln -s /usr/lib/libgdl-gnome-1.so.0 /usr/lib/libgdl-gnome-1.so

just i'm lazy to fix the package ;)

---

### Post by chiefofthejojos on 2007-04-24
A few tips on installation.  Make sure to install libdevhelp-1-0 first.
Also, I recommend download all the debs and installing like so:
```
sudo dpkg -i *.deb
```
I had to do it twice before it succeeded.  GDebi has problems with some of the debs.
Thanks klaim

---

### Post by klaim on 2007-04-25
what packages have problems?

---

### Post by chiefofthejojos on 2007-04-25
Sorry, it doesn't show me the errors anymore now that it's installed.  I'm a little scared to uninstall because this is my work computer and I don't want to lose any configuration.
It was with anjuta and anjuta-common.  For some reason it seems to think the version of your packages is less than the version installed with ubuntu.  In fact, they show up in the list in the update manager although they are grayed out.

---

### Post by chiefofthejojos on 2007-04-25
When I "sudo apt-get update && sudo apt-get upgrade" I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  anjuta anjuta-common
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```not sure what that means...

---

### Post by chiefofthejojos on 2007-04-25
BTW, thank you very much for the packages.:D  That install would have been a hell of a lot harder without your packages and the beta is SO much better than 1.2.

---

### Post by klaim on 2007-04-25
about...
"The following packages have been kept back:
  anjuta anjuta-common
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded."...

just you need to create /etc/apt/preferences:
Package: anjuta                                                                                                                          
Pin: version 2.1.2*                                                                                                                      
Pin-Priority: 990                                                                                                                        
                                                                                                                                         
Package: anjuta-common                                                                                                                   
Pin: version 2.1.2*                                                                                                                      
Pin-Priority: 990

that is can help to resolve your problem :)

may u need learn more about APT system. [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html),
in particular - 3.10 How to keep specific versions of packages installed (complex)

---

### Post by chiefofthejojos on 2007-04-25
I locked my packages but the problem is a bit deeper.  Ubuntu thinks the default feisty version of the package is NEWER than the package you made.  When GDebi didn't allow me to install those packages it said it was because the package installed on my system was newer.  It showed the version installed on my system as "1:1.2.4" and the version of your package as "0:2.1.2".  I guess it has something to do with that number before the ":"?

---

### Post by klaim on 2007-04-25
# apt-cache show anjuta
Package: anjuta
Priority: optional
Section: universe/gnome
Installed-Size: 2144
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Rob Bradford <robster@debian.org>
Architecture: i386
**Version: 1:1.2.4a-5build1**[COLOR="Red"]<-- ubuntu's package[/COLOR]
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.3.14), libfontconfig1 (>= 2.4.0), libgcc1 (>= 1:4.1.2), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.9), libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>= 2.14.1), libgnomecanvas2-0 (>= 2.11.1), libgnomeprint2.2-0 (>= 2.17.0), libgnomeprintui2.2-0 (>= 2.17.0), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.10.3), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.1), libpango1.0-0 (>= 1.16.0), libpcre3 (>= 4.5), libpopt0 (>= 1.10), libsm6, libstdc++6 (>= 4.1.2), libvte9 (>= 1:0.13.3), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxft2 (>> 2.1.1), libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>= 2:1.2.0), libxrender1, zlib1g (>= 1:1.2.1), scrollkeeper, anjuta-common (>= 1:1.2.4)
Recommends: gcc | g++, make, cvs, gnome-terminal, yelp, automake1.4, autoconf, autogen, indent, gdb, ctags, devhelp, gnome-devel, libtool
Suggests: libgtk2.0-dev, libgtkmm2.0-dev, libgnome2-dev, libgnomemm2.0-dev, devhelp-books, glade-2 | glade-gnome-2
Filename: pool/universe/a/anjuta/anjuta_1.2.4a-5build1_i386.deb
Size: 935276
MD5sum: ef7f039c38ae561d9cb80ff24ad78b53
SHA1: 6e4f5a1e94976ecc774c44d5958cf0ccacedaf2b
SHA256: d69df155eabbdc4aa24fc89c900b2685a779df045a5124a50b3ce0928ac6761d
Description: A GNOME development IDE for C/C++
 This IDE for C/C++ and GNOME/Gtk+ applications has features that enable easy
 debugging and management of code. It also integrates with Glade and CVS.
 .
 [http://www.anjuta.org](http://www.anjuta.org)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

Package: anjuta
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 4492
Maintainer: Rob Bradford <robster@debian.org>
Architecture: i386
**Version: 2.1.2-1**[COLOR="Red"]<-- my package[/COLOR]
Depends: gnome-build, libapr1, libaprutil1, libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.4.2), libdevhelp-1-0 (>= 0.13), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2), libgcc1 (>= 1:4.1.2), libgconf2-4 (>= 2.13.5), libgdl-1-0, libgdl-gnome-1, libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.9), libgnome-keyring0 (>= 0.7.1), libgnome2-0 (>= 2.14.1), libgnomecanvas2-0 (>= 2.11.1), libgnomeprint2.2-0 (>= 2.17.0), libgnomeprintui2.2-0 (>= 2.17.0), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.10.3), libgtksourceview1.0-0 (>= 1.7.2), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.1), libpango1.0-0 (>= 1.16.2), libpcre3 (>= 4.5), libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.10), libsm6, libstdc++6 (>= 4.1.2), libsvn1 (>= 1.4), libuuid1, libvte9 (>= 1:0.16.0), libwnck18 (>= 2.15.90), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxft2 (>> 2.1.1), libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>= 2:1.2.0), libxrender1, libxslt1.1 (>= 1.1.20), zlib1g (>= 1:1.2.1), scrollkeeper, anjuta-common (= 2.1.2-1)
Recommends: gcc | g++, make, cvs, gnome-terminal, yelp, automake, autoconf, autogen, indent, gdb, ctags, devhelp, gnome-devel, libtool
Suggests: libgtk2.0-dev, libgtkmm2.0-dev, libgnome2-dev, libgnomemm2.0-dev, devhelp-books, glade-2 | glade-gnome-2
Description: A GNOME development IDE, for C/C++
 This IDE for C/C++ and GNOME/Gtk+ applications has features that enable easy
 debugging and management of code. It also integrates with glade and CVS.
 .
 [http://www.anjuta.org](http://www.anjuta.org)

---

### Post by klaim on 2007-04-25
# LANG=C apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

as u can see... i have no problem like ur :)

---

### Post by chiefofthejojos on 2007-04-25
interesting.  I don't know what to think because I did it on a brand new feisty installation.  If no one else has the problem I guess it's fine.  I locked the packages to 2.1.2 so I'm satisfied.
Thanks klaim! :)

---

### Post by klaim on 2007-04-25
try to remove all anjuta versions and install again. i think u have installed my packages over ubuntu's anjuta

---

### Post by klaim on 2007-04-25
> **chiefofthejojos said:**
> 
Thanks klaim! :)
u welcome :) feel free to contact by jabber. will try to help you with other questions :^)

---

### Post by chiefofthejojos on 2007-04-26
Thanks klaim.  I guess GDebi gave me errors before because I already had anjuta installed.  I didn't think about that.  I uninstalled and reinstalled, and it works fine, however I still need to lock the version on those packages and I get a warning in gdebi (attached).  It's just a warning though and it installs fine.
Maybe aptitude assumes a "0:" by default when no number is provided?
Anyway, it works fine for me so I'm not complaining, just reporting. ;)

---

### Post by foundation on 2007-05-04
Thanks for the packages, worked fine in Feisty. :)

---

### Post by neilcavendish on 2007-05-04
Could i have the files as well please.

---

### Post by klaim on 2007-05-06
try again at [ftp://ghost.corbina.net](ftp://ghost.corbina.net)

---

### Post by neilcavendish on 2007-05-06
Thanks i was able to get them.

---

### Post by neilcavendish on 2007-05-06
I just installed them and i got this error do u know what it is? 
Errors were encountered while processing:
 gnome-build_0.1.5-1_i386.deb
 anjuta
 anjuta-dev

---

### Post by neilcavendish on 2007-05-06
Ok so i have more details on the erros.
dpkg: dependency problems prevent configuration of anjuta:
 anjuta depends on gnome-build; however:
  Package gnome-build is not installed.
 anjuta depends on libapr1; however:
  Package libapr1 is not installed.
 anjuta depends on libaprutil1; however:
  Package libaprutil1 is not installed.
 anjuta depends on libsvn1 (>= 1.4); however:
  Package libsvn1 is not installed.
dpkg: error processing anjuta (--install):
 dependency problems - leaving unconfigured
Setting up anjuta-common (2.1.2-1) ...

dpkg: dependency problems prevent configuration of anjuta-dev:
 anjuta-dev depends on anjuta (= 2.1.2-1); however:
  Package anjuta is not configured yet.
dpkg: error processing anjuta-dev (--install):
 dependency problems - leaving unconfigured
Setting up libgdl-1-common (0.7.3-1) ...
Setting up libgdl-gnome-1 (0.7.3-1) ...

Setting up libgdl-1-0 (0.7.3-1) ...

Setting up libgdl-1-dev (0.7.3-1) ...
Errors were encountered while processing:
 gnome-build_0.1.5-1_i386.deb
 anjuta
 anjuta-dev

I then tryed to install the gnome-build
sudo dpkg -i gnome-build_0.1.5-1_i386.deb 
(Reading database ... 150398 files and directories currently installed.)
Unpacking gnome-build (from gnome-build_0.1.5-1_i386.deb) ...
dpkg: error processing gnome-build_0.1.5-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgbf-1.so.0.0.1', which is also in package libgbf-1-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gnome-build_0.1.5-1_i386.deb

Ok so i fixed the dependancy probs but cant install gnome-build. Any help would be much appriciated. Cheers

---

### Post by klaim on 2007-05-07
please, read previous posts. may you need to uninstall Anjuta 1.2.4 (ubunu's reps).
and try again like 
#dpkg -i /path/to/downloaded/anjuta-s-debs/*.deb

---

### Post by kazaawang on 2007-05-22
Thanks to Klaim for sending me those files. I uploaded them into my box.net space:

[http://www.box.net/shared/n1rfxpyrdr#1:6712590]("http://www.box.net/shared/n1rfxpyrdr#1:6712590")

It is a public space, anybody can download from there.

Enjoy.

Keywords: Anjuta, Anjuta2, Ubuntu, Feisty

---

### Post by kazaawang on 2007-05-24
I installed that. It works fine.

This is what I did:

Make sure to install libdevhelp-1-0.
Make sure to uninstall libgbf, libgbf-common.

sudo ln -s /usr/lib/libgdl-gnome-1.so.0 /usr/lib/libgdl-gnome-1.so
sudo dpkg -i *.deb

install autogen version 5.

Thanks again Klaim.

---

### Post by mrincredible on 2007-07-22
The above packages worked, but screwed up my system, and apt has been crying like a baby ever since. This is on a clean feisty installation.

Rather go to anjuta.org and get the url for 2.2.0 Stable.

I think this is the repo to add to synaptic:

deb [http://anjuta.org/apt](http://anjuta.org/apt) ./

And you'll get everything via Synaptic. Uninstall anjuta first, or use the force version.

---

