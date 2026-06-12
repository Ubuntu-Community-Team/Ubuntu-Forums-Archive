---
title: "apt-get install returns ttf-opensymbol postinst errors"
date: 2006-12-27
forum: General Help
---

### Post by jakal323 on 2006-12-27
I recently did some updates to openoffice per the suggestions of the update app. It appears that something has gone wrong with the ttf-opensymbol update. As openoffice-core appears to depend on ttf-opensymbol, it breaks. Then all of the other updates break.

'apt-get install' returns the following:

```
jakal323@jakal323-laptop:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up ttf-opensymbol (2.0.4-0ubuntu4) ...
Updating fontconfig cache...
"/usr/share/fonts": error scanning
"/usr/X11R6/lib/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 2.0.4); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-help-en-us:
 openoffice.org-help-en-us depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
dpkg: error processing openoffice.org-help-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-impress; however:
  Package openoffice.org-impress is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-math; however:
  Package openoffice.org-math is not configured yet.
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.0.4~rc3) | openoffice.org-core-experimental (>> 2.0.4~rc3); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-default:
 openoffice.org-style-default depends on openoffice.org-common (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-default (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-industrial:
 openoffice.org-style-industrial depends on openoffice.org-common (= 2.0.4-0ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-industrial (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 python-uno
 openoffice.org-writer
 openoffice.org-help-en-us
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-style-default
 openoffice.org-style-industrial
E: Sub-process /usr/bin/dpkg returned an error code (1)
jakal323@jakal323-laptop:~$
``` 

Does anyone have any input on how to break the logjam? If there is any other information required to fix the problem, please let me know.

---

### Post by jakal323 on 2006-12-29
I just tried reinstalling using synaptic to no avail. Are there any ideas out there?

---

### Post by k@y@ on 2006-12-30
Yes, i got the same problem too. Please someone help us.

---

### Post by brodock on 2006-12-31
same here, it's a bug related to fontconfig package...
someone said it get working installing fontconfig from festy, but i tried here and i got dependencies error (depends on libc6 2.0.5)

---

### Post by brodock on 2006-12-31
installing the package from debian testing, solved the issue

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ff%2Ffontconfig%2Ffontconfig_2.4.1-2_i386.deb&md5sum=3cb8a5e7f5822e8652de54f0a9660956&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ff%2Ffontconfig%2Ffontconfig_2.4.1-2_i386.deb&md5sum=3cb8a5e7f5822e8652de54f0a9660956&arch=i386&type=main)

---

### Post by k@y@ on 2006-12-31
Thanks brodock, you are a great man :)

---

### Post by jakal323 on 2007-01-02
Thanks/Obrigado, brodock. I'll try it right away.

---

### Post by jakal323 on 2007-01-02
That did it. Thanks again!

---

### Post by OliW on 2007-03-11
Sorry for bumping this thread. Turns out I'm a nonce who can't read filenames correctly! My bad.

---

### Post by Blario on 2007-04-09
The instructions here are great!  When I came along though, those links to the debian packages were dead or something though.  This is where I found them.  Good luck guys!```
For anyone other who has this problem and comes to this bug page, the following packages solved the problem for me:

http://packages.debian.org/unstable/utils/fontconfig

http://packages.debian.org/unstable/libs/fontconfig-config

http://packages.debian.org/unstable/libs/libfontconfig1

download every .deb into a folder and install them via "dpkg -i *.deb" - thats it
```

---

### Post by sdlnxgk on 2007-04-11
> **Blario said:**
> The instructions here are great!  When I came along though, those links to the debian packages were dead or something though.  This is where I found them.  Good luck guys!```
For anyone other who has this problem and comes to this bug page, the following packages solved the problem for me:

http://packages.debian.org/unstable/utils/fontconfig

http://packages.debian.org/unstable/libs/fontconfig-config

http://packages.debian.org/unstable/libs/libfontconfig1

download every .deb into a folder and install them via "dpkg -i *.deb" - thats it
```


Great fix +1 got me all updated and error free !!!

---

### Post by RD1945 on 2007-04-11
I just retried several times and it suddenly installed...
Very strange..

