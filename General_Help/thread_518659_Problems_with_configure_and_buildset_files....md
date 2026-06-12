---
title: "Problems with configure and buildset files..."
date: 2007-08-06
forum: General Help
---

### Post by carlnz on 2007-08-06
Hey there,

I've just recently installed Kubuntu Feisty on my computer, and while generally everything has been great, there have been a few niggly problems, no doubt caused by my own incompetence. As I just can't seem to resolve them, I thought I'd ask for some help...

I've been trying to install a few programs, to no avail thus far! I got GCC installed, then the x-libraries, but now this error is what I am confronted with:

(This is whilst attempting to install the QtCurve theme, btw, but the same message is occuring for everything I'm trying to install)

> checking for libjpeg6b... 
no
checking for libjpeg... 
no
configure: WARNING: libjpeg not found. disable JPEG support.
checking for perl... 
/usr/bin/perl
checking for Qt... 
configure: error: Qt (>= Qt 3.3) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

I've installed the most recent libjpeg packages I can find, but the message persists. What do I need to do here?


The other problem I've been running in to is in regards to icon themes, most of which use buildsets.

In the case of one example, this is what I receive:

> This script builds an installable KDE iconset using bash and convert.
Change what you want, add additional sizes, whatever... :)

Checking for bzip2... found /bin/bzip2
Checking for tar...  found /bin/tar
Checking for convert...  found /usr/bin/convert

Dependencies met - this script is using:
                /bin/bzip2 as compressor
                /bin/tar as tar path
                /usr/bin/convert as convert path

Ready to go!  Converting all icons! (about 15 seconds on an Athlon 64)

convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
convert: unable to open file `*': No such file or directory.
cp: cannot stat `index.desktop': No such file or directory
cp: cannot stat `README': No such file or directory
cp: cannot stat `buildset': No such file or directory
cp: cannot stat `GPL': No such file or directory
cp: cannot stat `CHANGELOG': No such file or directory

Done with conversions.
Tarring and compressing.

The SnowIsh-1.3 icon set has been built.  Use kcontrol to install the icon set.

4.0K SnowIsh-1.3.tar.bz2

Removing all temporary directories...

All done. ;)


But, while a file is created, it is not a valid theme file, as obviously none of the icons are being converted.

And in another - OS-L - I receive one of two messages:

> Select a kmenu icon from the following choices:

        kmenu_apple,kmenu_appleb,kmenu_apple-gball_blue,kmenu_apple-gball_red,kmenu_baghira,kmenu_mdk,kmenu_mdk2, kmenu_redhat,kmenu_suse,kmenu_tux_apple,kmenu_tux,kmenu_happy, and enter it now (case sensitive - dont put (.png) at the end of your selection): kmenu_apple

Using the kmenu_apple.png icon as your kmenu icon.
Invalid selection (kmenu_apple), the kmenu_apple icon was not found in the .128x128/apps/ directory....exiting...



Or, when I attempt to navigate through to the buildset through a shell rather than straight from the command line, I receive this:

> carl@ubuntu:~$ cd /home/carl/Themes/OS-L-IconSet-Buildkit/
carl@ubuntu:~/Themes/OS-L-IconSet-Buildkit$ sh buildset
buildset: 33: Syntax error: "(" unexpected


Can anyone please help me?

Cheers,
Carl

---

### Post by nitro_n2o on 2007-08-06
I don't use KDE but one of your errors suggest that you should get qt4-dev-tools and read the README file and follow the instructions.. maybe you are not in the right directory of forgot some step

---

### Post by carlnz on 2007-08-06
I've installed qt4-dev-tools and to no avail. And I've scoured the readmes (not difficult, as they're extremely short). I'm still having no luck :(

---

### Post by txHarleyMan on 2008-01-13
Install Imagemagic

---

