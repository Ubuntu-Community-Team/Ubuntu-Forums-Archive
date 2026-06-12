---
title: "Googleearth-package 0.2.0 fix"
date: 2007-11-03
forum: General Help
---

### Post by dcstar on 2007-11-03
The current package in the Ubuntu Multiverse repository doesn't work because it points to an outdated URL to fetch the latest Googleearth Linux file.

If you want to use it (it creates a .deb package that you can use to install GoogleEarth on your system), then you have to first install **googleearth-package** and then manually edit the file:

```
gksudo gedit /usr/bin/make-googleearth-package
```

with the following correct URL: **"http://dl.google.com/earth/client/current/GoogleEarthLinux.bin"** (remove the "" characters, they are there so the full string is displayed correctly)

Save the file, then run it with:

```
sudo make-googleearth-package
```

When completed, you should have a **googleearth........deb** file (the "...." will be the version created) that you can now install like any other package:

```
sudo dpkg -i googleearth*deb
```

After successful installation, there should be: **Applications-Internet-Google Earth**

**Please note that you need working 3D video drivers for this to run.**


For Ubuntu **AMD-64** users you need to do the following:

```
gksudo gedit /usr/bin/make-googleearth-package
``` and replace all the "i386" entries with "amd64" - this will now build a amd64 .deb that will install (you will have previously changed the URL to the above).

```
sudo make-googleearth-package --force
```

```
sudo dpkg -i googleearth*deb
```

---

### Post by Rob-e on 2007-11-10
thanks, i got this working, except the url  http: //dl.google.com/earth/client/current/GoogleEarthLi(SPACE HERE)nux.bin  also has a space in linux as shown and i had to add --force to make it work because the version was unrecognized, but other than that, it works well, thanks!

---

### Post by finger51 on 2007-11-10
tried to get this going- from Apps\Internet does nothing. doesn't show up in 'ps'. from CLI I get 
```

$ googleearth 
/usr/bin/googleearth: line 4: /usr/lib/googleearth/googleearth-bin: No such file or directory
/usr/bin/googleearth: line 4: exec: /usr/lib/googleearth/googleearth-bin: cannot execute: No such file or directory

```

I'm on amd64 but followed the instructions for editing the make package. seemed to go without issue. dpkg -i didn't protest at all. It looked like a clean install.

?stump'd?

---

### Post by eabadham on 2008-01-15
Hi,
I am running amd64 as well and it looks like a clean install but when I then click on the google earth icon nothing happens..

My last code in terminal was:
laptop:~$ sudo dpkg -i googleearth*deb
Selecting previously deselected package googleearth.
(Reading database ... 105142 files and directories currently installed.)
Unpacking googleearth (from googleearth_4.2.205.5730+0.2.0-1_amd64.deb) ...
Setting up googleearth (4.2.205.5730+0.2.0-1) ...

-laptop:~$ 

Any ideas about what could be wrong?
Thanks for your help!

---

### Post by dcstar on 2008-01-15
> **eabadham said:**
> Hi,
I am running amd64 as well and it looks like a clean install but when I then click on the google earth icon nothing happens..
.........
Any ideas about what could be wrong?
Thanks for your help!

Open a terminal, and enter:
```
googleearth
```
and see if there are any relevant messages.

---

### Post by narf y akim on 2008-01-30
> **dcstar said:**
> The current package in the Ubuntu Multiverse repository doesn't work because it points to an outdated URL to fetch the latest Googleearth Linux file.

If you want to use it (it creates a .deb package that you can use to install GoogleEarth on your system), then you have to first install **googleearth-package** and then manually edit the file:

```
gksudo gedit /usr/bin/make-googleearth-package
```

with the following correct URL: **http: //dl.google.com/earth/client/current/GoogleEarthLinux.bin** (remove the space after the http:, and the other one that the forum seems to put in )

Save the file, then run it with:

```
sudo make-googleearth-package
```

When completed, you should have a **googleearth........deb** file (the "...." will be the version created) that you can now install like any other package:

```
sudo dpkg -i googleearth*deb
```

After successful installation, there should be: **Applications-Internet-Google Earth**

**Please note that you need working 3D video drivers for this to run.**


For Ubuntu **AMD-64** users you need to do the following:

```
gksudo gedit /usr/bin/make-googleearth-package
``` and replace all the "i386" entries with "amd64" - this will now build a amd64 .deb that will install (you will have previously changed the URL to the above).

```
sudo make-googleearth-package --force
```