---

### Post by tehownt on 2007-04-22
Hi,

installing the package from the debian testing didn't work for me **but** touching every directory needed for the font cache **worked**.

So, for the directories that get: "**failed to write cache**" while doing apt-get/aptitude install/remove ttf-opensymbol, copy all of them in a file, edit it with vim, and remove what is behind the colon in order to have a one column list..

use

```
:%s/\(.\+\):.\+/\1/
```

in vim, 
(this will only keep the directory name column)
and then 

```
for i in `cat tempfile`;do touch $i;done;
```

this allowed me to do

```
sudo aptitude reinstall ttf-opensymbol
```

without any problem.

Hope it helps.

---

### Post by temis01 on 2007-07-12
On july 23 update more files have to touch : here is the new list of directories :
same action has to be done on these directories : 

for i in `cat tempfile`;do touch $i;done;

/usr/share/fonts
/usr/share/fonts/X11
/usr/share/fonts/X11/100dpi
/usr/share/fonts/X11/75dpi
/usr/share/fonts/X11/Type1
/usr/share/fonts/X11/encodings
/usr/share/fonts/X11/encodings/large
/usr/share/fonts/X11/misc
/usr/share/fonts/X11/util
/usr/share/fonts/truetype/arphic
/usr/share/fonts/truetype/baekmuk
/usr/share/fonts/truetype/freefont
/usr/share/fonts/truetype/kochi
/usr/share/fonts/truetype/thai
/usr/share/fonts/truetype/ttf-arabeyes
/usr/share/fonts/truetype/ttf-bengali-fonts
/usr/share/fonts/truetype/ttf-bitstream-vera
/usr/share/fonts/truetype/ttf-dejavu
/usr/share/fonts/truetype/ttf-devanagari-fonts
/usr/share/fonts/truetype/ttf-gentium
/usr/share/fonts/truetype/ttf-gujarati-fonts
/usr/share/fonts/truetype/ttf-kannada-fonts
/usr/share/fonts/truetype/ttf-lao
/usr/share/fonts/truetype/ttf-malayalam-fonts
/usr/share/fonts/truetype/ttf-mgopen
/usr/share/fonts/truetype/ttf-oriya-fonts
/usr/share/fonts/truetype/ttf-punjabi-fonts
/usr/share/fonts/truetype/ttf-tamil-fonts
/usr/share/fonts/truetype/ttf-telugu-fonts
/usr/share/fonts/type1
/usr/share/fonts/type1/gsfonts
/usr/share/X11/fonts
/usr/share/X11/fonts/100dpi
/usr/share/X11/fonts/75dpi
/usr/share/X11/fonts/Type1
/usr/share/X11/fonts/encodings
/usr/share/X11/fonts/encodings/large
/usr/share/X11/fonts/misc
/usr/share/X11/fonts/util
/usr/local/share/fonts
/var/lib/defoma/fontconfig.d/B/
/var/lib/defoma/fontconfig.d/C/
/var/lib/defoma/fontconfig.d/D/
/var/lib/defoma/fontconfig.d/E/
/var/lib/defoma/fontconfig.d/F/
/var/lib/defoma/fontconfig.d/G/
/var/lib/defoma/fontconfig.d/H/
/var/lib/defoma/fontconfig.d/J/
/var/lib/defoma/fontconfig.d/K/
/var/lib/defoma/fontconfig.d/L/
/var/lib/defoma/fontconfig.d/M/
/var/lib/defoma/fontconfig.d/N/
/var/lib/defoma/fontconfig.d/O/
/var/lib/defoma/fontconfig.d/P/
/var/lib/defoma/fontconfig.d/R/
/var/lib/defoma/fontconfig.d/S/
/var/lib/defoma/fontconfig.d/T/
/var/lib/defoma/fontconfig.d/U/
/var/lib/defoma/fontconfig.d/V/
/var/lib/defoma/fontconfig.d/a/
/var/lib/defoma/fontconfig.d/j/
/var/lib/defoma/fontconfig.d/m/
/var/lib/defoma/fontconfig.d/u/

---

