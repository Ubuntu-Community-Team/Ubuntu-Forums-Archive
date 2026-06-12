---
title: "APT-GET question"
date: 2013-06-14
forum: General Help
---

### Post by Mopar1973Man on 2013-06-14
Q: Is there a way to APT-GET download a entire program with dependencies so you can burn them to a disk for later installation like on a computer without Internet connections? I would hate like hell to try and help someone out with a laptop that doesn't have Internet connection all the time try and install a program and be short the dependencies. So how would you do that?

---

### Post by localhost8080 on 2013-06-14
check out this:
[http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline](http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline)

it suggests keryx. its like synaptic but for downloading a package and its dependancies.

there are lots of other great answers on the linked page too :)

---

### Post by HiImTye on 2013-06-14
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
synaptic is the easist. load a live CD, install synaptic, then select your program, and create a download script. it'll save a bash script with the addresses of all the packages you need.

---

### Post by deadflowr on 2013-06-14
[Aptoncd]("http://packages.ubuntu.com/search?keywords=aptoncd")

---

### Post by Mopar1973Man on 2013-06-17
After reviewing what I've got for answers here I like the keryx the most but can't seem to figure out how to install or even start it. There is a serious bug issue with .DEB file of keryx and the portable version does nothing. 
[https://answers.launchpad.net/keryx/+question/203574](https://answers.launchpad.net/keryx/+question/203574)

APTonCD seems to just backup the APT cache folder not allowing for picking a choosing of what you want to install. (Didn't actually install and try). 

As for the Synaptic doesn't work because the second machine will most likely be without Internet 90% of the time so the package and dependencies all have to be on the same disc/media.

---

### Post by Mopar1973Man on 2013-06-17
Ok. Now I've tried the APTonCD and it doesn't get the dependencies if the software is already installed on the computer so you'll still be no better than "apt-get -download" command. I can see how this would work excellent with a fresh install but I tried like Gimp and Conky and it just packaged only the core package but no dependencies.

---

### Post by HiImTye on 2013-06-17
you use Synaptic to generate a download script by

[LIST=1]
[*]mark all packages you want (Synaptic will select any dependencies) 
[*]File > Generate Download Script 
[*]save the file in the folder you want them downloaded to
[/LIST]
this will make a script like the following (this one is after marking 'wine' for iinstallation
```
#!/bin/sh
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libu/libusb/libusb-0.1-4_0.1.12-23_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/d/db/libdb5.1_5.1.29-5ubuntu2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libtinfo5_5.9-10ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/n/ncurses/libncurses5_5.9-10ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libroken18-heimdal_1.6~git20120403+dfsg1-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libasn1-8-heimdal_1.6~git20120403+dfsg1-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gettext/libasprintf0c2_0.18.1.1-9ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libhcrypto4-heimdal_1.6~git20120403+dfsg1-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libheimbase1-heimdal_1.6~git20120403+dfsg1-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libwind0-heimdal_1.6~git20120403+dfsg1-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libhx509-5-heimdal_1.6~git20120403+dfsg1-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libkrb5-26-heimdal_1.6~git20120403+dfsg1-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libheimntlm0-heimdal_1.6~git20120403+dfsg1-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libgssapi3-heimdal_1.6~git20120403+dfsg1-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-2_2.1.25.dfsg1-5_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.31-1ubuntu2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libu/libusbx/libusb-1.0-0_1.0.12-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/f/fonts-horai-umefont/fonts-horai-umefont_442-1_all.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libc/libcroco/libcroco3_0.6.6-1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libe/libexif/libexif12_0.6.20-3_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxpm/libxpm4_3.5.10-1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-6ubuntu3_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libu/libunistring/libunistring0_0.9.3-5build1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gettext/libgettextpo0_0.18.1.1-9ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/g/giflib/libgif4_4.1.6-9.1ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/libgomp1_4.7.2-2ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libltdl7_2.4.2-1ubuntu2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.4.14-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.4.14-2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gpm/libgpm2_1.20.4-6_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libi/libieee1284/libieee1284-3_0.2.11-10build2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/m/mpg123/libmpg123-0_1.14.2+svn20120622-1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.6.6-3ubuntu5_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/s/samba/libnss-winbind_3.6.6-3ubuntu5_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/s/samba/libpam-winbind_3.6.6-3ubuntu5_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/v/v4l-utils/libv4lconvert0_0.8.8-2ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/v/v4l-utils/libv4l-0_0.8.8-2ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/libsane_1.0.23-0ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxcomposite/libxcomposite1_0.4.3-2build2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxcursor/libxcursor1_1.1.13-1ubuntu0.12.10.1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxinerama/libxinerama1_1.1.2-1ubuntu0.12.10.1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxrandr/libxrandr2_1.4.0-1ubuntu0.1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.26-14ubuntu0.1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst_2.2.14p2-5ubuntu4_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian2_2.2.14p2-5ubuntu4_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/f/fonts-horai-umefont/ttf-umefont_442-1_all.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/w/wine-gecko1.4/wine-gecko1.4_1.4.0-0ubuntu2_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/w/wine-gecko1.4/wine-gecko1.4_1.4.0-0ubuntu2_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/wine1.4-common_1.4.1-0ubuntu1_all.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/wine1.4-amd64_1.4.1-0ubuntu1_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libglu/libglu1-mesa_9.0.0-0ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/o/openal-soft/libopenal1_1.14-4ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/wine1.4-i386_1.4.1-0ubuntu1_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/wine1.4_1.4.1-0ubuntu1_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/winetricks/winetricks_0.0+20120912_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/i/isdnutils/libcapi20-3_3.12.20071127-0ubuntu11_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.25.dfsg1-5_i386.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/f/fonts-unfonts-core/fonts-unfonts-core_1.0.3.is.1.0.2-080608-5ubuntu2_all.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/i/icoutils/icoutils_0.30.0-1_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-l10n_2.4.14-2_all.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/f/fonts-unfonts-core/ttf-unfonts-core_1.0.3.is.1.0.2-080608-5ubuntu2_all.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.14p2-5ubuntu4_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.6.1-0ubuntu11.4_amd64.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.9-0ubuntu1_all.deb
wget -c http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/wine_1.4.1-0ubuntu1_amd64.
```
next you move to the folder you want to put the files in and run the script. it will save the files in the folder.
in the terminal
```
cd /path/to/folder/
./whateverYouNamedTheScript
```
otherwise, navigate to the folder in Nautilus (Files), or whatever file manager you use, and open it.

you use a liveCD so that you get all the packages that you wouldn't if you already had some installed.[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

