---
title: "Installing Mono on Ubuntu"
date: 2007-09-23
forum: General Help
---

### Post by Charlatat on 2007-09-23
Ok, I was having a heck of a time getting gui apps working after installing Mono 1.2.5.1. Neither GTK/GTK2 or WinForms worked correctly.  After a long time of struggling with it, I finally got everything working with the help of [https://help.ubuntu.com/community/MonoFromSource](https://help.ubuntu.com/community/MonoFromSource). GTK, GTK2 and WinForms work great now.  However, to get things working I ended up installing a LOT of packages (the webpage was a bit outdated) . Too many, I'm sure.  I'd like some help in trimming the list down, though. If you can lend a hand or offer some helpful tips, I'd appreciate it. Here's what I did:

```
 1. Install Ubuntu 7.04
 2. Enable all sources in /etc/apt/sources.list
 3. Perform sudo apt-get update and sudo apt-get upgrade
 4. Restart
 5. Perform sudo apt-get update and sudo apt-get dist-upgrade
 6. Restart
 7. Go to http://go-mono.com/sources-stable/ and download these packages:
	A. mono-1.2.5.1.tar.bz2
	B. libgdiplus-1.2.5.tar.bz2
	C. gtk-sharp-1.0.10.tar.gz
	D. monodoc-1.2.5.zip
	E. gecko-sharp-2.0-0.12.tar.gz
	F. mono-debugger-0.50.tar.bz2
	G. gtk-sharp-2.10.2.tar.bz2
	H. gnome-sharp-2.16.0.tar.gz
 8. Extract them all to a temp directory
 9. Open up Synaptic Package Manager and install these packages (accept all dependecies):
	A. build-essential
	B. devscripts
	C. dh-buildinfo
	D. sbuild
	E. pkg-config
	F. libextutils-pkgconfig-perl
	G. libgift-dev
	H. libpthread-stubs0-dev
	I. xserver-xorg-dev
	J. bison
	K. bison-doc
	L. libcairo2-dev
	M. libcairo2-doc
	N. libcairo-directfb2
	O. libcairo-directfb2-dev
	P. libglib1.2
	Q. libglib1.2-dbg
	R. libglib1.2-dev
	S. libglib2.0-0
	T. libglib2.0-0-dbg
	U. libglib2.0-cil
	V. libglib2.0-data
	W. libglib2.0-dev
	X. libglib2.0-doc
	Y. libungif4-dev
	Z. libungif-bin
	AA. libjpeg-progs
	BB. libtiff4-dev
	CC. libtiff-opengl
	DD. libtiff-tools
	EE. libtiffxx0c2
	FF. libgnome-desktop-dev
	GG. libgtk-html2-dev
	HH. libgtkhtml3.14-dbg
	II. libgtkhtml3.14-dev
	JJ. libgtkhtml3.8-dev
	KK. libgtkhtml3.8-15
	LL. libgtkhtml3.8-dbg
	MM. libgtkhtml3.8-dev
	NN. libvte2.0-cil
	OO. libvte-cil
	PP. libvte-dev
	QQ. libvte-doc
	RR. librsvg2-bin
	SS. librsvg2-dev
	TT. libgail-gnome-dbg
	UU. libgail-gnome-dev
	VV. libgnome2-doc
	WW. libgnomecanvas2-doc
	XX. libgnome-cil
	YY. libgnomedb2-4
	ZZ. libgnome2-4-dbg
	AAA. libgnomedb2-bin
	BBB. libgnomedb2-dev
	CCC. libgnomedb2-doc
	DDD. libgnome-dev
	EEE. libgnomevi-doc
	FFF. libpanel-applet2-dev
	GGG. libpanel-applet2-doc
	HHH. gawk
	III. gawk-doc
	JJJ. exif
	KKK. exiftags
	LLL. exifrun
	MMM. exifprobe
	NNN. libexif
	OOO. libexif-gtk-dev
	PPP. libexif-gtk5
	QQQ. libpango1.0-dbg
	RRR. libpango1.0-doc
	SSS. libsdl-pang1
	TTT. libsdl-pango-dev
10. Configure/make libgdiplus-1.2.5:
	A. ./configure --prefix=/usr/local
	B. make
	C. sudo make install
11. sudo nano /etc/ld.so.conf
	A. Add /usr/local/lib
	B. Add /usr/local
12. sudo ldconfig
13. Configure/make mono-1.2.5.1:
	A. ./configure --prefix=/usr/local --with-preview=yes
	B. make
	C. sudo make install
14. Run mono -V to verify mono version
15. Configure/make gtk-sharp-1.0.10:
	A. ./configure --prefix=/usr/local --with-preview=yes
	B. make
	C. sudo make install
16. Configure/make gtk-sharp-2.0.10:
	A. ./configure --prefix=/usr/local
	B. make
	C. sudo make install
17. Configure/make gnome-sharp-2.16.0:
	A../configure --prefix=/usr/local
	B. make
	C. sudo make install
18. Configure/make gecko-sharp-2.0-0.12:
	A../configure --prefix=/usr/local
	B. make
	C. sudo make install
19. Configure/make mono-debugger-0.50:
	A../configure --prefix=/usr/local
	B. make
	C. sudo make install
20. Configure/make monodoc-1.2.5:
	A../configure --prefix=/usr/local
	B. make
	C. sudo make install
21. sudo ldconfig (possibly restart too)
22. Be mindful of any errors that reference a particular mono folder (when launching an app) and add it to /etc/ld.so.conf and do a sudo ldconfig. I had to do this once, but not always.
```

---

### Post by Charlatat on 2007-09-24
*bump*

---

### Post by bergetun on 2007-10-08
Thank you very much for putting this on, I have spent days getting the winform working with mono 1.2.5 on ubuntu with no luck. 

But I cant get past the compiling of libgdiplus . 

Getting this error : 

[PHP]
../src/.libs/libgdiplus.so: undefined reference to `png_set_expand_gray_1_2_4_to_8'
collect2: ld returned 1 exit status
make[2]: *** [testgdi] Error 1
make[2]: Leaving directory `/home/bergetun/libgdiplus-1.2.5/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bergetun/libgdiplus-1.2.5'
make: *** [all] Error 2

[/PHP]


I think its kinda strange that there is no deb packages for Mono 1.2.5 on ubuntu .

---

### Post by Charlatat on 2007-10-08
1. try using Synaptic and installing libpng packages
2. try doing step #11 and #12
3. try compiling libgdiplus again

---

### Post by posterboy on 2007-10-09
Don't forget about apt-get build-dep package-name. That's a life-saver for those of us who need to compile stuff. I needed to re-compile beagle, in order to get t-bird support, and that command went and got all the mono stuff, and everything needed to do so.

---

### Post by ENielsen on 2007-10-30
> **bergetun said:**
> Thank you very much for putting this on, I have spent days getting the winform working with mono 1.2.5 on ubuntu with no luck. 

But I cant get past the compiling of libgdiplus . 

Getting this error : 

[PHP]
../src/.libs/libgdiplus.so: undefined reference to `png_set_expand_gray_1_2_4_to_8'
collect2: ld returned 1 exit status
make[2]: *** [testgdi] Error 1
make[2]: Leaving directory `/home/bergetun/libgdiplus-1.2.5/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bergetun/libgdiplus-1.2.5'
make: *** [all] Error 2

[/PHP]


I think its kinda strange that there is no deb packages for Mono 1.2.5 on ubuntu .
I am having the same problem building on 6.06 LTS. It seems like this may be related to a problem with binutils. This is Bug 325511 in the Mono database:

[https://bugzilla.novell.com/show_bug.cgi?id=MONO82844](https://bugzilla.novell.com/show_bug.cgi?id=MONO82844)

---

### Post by agibby5 on 2007-11-10
seems like a lot of steps to get this thing to work.  I just installed it from the package manager, and it worked except i didn't have the winforms designer.  I hope that the installation for these 'add-ons' will become more streamlined soon.  I'd like to dump windows asap! :)

---

### Post by tgs1952 on 2007-11-10
I began installing mono this morning using synaptic. The install is hanging at configuring Apache = stuck there for over an hour. At what point should I cancel?

I am using Feisty on a ppc.

---

