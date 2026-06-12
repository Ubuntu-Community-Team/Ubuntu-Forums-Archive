---
title: "How to install gtk+ and seeking opinion on flat-bed scanner"
date: 2018-05-20
forum: General Help
---

### Post by satimis on 2018-05-20
Hi all,

Ubuntu 16.04 desktop

I need to install iscan_2.10.0-1.tar.gz to operate my old Epson Perfection 3490 Photo flat-bed scanner for scanning color film negatives.  The said scanner is still working without problem scanning color photos and documents running "Simple Scan"

Performed following steps;

&#10219; tar -xzf iscan_2.10.0-1.tar.gz
&#10219; cd iscan_2.10.0/
&#10219;./configure```

....
checking for GTK... configure: error: Package requirements (gtk+) were not met:
No package 'gtk+' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

&#10219; dpkg -l | grep libgtk```

ii  libgtk-3-0:amd64                            3.18.9-1ubuntu3.3                            amd64        GTK+ graphical user interface library
ii  libgtk-3-bin                                3.18.9-1ubuntu3.3                            amd64        programs for the GTK+ graphical user interface library
ii  libgtk-3-common                             3.18.9-1ubuntu3.3                            all          common files for the GTK+ graphical user interface library
ii  libgtk-3-dev:amd64                          3.18.9-1ubuntu3.3                            amd64        development files for the GTK+ library
ii  libgtk2-perl                                2:1.2498-1                                   amd64        Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0:amd64                           2.24.30-1ubuntu1.16.04.2                     amd64        GTK+ graphical user interface library
ii  libgtk2.0-bin                               2.24.30-1ubuntu1.16.04.2                     amd64        programs for the GTK+ graphical user interface library
ii  libgtk2.0-common                            2.24.30-1ubuntu1.16.04.2                     all          common files for the GTK+ graphical user interface library
ii  libgtkglext1:amd64                          1.2.0-3.2fakesync1ubuntu1                    amd64        OpenGL Extension to GTK+ (shared libraries)
ii  libgtkmm-2.4-1v5:amd64                      1:2.24.4-2                                   amd64        C++ wrappers for GTK+ (shared libraries)
ii  libgtkmm-3.0-1v5:amd64                      3.18.0-1                                     amd64        C++ wrappers for GTK+ (shared libraries)
ii  libgtksourceview-3.0-1:amd64                3.18.2-1                                     amd64        shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview-3.0-common                 3.18.2-1                                     all          common files for the GTK+ syntax highlighting widget
ii  libgtkspell0                                2.0.16-1.1ubuntu1                            amd64        a spell-checking addon for GTK's TextView widget
ii  libgtkspell3-3-0:amd64                      3.0.7-2                                      amd64        spell-checking addon for GTK+'s TextView widget

```

Please advise which package shall I install and how to install it?

Thanks in advance.

Besides if my old Epson scanner is not suitable to scan color film negatives please advise me?  I'll purchase a Epson Perfection v370 flat-bed scanner.

Regards
satimis

---

### Post by Perfect Storm on 2018-05-20
Try with
```
sudo apt install libgtk-3-dev
```

That is it refer to gtk3 and not to gtk2.

---

### Post by steeldriver on 2018-05-20
Isn't it the other way around? the OP has `libgtk-3-dev:amd64` but needs `libgtk2.0-dev`

---

### Post by Perfect Storm on 2018-05-20
ya, sorry.

```
sudo apt install libgtk2.0-dev
```

---

### Post by satimis on 2018-05-20
Hi all,

Thanks for your advice.

Performed following steps;
&#10219; sudo apt install libgtk2.0-dev```