```
sudo dpkg -i googleearth*deb
```
Hello,
I followed your instructions, but I have a problem, probably with a simple answer, because I'm new in Linux. The problem is:
After the command:
**sudo make-googleearth-package**
I got an archive named **GoogleEarthLinux.bin** and a message about it can't determine the version, and use **--force** .
After the command:
**sudo dpkg -i googleearth*deb**
or
**sudo dpkg -i googleearth*deb --force**
I get this:
[B]dpkg: error processing googleearth*deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing --force (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 googleearth*deb
 --force[/B]
Any idea?

---

### Post by dcstar on 2008-01-31
> **narf y akim said:**
> Hello,
I followed your instructions, but I have a problem, probably with a simple answer, because I'm new in Linux. The problem is:
After the command:
**sudo make-googleearth-package**
I got an archive named **GoogleEarthLinux.bin** and a message about it can't determine the version, and use **--force** .
After the command:
**sudo dpkg -i googleearth*deb**
or
**sudo dpkg -i googleearth*deb --force**
I get this:
[B]dpkg: error processing googleearth*deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing --force (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 googleearth*deb
 --force[/B]
Any idea?

If the message tells you to use **--force**, then use it :

```
sudo make-googleearth-package --force
```

---

### Post by narf y akim on 2008-01-31
Thanks very much! It works great! 

Only for curiosity, could you explain me a little bit more about this? After the install I have two archives in my home folder of 22 Mb each. One is GoogleEarthLinux.bin and the other is the package googleearth_4.2.205.5730+0.2.0-1_i386.deb. 

Do I have to conserve this files in my home folder? I mean, does the program need this files to run or can I delete them?

Thanks for your time!

---

### Post by andrewabc on 2008-02-11
I got an error while trying this

```
Google Earth for GNU/Linux 4.2.205.5730
Supported Google Earth version: 4.2.205.5730
./
./README.linux
./bin/
./bin/googleearth
./googleearth-icon.png
./googleearth.xpm
./linux/
./linux/xdg/
./linux/xdg/xdg-desktop-icon
./linux/xdg/xdg-desktop-menu
./linux/xdg/xdg-mime
./postinstall.sh
./preuninstall.sh
./setup.data/
./setup.data/bin/
./setup.data/bin/Linux/
./setup.data/bin/Linux/x86/
./setup.data/bin/Linux/x86/setup.gtk
./setup.data/bin/Linux/x86/setup.gtk2
./setup.data/bin/Linux/x86/uninstall
./setup.data/bin/Linux/amd64
./setup.data/bin/Linux/x86_64
./setup.data/bin/NetBSD
./setup.data/bin/OpenBSD
./setup.data/bin/FreeBSD
./setup.data/config.sh
./setup.data/locale/
./setup.data/locale/de/
./setup.data/locale/de/LC_MESSAGES/
./setup.data/locale/de/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/de/LC_MESSAGES/setup.mo
./setup.data/locale/es/
./setup.data/locale/es/LC_MESSAGES/
./setup.data/locale/es/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/es/LC_MESSAGES/setup.mo
./setup.data/locale/fr/
./setup.data/locale/fr/LC_MESSAGES/
./setup.data/locale/fr/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/fr/LC_MESSAGES/setup.mo
./setup.data/locale/it/
./setup.data/locale/it/LC_MESSAGES/
./setup.data/locale/it/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/it/LC_MESSAGES/setup.mo
./setup.data/locale/nl/
./setup.data/locale/nl/LC_MESSAGES/
./setup.data/locale/nl/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/nl/LC_MESSAGES/setup.mo
./setup.data/locale/ru/
./setup.data/locale/ru/LC_MESSAGES/
./setup.data/locale/ru/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/ru/LC_MESSAGES/setup.mo
./setup.data/locale/sv/
./setup.data/locale/sv/LC_MESSAGES/
./setup.data/locale/sv/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/sv/LC_MESSAGES/setup.mo
./setup.data/setup.glade
./setup.data/setup.gtk2.glade
./setup.data/setup.xml
./setup.data/splash.xpm
./setup.sh
./googleearth-linux-x86.tar
./googleearth-data.tar
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
dpkg-shlibdeps: error: cannot read control file debian/control: No such file or directory
Package: googleearth
Version: 4.2.205.5730+0.4.3-1
Section: non-free/science
Priority: optional
Maintainer:  <>
Architecture: i386
Depends: ttf-dejavu | ttf-bitstream-vera | msttcorefonts,  
Description: Google Earth, a 3D map/planet viewer
 Package built with googleearth-package.
dpkg-deb: parse error, in file `/home/andrew/googleearth-deb/DEBIAN/control' near line 7 package `googleearth':
 `Depends' field, missing package name, or garbage where package name expected
Success!

```
Won't let me do that next command
> andrew@andrew-desktop:~$ sudo dpkg -i googleearth*deb
dpkg: error processing googleearth*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 googleearth*deb

Using 32bit hardy.

EDIT:
Going to download it from google website and install from there.
EDIT:
Well that didn't work. Nothing will open the .bin file...

EDIT:
I used
```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```
And it works.

---

### Post by dcstar on 2008-02-24
> **narf y akim said:**
> Thanks very much! It works great! 

Only for curiosity, could you explain me a little bit more about this? After the install I have two archives in my home folder of 22 Mb each. One is GoogleEarthLinux.bin and the other is the package googleearth_4.2.205.5730+0.2.0-1_i386.deb. 

Do I have to conserve this files in my home folder? I mean, does the program need this files to run or can I delete them?

Thanks for your time!

The .bin file is the generic Linux version downloaded from Google Earth, the .deb is the packaged version for Ubuntu containing the .bin program.

You can delete both after install (or keep the .deb if you think you may need to install it again).

---

### Post by CaptainCabinet on 2008-02-25
Thank you so much for this I've been wanting google earth on Ubuntu for ages. :)

---

### Post by Norrbagge on 2008-03-05
Great "howto", worked like a charm. Except one small thingie that i had to change. It was the adress that you copy into the "googleearth-package" file.

The adress that i had to copy inn, to make it work is:
http ://dl.google.com/earth/client/current/GoogleEarthLinux.bin

The adress i copied inn was with NO spaces...

---

### Post by sadohert on 2008-04-20
This worked perfectly for me.  I'm on an amd64 (Gutsy).  I modified the url in the make-googleearth-package script, ran the script (initially had a problem because it was run from a directory that had a space in its name.  Changed the directory name, ran it, and I was good to go after installing the *.deb.

Thanks.

---

### Post by dcstar on 2008-04-23
> **sadohert said:**
> This worked perfectly for me.  I'm on an amd64 (Gutsy).  I modified the url in the make-googleearth-package script, ran the script (initially had a problem because it was run from a directory that had a space in its name.  Changed the directory name, ran it, and I was good to go after installing the *.deb.

Thanks.

I had the "space" issue highlighted because the forum engine causes it, apparently not highlighted enough!

Anyway, I have changed things so the download URL should now be ok.

---

### Post by roswald on 2008-04-23
Hi, Everyone 
I installed Google Earth thru Synaptic. The install seemed to go ok and there is a google earth icon under Aplications> internet. It appears to be eye candy only because it dont work!! any ideas??

---

### Post by dcstar on 2008-04-25
> **roswald said:**
> Hi, Everyone 
I installed Google Earth thru Synaptic. The install seemed to go ok and there is a google earth icon under Aplications> internet. It appears to be eye candy only because it dont work!! any ideas??

Open a terminal and enter **googleearth **to see what messages are listed, and then create a new thread (or do a search) with the message.

---

### Post by qhaz on 2008-04-25
I'm getting gobs of error messages when running 
sudo make-googleearth-package --force

any ideas?

./setup.sh
./googleearth-linux-x86.tar
./googleearth-data.tar
dpkg-shlibdeps: warning: shared libs info file `shlibs.local' line 12: bad line `libcollada-1.4.so'
dpkg-shlibdeps: warning: shared libs info file `shlibs.local' line 12: bad line `libcollada-1.4.so'
dpkg-shlibdeps: warning: shared libs info file `shlibs.local' line 12: bad line `libcollada-1.4.so'
dpkg-shlibdeps: failure: couldn't find library libQt3Support.so.4 needed by ../usr/lib/googleearth/libmath.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.

---

### Post by dccrens on 2008-04-26
Well. I have tried installing from the google website using "sh withlatestgoogledownload.bin" and I have tried using the google packager. Both install but when I run googleearth I get the google earth application but no "earth" diplayed. Nothing but the Starfield is displayed and most options/menues are greyed out. Anyone have any suggestions? I have tried installing both as root using sudo and as a user to my home directory. I have also tried removing the ~/.googleearth directory but I get the same thing...

---

### Post by qhaz on 2008-04-26
. . . I'm in the same boat as dccrens.  I'm nearly googled out trying to find ways around getting this to go.  Currently don't seem to be able to compile googleearth-package (see previous entry).  Both the google site binary and the synaptic listed googele give me the same result . . . googleearth starts, gives and error message about maybe being blocked from /opt/googleearth . .  . and a star lit sky . . . no earth.
I'm running Hardy on a amd64 machine.  Anyone else experiencing this?  Any suggestions?

cheers

---

### Post by dccrens on 2008-04-27
Post number 5 at this thread worked for me. 

[http://ubuntuforums.org/showthread.php?t=756960&highlight=googleearth]("http://ubuntuforums.org/showthread.php?t=756960&highlight=googleearth")

---

