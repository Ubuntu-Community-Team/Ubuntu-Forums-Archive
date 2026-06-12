---
title: "Unable to compile anything"
date: 2007-07-11
forum: General Help
---

### Post by raffytaffy on 2007-07-11
I cannot compile anything. I get this message 

configure: error: C compiler cannot create executables

example-> i am trying to recompile alsa-source to get it to support my card...just an example.

i tried to compile other things, same end result.

for i in control postinst postrm ; do \
		if [ -f debian/$i.orig ]; then \
			mv -f debian/$i.orig debian/$i ; \
		fi ; \
	done
rm -f control-munge
make mrproper
make[1]: Entering directory `/usr/src/modules/alsa-driver'
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
rm -f configure-stamp
rm -f build-stamp
/usr/bin/make -f debian/rules binary-modules
make[1]: Entering directory `/usr/src/modules/alsa-driver'
CC="gcc-4.1" ./configure --prefix=/usr --with-kernel=/lib/modules/2.6.22-ck1/source --with-build=/lib/modules/2.6.22-ck1/source --with-moddir=/lib/modules/2.6.22-ck1/updates/alsa --with-sequencer=yes --with-isapnp=yes --with-debug=detect --with-cards="ca0106"
checking for gcc... gcc-4.1
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
make[1]: *** [configure-stamp] Error 77
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2

i have build essentials, gcc4.1, linux-libc-dev , and all the other programs suggested by the countless threads on here, but i am still unable to compile anything. this is driving me nuts and

---

### Post by ramjet_1953 on 2007-07-12
Have you installed the [COLOR="Blue"]build-essential [/COLOR]package?

if not, copy and paste this into a terminal:

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Also the package [COLOR="Blue"]checkinstall[/COLOR] is good, as it allows you to create a deb package, which you can then install. 
[COLOR="Red"]
sudo apt-get install checkinstall[/COLOR]

The steps to compile and install are then:

[COLOR="Blue"]./configure
make
sudo checkinstall[/COLOR]

You then right click on the package to install it with the debi package installer.

Regards,
Roger :cool:

---

### Post by raffytaffy on 2007-07-12
on the bottom of my question "i have build essentials, gcc4.1, linux-libc-dev , and all the other programs suggested by the countless threads on here, but i am still unable to compile anything. this is driving me nuts and"  lol

---

### Post by ramjet_1953 on 2007-07-12
Sorry, I missed that bottom line.

Perhaps you are having dependency issues?

I have always found it helpful to have a good look at the output of the ./configure command.

If there are any issues it will tell you.

I have noticed that quite often, you can go through all of the steps with dependency problems and it will still compile OK, but of course, the package won't run.

Regards,
Roger :cool:

---