.....
Unpacking libgtk2.0-dev (2.24.30-1ubuntu1.16.04.2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up gir1.2-gtk-2.0 (2.24.30-1ubuntu1.16.04.2) ...
Setting up libxml2-utils (2.9.3+dfsg1-1ubuntu0.5) ...
Setting up libgtk2.0-dev (2.24.30-1ubuntu1.16.04.2) ...

```

&#10219; cd Downloads/iscan_2.10.0/iscan_2.10.0/
&#10219; ./configure```

....
...
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
```
&#10219; make```

.....
In file included from imgstream.cc:31:0:
imgstream.hh:46:18: fatal error: ltdl.h: No such file or directory
compilation terminated.
Makefile:353: recipe for target 'libimage_stream_la-imgstream.lo' failed
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1
make[2]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/lib'
Makefile:395: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0'
Makefile:310: recipe for target 'all' failed
make: *** [all] Error 2

```

'make" failed

Please advise.  Thanks

Regards
satimis

---

### Post by Perfect Storm on 2018-05-20
It may be:
```
sudo apt install libltdl-dev
```

---

### Post by satimis on 2018-05-20
Performed following steps;

&#10219; sudo apt install libltdl-dev```

.....
(Reading database ... 233234 files and directories currently installed.)
Preparing to unpack .../libltdl-dev_2.4.6-0.1_amd64.deb ...
Unpacking libltdl-dev:amd64 (2.4.6-0.1) ...
Selecting previously unselected package libtool.
Preparing to unpack .../libtool_2.4.6-0.1_all.deb ...
Unpacking libtool (2.4.6-0.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libltdl-dev:amd64 (2.4.6-0.1) ...
Setting up libtool (2.4.6-0.1) ...

```

&#10219; ./configure```

...
....
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```

&#10219; make```

.....
In file included from imgstream.hh:45:0,
                 from imgstream.cc:31:
/usr/include/dirent.h:379:12: note:   initializing argument 2 of 'int versionsort(const dirent**, const dirent**)'
 extern int versionsort (const struct dirent **__e1,
            ^
Makefile:353: recipe for target 'libimage_stream_la-imgstream.lo' failed
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1
make[2]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/lib'
Makefile:395: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0'
Makefile:310: recipe for target 'all' failed
make: *** [all] Error 2

```

Problem still remains

Regards
satimis

---

### Post by Perfect Storm on 2018-05-20
hmmm... it's trouble with libimage_stream_la-imgstream.lo

try:
```
sudo apt install libpng-dev libjpeg-dev
```

---

### Post by satimis on 2018-05-20
Again;

&#10219; sudo apt install libpng-dev libjpeg-dev```

....
....
Unpacking libjpeg-dev:amd64 (8c-2ubuntu8) ...
Setting up libjpeg-turbo8-dev:amd64 (1.4.2-0ubuntu3) ...
Setting up libjpeg8-dev:amd64 (8c-2ubuntu8) ...
Setting up libjpeg-dev:amd64 (8c-2ubuntu8) ...

```

&#10219; ./configure```

......
......
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```

&#10219; make```

...
...
Makefile:353: recipe for target 'libimage_stream_la-imgstream.lo' failed
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1
make[2]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/lib'
Makefile:395: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0'
Makefile:310: recipe for target 'all' failed
make: *** [all] Error 2

```

Still the same problem.

satimis

---

### Post by Perfect Storm on 2018-05-20
A google search, came across this: [https://answers.launchpad.net/ubuntu/+question/21695](https://answers.launchpad.net/ubuntu/+question/21695)

it suggest:
> (>= 5.0.42), libsane-dev, libltdl3-dev | libltdl7-dev, libgtk2.0-dev, libpng-dev, libjpeg-dev, libgimp2.0-dev, libtiff4-dev

it seems as the same problem you have. Why not use the buildin scanner app that comes with ubuntu?

---

### Post by steeldriver on 2018-05-20
The problem really is that you are trying to build > 10 year old code

You *might *be able to get it to build with

```

make clean
./configure 'CFLAGS=-fPIC' 'CXXFLAGS=-fpermissive'
make

```

Good luck

---

### Post by satimis on 2018-05-20
> **Artificial Intelligence said:**
>  - snip -
it seems as the same problem you have. Why not use the buildin scanner app that comes with ubuntu?
Whether you meant "Simple Scan"?

It can't scan film negative.  It scan photos and documents without problem.  I have old film negatives to work because the color of my old photos becomes yellow

Regards
satimis

---

### Post by Perfect Storm on 2018-05-20
Install "sane" and use gimp as a scanning tool.

In gimp go to file ---> create ---> xscanimage

---

### Post by satimis on 2018-05-20
> **steeldriver said:**
> The problem really is that you are trying to build > 10 year old code

You *might *be able to get it to build with

```

make clean
./configure 'CFLAGS=-fPIC' 'CXXFLAGS=-fpermissive'
make

```

Good luck
Thanks for your advice.

Performed following steps;
&#10219; make clean```

...
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/libltdl'
Making clean in include
make[1]: Entering directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/include'
rm -rf .libs _libs
rm -f *.lo
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/include'
Making clean in .
make[1]: Entering directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0'
rm -rf .libs _libs
rm -f *.lo
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0'

```

&#10219; ./configure 'CFLAGS=-fPIC' 'CXXFLAGS=-fpermissive'```

.....
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
```

&#10219; make```

../include/sane/sanei.h:89:23: fatal error: sane/sane.h: No such file or directory
compilation terminated.
Makefile:345: recipe for target 'libsanei_la-sanei_config.lo' failed
make[2]: *** [libsanei_la-sanei_config.lo] Error 1
make[2]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/sanei'
Makefile:395: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0'
Makefile:310: recipe for target 'all' failed
make: *** [all] Error 2

```

No luck.  Still fail.

Yes, this is an old scanner.  I only use it scanning documents and photos occasionally.  I can run Simple Scan to scan photos and documents without problem but I couldn't scan negative.  That is my reason to install Epson software.

I'm considering to purchase a new Epson Perfection V370 flat-bed scanner to work on my old color film negatives.

Regards
satimis

---

### Post by Perfect Storm on 2018-05-20
> ./include/sane/sanei.h:89:23: fatal error: sane/sane.h: No such file or directory

```
sudo apt install libsane-dev
```

---

### Post by satimis on 2018-05-20
> **Artificial Intelligence said:**
> Install "sane" and use gimp as a scanning tool.

In gimp go to file ---> create ---> xscanimage
sane already installed

&#10219; apt-cache policy sane```

sane:
  Installed: 1.0.14-11
  Candidate: 1.0.14-11
  Version table:
 *** 1.0.14-11 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Start GIMP

File -> Create -> xscanimage -> Device Dialogue ...
```

Fail to open device 'snapscan:libuse:002:009'; Error during device I/O
-> OK

```

Very strange.  GIMP can't detect Epson scanner?

satimis

---

### Post by satimis on 2018-05-20
Hi  Artificial Intelligence,

Finally I made GIMP to work scanning the film negative.

Performed;
1) Power off and on Epson scanner
2) File -> Create -> xscanimage -> Device Dialogue ...
to start "snapscan:libusb:002:007" window

Scan source [Transparency Adapter]
Bit depth [bit] [8]
[check] Quality calibration
[389x1913:2.1 MB]
-> Scan

Four film negatives scanned and save the file on /Document/ as test01.xcf

How to view/edit the file, on GIMP or on Darktable?

Regards
satimis

---

### Post by Perfect Storm on 2018-05-20
You may export the file as .png for that.

File ---> Export As
then change the file name to end with .png

---

### Post by satimis on 2018-05-20
> **Artificial Intelligence said:**
> ```
sudo apt install libsane-dev
```
Performed following steps;

&#10219; sudo apt install libsane-dev
&#10219; cd Downloads/iscan_2.10.0/iscan-2.10.0/
&#10219; make clean```

....
test -z "libltdlc.la" || rm -f libltdlc.la
rm -f "./so_locations"
rm -f *.o
rm -f *.lo
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/libltdl'
Making clean in include
make[1]: Entering directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/include'
rm -rf .libs _libs
rm -f *.lo
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/include'
Making clean in .
make[1]: Entering directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0'
rm -rf .libs _libs
rm -f *.lo
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0'

```

&#10219; ./configure```

.....
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```

&#10219; make```

....
Makefile:353: recipe for target 'libimage_stream_la-imgstream.lo' failed
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1
make[2]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0/lib'
Makefile:395: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/satimis/Downloads/iscan_2.10.0/iscan-2.10.0'
Makefile:310: recipe for target 'all' failed
make: *** [all] Error 2

```

Still the same.

Should I can manage GIMP scanning plug-in, I don't need Epson scanning software.  However the latter offers more option.  Please see attached photo : "screenshot_epson_scan.png".  Besides I can adjust the scanned film negative on Darktable, which is running here, provided if a quality scanning can be made on GIMP plug-in.

For your information .xcf can be converted to .png with "Convert" command of ImageMagick.  Now I can view the 4 scanned film negatives on Imageviewer.  They are not very clear.  I'll try again later scanning on 16/24 bit colour.

How to convert bit to resolution?  I have been googling a while without luck.

Thanks

Regards
satimis

---

