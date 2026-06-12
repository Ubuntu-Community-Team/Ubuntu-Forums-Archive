---
title: "Pixma MG6250 scan gear installation problems"
date: 2012-11-29
forum: General Help
---

### Post by Bhakti108 on 2012-11-29
Hope someone can help, I have scoured the forums for help but can't find anyhting. 

I have a Pxma MG6250 all in one -- the printer part has installed correctly after some jigging of the install script re architecture. However the scangear drivers will not install. 

I have jigged the install script per instructions from here so that it will recognise the architecture but then I get this error coming up 

```
[I]An error occurred. A necessary package could not be found in the proper location.
douglas@douglas-K53SV:~/Documents/Downloads/Canon Drivers/scangearmp-mg6200series-1.80-1-deb$ [/I]
```What package is missing? or in the wrong location. This is a meaningless error message and very frustrating as I have now been on this for 2 hours. 


Please help if possible.

---

### Post by Bhakti108 on 2012-11-29
Bump

---

### Post by pdc on 2012-11-30
so I would go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100396002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100396002.html)

and download scangearmp-mg6200series-1.80-1-deb.tar.gz

and if I suggest some terminal commands for you ......if you copy and paste each and hit the enter key after pasting each command ........

> [COLOR="Red"]cd Downloads[/COLOR]

> [COLOR="Red"]tar -zxvf scangearmp-mg6200series-1.80-1-deb.tar.gz[/COLOR]

> [COLOR="Red"]cd scangearmp-mg6200series-1.80-1-deb[/COLOR]

> [COLOR="Red"]install.sh[/COLOR]

......that should install it for you ........

 .......to run scangear ....if you issue the command

> [COLOR="Red"]scangearmp[/COLOR]

.....it opens the programme...........

 .......... you may well prefer a launcher for repeated uses .....

........such links as this

[http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/](http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/)

.......tell you how.....

.....we hope all goes well for you .........

---

### Post by Bhakti108 on 2012-12-02
Thanks for the help, but ,maybe I wasn't clear enough. I have done all of your commands, exactly, but when it comes to the command ```
sudo ./install.sh 
```-- I get that error and no way to find out what is missing. 

Incidentally following canon's install htm results in "unknown architecture' error, which is well detailed in other threads. That i what I meant  for jigging the bash script. 

So the same errors occurred with the bash script for installing the printer, but after correcting the script, it went fine. Scan gear will not though. 

Any ideas?

---

### Post by pdc on 2012-12-02
let's get some details;

please let us know........

.........version of ubuntu.....32bit.........64bit........standalone computer.......usb cable to 6250..............

.....you say..........

> *but when it comes to the command Code: sudo ./install.sh* 

...........where did you get the sudo ./install.sh from ..(I didn't use it..) ..............see post #3 above ...................

.....you also say............

> -- *I get that error* and no way to find out what is missing. 

.............help me understand..............which error?

the intention of the [COLOR="Magenta"]install.sh[/COLOR] is to make things easier...but...

............if one looks at the packages that Canon supply, (see thumbnail below); they supply both 32bit and 64bit.........and they can be installed from the directory they are packaged in........called Packages.......

...........as with many Canon packages.......there is 

1) a [COLOR="RoyalBlue"]COMMON[/COLOR] package to install 

......and then ........

2) a [COLOR="RoyalBlue"]SPECIFIC[/COLOR] (MG6200series) package

..........so one could work out if one has 32bit or 64bit and install the correct common and then specific ............. using gdebi installer................

---

### Post by Bhakti108 on 2012-12-02
Ok I will try to answer all your questions.

1) 32bit Ubuntu 12.04
2) Laptop - wireless - standalone
3) The sudo./install command comes directly from the canon install guide 

Ok here is what the terminal gives me, 

```

Canon Drivers$ tar zxvf scangearmp-mg6200series-1.80-1-deb.tar.gz 

scangearmp-mg6200series-1.80-1-deb/
scangearmp-mg6200series-1.80-1-deb/packages/
scangearmp-mg6200series-1.80-1-deb/packages/scangearmp-mg6200series_1.80-1_amd64.deb
scangearmp-mg6200series-1.80-1-deb/packages/scangearmp-common_1.80-1_i386.deb
scangearmp-mg6200series-1.80-1-deb/packages/scangearmp-common_1.80-1_amd64.deb
scangearmp-mg6200series-1.80-1-deb/packages/scangearmp-mg6200series_1.80-1_i386.deb
scangearmp-mg6200series-1.80-1-deb/resources/
scangearmp-mg6200series-1.80-1-deb/resources/scanner_ja_utf8.lc
scangearmp-mg6200series-1.80-1-deb/resources/scanner_fr_utf8.lc
scangearmp-mg6200series-1.80-1-deb/resources/scanner_zh_utf8.lc
scangearmp-mg6200series-1.80-1-deb/install.sh


```

```


Canon Drivers$ cd scangearmp-mg6200series-1.80-1-deb


```

```

scangearmp-mg6200series-1.80-1-deb$ install.sh
**install.sh: command not found**

```

However putting (direct from the Canon html guide to installing scangear)

```
 

scangearmp-mg6200series-1.80-1-deb$[B] sudo ./install.sh
[/B]
ScanGear MP
Version 1.80
Copyright CANON INC. 2007-2011
All Rights Reserved.

==================================================
An error occurred. The package management system cannot be identified.


```

At this point I go to thread [http://ubuntuforums.org/showthread.php?t=1475336](http://ubuntuforums.org/showthread.php?t=1475336)

Which details to hack the install script and force it to ignore the architecture. (The weird thing is though, that the thread says this hack is for 64bit systems and uname -m returns i686 for me, so definitely a 32 bit system. I had to hack the printer installs cript too, but once I did that went fine and works a treat. 

AHHHH - found the problem 

when I followed the hack exactly and edited out the comments it told me too, leaving only "** C_system="deb"** 

then I got the following errors

```

[B]scangearmp-mg6200series-1.80-1-deb$ sudo ./install.sh
./install.sh: line 354: [: =: unary operator expected
==================================================

ScanGear MP
Version 1.80
Copyright CANON INC. 2007-2011
All Rights Reserved.

==================================================
./install.sh: line 228: [: =: unary operator expected
./install.sh: line 432: [: too many arguments
./install.sh: line 439: [: =: unary operator expected
./install.sh: line 432: [: too many arguments
./install.sh: line 439: [: =: unary operator expected
./install.sh: line 460: [: =: unary operator expected
An error occurred. A necessary package could not be found in the proper location.
[/B]
```

BUT - I thought about it, and included the next line in the install script which is **C_arch32="i386"**

and Bingo it installed, and works fine. 

So thank you, because in answering this I went back and ran over exactly what I did step by step to give you the answers, and suddenly found the solution. 

So once again thanks, problem solved

---

### Post by pdc on 2012-12-03
that's great;

the usual explanation for 

> An error occurred. The package management system cannot be identified.

......is that it is finding some trace of rpm on  your system, as well as .deb packages........I don't know if that is true for you:

What I was trying to say was...........

install.sh tells the system to install the appropriate COMMON and then SPECIFIC package ........

.......another way.......is for you....knowing it is 32bit.......to just choose the COMMON and then the SPECIFIC and install them yourself.. that's all the script does.........

........glad all is working and enjoy .....

---

