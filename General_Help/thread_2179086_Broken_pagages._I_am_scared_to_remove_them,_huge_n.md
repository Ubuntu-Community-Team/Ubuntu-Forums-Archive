---
title: "Broken pagages. I am scared to remove them, huge number of dependecies"
date: 2013-10-06
forum: General Help
---

### Post by dan45 on 2013-10-06
Hi,

I have been trying for a while to install packages so that I could just transfer files to my nexus 4. No success. This time I also managed to screw up the system. There are broken pakages after I followed some command line apt-get instructions.

I found the ones that create problems using Synaptic, and there is not much else I can do apart from removing them. They are:
libusb-0.1-4
libusb-0.1-4:i386

A suggestion from the terminal, when I was trying to install something else and it couldn't proceed, was the following ( it goes on a bit in a loop... )

dan@dan:~$ sudo apt-get install mtp-tools mtpfs
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
```
 libusb-0.1-4 : Breaks: libusb-0.1-4:i386 (!= 2:0.1.12-20) but 2:0.1.12-23.2 is to be installed
 libusb-0.1-4:i386 : Breaks: libusb-0.1-4 (!= 2:0.1.12-23.2) but 2:0.1.12-20 is to be installed
 mtpfs : Depends: fuse-utils but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dan@dan:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopenal1:i386 bluez-alsa:i386 libsdl-ttf2.0-0:i386 libgconf-2-4:i386
  libatk1.0-0:i386 libstdc++5:i386 libpam-winbind ttf-umefont
  libxcomposite1:i386 libgail18:i386 libldap-2.4-2:i386 libv4l-0:i386
  gnome-exe-thumbnailer libqt4-qt3support:i386 libroken18-heimdal:i386
  libunistring0 libunistring0:i386 libcupsimage2:i386 libidn11:i386
  libnss3:i386 libcaca0:i386 gtk2-engines:i386 libgudev-1.0-0:i386
  libcairo-gobject2:i386 libavc1394-0:i386 libbz2-1.0:i386 libaio1:i386
  odbcinst1debian2:i386 libqt4-test:i386 libqt4-designer:i386
  libsdl-mixer1.2:i386 libcap2:i386 libproxy1:i386 ibus-gtk:i386
  libdbus-glib-1-2:i386 libtdb1:i386 libasn1-8-heimdal:i386 libspeex1:i386
  libxslt1.1:i386 libgomp1:i386 libcapi20-3 libcapi20-3:i386
  libibus-1.0-0:i386 libcairo2:i386 libgssapi3-heimdal:i386
  libcanberra-gtk-module:i386 libcanberra0:i386 gtk2-engines-murrine:i386
  libwavpack1:i386 libqt4-opengl:i386 libsoup-gnome2.4-1:i386
  libv4lconvert0:i386 gstreamer0.10-plugins-good:i386 librsvg2-common:i386
  libncursesw5:i386 libiec61883-0:i386 libgdk-pixbuf2.0-0:i386
  libsdl-image1.2:i386 wine-gecko1.4 wine-gecko1.4:i386 libwind0-heimdal:i386
  libpixman-1-0:i386 libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386
  winetricks libcurl3:i386 libxinerama1:i386 libesd0:i386 libmikmod2:i386
  libgif4:i386 libxft2:i386 libcroco3:i386 libpulse-mainloop-glib0:i386
  libaa1:i386 libieee1284-3:i386 libao4:i386 libxmu6:i386
  libcanberra-gtk0:i386 libvorbisfile3:i386 libxpm4:i386 libqt4-svg:i386
  libgail-common:i386 libhcrypto4-heimdal:i386 libraw1394-11:i386
  libnspr4:i386 libshout3:i386 libdv4:i386 libhx509-5-heimdal:i386
  gstreamer0.10-x:i386 libgettextpo0 libgettextpo0:i386 libgd2-xpm:i386
  libheimbase1-heimdal:i386 libsdl-net1.2:i386 libjasper1:i386
  libgnome-keyring0:i386 libxtst6:i386 gtk2-engines-pixbuf:i386
  libtag1c2a:i386 librsvg2-2:i386 ttf-unfonts-core libmpg123-0
  libmpg123-0:i386 libssl0.9.8:i386 libmad0:i386 libsasl2-2:i386 libdb5.1:i386
  gtk2-engines-oxygen:i386 xaw3dg:i386 libpango1.0-0:i386
  libheimntlm0-heimdal:i386 libpulsedsp:i386 winbind libxcb-render0:i386
  libodbc1:i386 libexif12:i386 libqt4-scripttools:i386 librtmp0:i386
  libxp6:i386 libxcursor1:i386 libxcb-shm0:i386 libsasl2-modules:i386
  libxrandr2:i386 libgtk2.0-0:i386 libltdl7:i386 libkrb5-26-heimdal:i386
  glib-networking:i386 libsoup2.4-1:i386 libtag1-vanilla:i386
  libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  ia32-libs ia32-libs-multiarch:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libsane:i386 libusb-0.1-4:i386 playonlinux wine wine1.4 wine1.4-amd64
  wine1.4-common wine1.4-i386:i386
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 232 MB disk space will be freed.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libusb-0.1-4
dan@dan:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopenal1:i386 bluez-alsa:i386 libsdl-ttf2.0-0:i386 libgconf-2-4:i386
  libatk1.0-0:i386 libstdc++5:i386 libpam-winbind ttf-umefont
  libxcomposite1:i386 libgail18:i386 libldap-2.4-2:i386 libv4l-0:i386
  gnome-exe-thumbnailer libqt4-qt3support:i386 libroken18-heimdal:i386
  libunistring0 libunistring0:i386 libcupsimage2:i386 libidn11:i386
  libnss3:i386 libcaca0:i386 gtk2-engines:i386 libgudev-1.0-0:i386
  libcairo-gobject2:i386 libavc1394-0:i386 libbz2-1.0:i386 libaio1:i386
  odbcinst1debian2:i386 libqt4-test:i386 libqt4-designer:i386
  libsdl-mixer1.2:i386 libcap2:i386 libproxy1:i386 ibus-gtk:i386
  libdbus-glib-1-2:i386 libtdb1:i386 libasn1-8-heimdal:i386 libspeex1:i386
  libxslt1.1:i386 libgomp1:i386 libcapi20-3 libcapi20-3:i386
  libibus-1.0-0:i386 libcairo2:i386 libgssapi3-heimdal:i386
  libcanberra-gtk-module:i386 libcanberra0:i386 gtk2-engines-murrine:i386
  libwavpack1:i386 libqt4-opengl:i386 libsoup-gnome2.4-1:i386
  libv4lconvert0:i386 gstreamer0.10-plugins-good:i386 librsvg2-common:i386
  libncursesw5:i386 libiec61883-0:i386 libgdk-pixbuf2.0-0:i386
  libsdl-image1.2:i386 wine-gecko1.4 wine-gecko1.4:i386 libwind0-heimdal:i386
  libpixman-1-0:i386 libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386
  winetricks libcurl3:i386 libxinerama1:i386 libesd0:i386 libmikmod2:i386
  libgif4:i386 libxft2:i386 libcroco3:i386 libpulse-mainloop-glib0:i386
  libaa1:i386 libieee1284-3:i386 libao4:i386 libxmu6:i386
  libcanberra-gtk0:i386 libvorbisfile3:i386 libxpm4:i386 libqt4-svg:i386
  libgail-common:i386 libhcrypto4-heimdal:i386 libraw1394-11:i386
  libnspr4:i386 libshout3:i386 libdv4:i386 libhx509-5-heimdal:i386
  gstreamer0.10-x:i386 libgettextpo0 libgettextpo0:i386 libgd2-xpm:i386
  libheimbase1-heimdal:i386 libsdl-net1.2:i386 libjasper1:i386
  libgnome-keyring0:i386 libxtst6:i386 gtk2-engines-pixbuf:i386
  libtag1c2a:i386 librsvg2-2:i386 ttf-unfonts-core libmpg123-0
  libmpg123-0:i386 libssl0.9.8:i386 libmad0:i386 libsasl2-2:i386 libdb5.1:i386
  gtk2-engines-oxygen:i386 xaw3dg:i386 libpango1.0-0:i386
  libheimntlm0-heimdal:i386 libpulsedsp:i386 winbind libxcb-render0:i386
  libodbc1:i386 libexif12:i386 libqt4-scripttools:i386 librtmp0:i386
  libxp6:i386 libxcursor1:i386 libxcb-shm0:i386 libsasl2-modules:i386
  libxrandr2:i386 libgtk2.0-0:i386 libltdl7:i386 libkrb5-26-heimdal:i386
  glib-networking:i386 libsoup2.4-1:i386 libtag1-vanilla:i386
  libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  ia32-libs ia32-libs-multiarch:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libsane:i386 libusb-0.1-4:i386 playonlinux wine wine1.4 wine1.4-amd64
  wine1.4-common wine1.4-i386:i386
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 232 MB disk space will be freed.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libusb-0.1-4
dan@dan:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dan@dan:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dan@dan:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 libusb-0.1-4 : Breaks: libusb-0.1-4:i386 (!= 2:0.1.12-20) but 2:0.1.12-23.2 is installed
 libusb-0.1-4:i386 : Breaks: libusb-0.1-4 (!= 2:0.1.12-23.2) but 2:0.1.12-20 is installed
E: Unmet dependencies. Try using -f.
dan@dan:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopenal1:i386 bluez-alsa:i386 libsdl-ttf2.0-0:i386 libgconf-2-4:i386
  libatk1.0-0:i386 libstdc++5:i386 libpam-winbind ttf-umefont
  libxcomposite1:i386 libgail18:i386 libldap-2.4-2:i386 libv4l-0:i386
  gnome-exe-thumbnailer libqt4-qt3support:i386 libroken18-heimdal:i386
  libunistring0 libunistring0:i386 libcupsimage2:i386 libidn11:i386
  libnss3:i386 libcaca0:i386 gtk2-engines:i386 libgudev-1.0-0:i386
  libcairo-gobject2:i386 libavc1394-0:i386 libbz2-1.0:i386 libaio1:i386
  odbcinst1debian2:i386 libqt4-test:i386 libqt4-designer:i386
  libsdl-mixer1.2:i386 libcap2:i386 libproxy1:i386 ibus-gtk:i386
  libdbus-glib-1-2:i386 libtdb1:i386 libasn1-8-heimdal:i386 libspeex1:i386
  libxslt1.1:i386 libgomp1:i386 libcapi20-3 libcapi20-3:i386
  libibus-1.0-0:i386 libcairo2:i386 libgssapi3-heimdal:i386
  libcanberra-gtk-module:i386 libcanberra0:i386 gtk2-engines-murrine:i386
  libwavpack1:i386 libqt4-opengl:i386 libsoup-gnome2.4-1:i386
  libv4lconvert0:i386 gstreamer0.10-plugins-good:i386 librsvg2-common:i386
  libncursesw5:i386 libiec61883-0:i386 libgdk-pixbuf2.0-0:i386
  libsdl-image1.2:i386 wine-gecko1.4 wine-gecko1.4:i386 libwind0-heimdal:i386
  libpixman-1-0:i386 libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386
  winetricks libcurl3:i386 libxinerama1:i386 libesd0:i386 libmikmod2:i386
  libgif4:i386 libxft2:i386 libcroco3:i386 libpulse-mainloop-glib0:i386
  libaa1:i386 libieee1284-3:i386 libao4:i386 libxmu6:i386
  libcanberra-gtk0:i386 libvorbisfile3:i386 libxpm4:i386 libqt4-svg:i386
  libgail-common:i386 libhcrypto4-heimdal:i386 libraw1394-11:i386
  libnspr4:i386 libshout3:i386 libdv4:i386 libhx509-5-heimdal:i386
  gstreamer0.10-x:i386 libgettextpo0 libgettextpo0:i386 libgd2-xpm:i386
  libheimbase1-heimdal:i386 libsdl-net1.2:i386 libjasper1:i386
  libgnome-keyring0:i386 libxtst6:i386 gtk2-engines-pixbuf:i386
  libtag1c2a:i386 librsvg2-2:i386 ttf-unfonts-core libmpg123-0
  libmpg123-0:i386 libssl0.9.8:i386 libmad0:i386 libsasl2-2:i386 libdb5.1:i386
  gtk2-engines-oxygen:i386 xaw3dg:i386 libpango1.0-0:i386
  libheimntlm0-heimdal:i386 libpulsedsp:i386 winbind libxcb-render0:i386
  libodbc1:i386 libexif12:i386 libqt4-scripttools:i386 librtmp0:i386
  libxp6:i386 libxcursor1:i386 libxcb-shm0:i386 libsasl2-modules:i386
  libxrandr2:i386 libgtk2.0-0:i386 libltdl7:i386 libkrb5-26-heimdal:i386
  glib-networking:i386 libsoup2.4-1:i386 libtag1-vanilla:i386
  libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  ia32-libs ia32-libs-multiarch:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libsane:i386 libusb-0.1-4:i386 playonlinux wine wine1.4 wine1.4-amd64
  wine1.4-common wine1.4-i386:i386
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 232 MB disk space will be freed.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libusb-0.1-4
```


If I click on them, then mark for removal ( even not the complete removal ) gives a looooong list of other packages that would be removed, which is not possible to copy and paste.
Among them: apt, ubuntu-minimal, wine and xubuntu-desktop. I don't think it's a good idea to just proceed.

Any idea apart from reinstalling from scratch? I use this computer for work and I have a lot of stuff on it. Backed up, but it would be a pain to recreate the environment...


Thanks!

---

### Post by dan45 on 2013-10-06
I tried to install something from Ubuntu Software Centre. It gives me a problem message, asks me if I want it to try and solve it, but it fails.

The message I get is:

[FONT=courier new]installArchives() failed: dpkg: error processing libusb-0.1-4 (--configure):
 libusb-0.1-4:amd64 2:0.1.12-20 cannot be configured because libusb-0.1-4:i386 is in a different version (2:0.1.12-23.2)
dpkg: error processing libusb-0.1-4:i386 (--configure):
 libusb-0.1-4:i386 2:0.1.12-23.2 cannot be configured because libusb-0.1-4:amd64 is in a different version (2:0.1.12-20)
[/FONT]

---

### Post by TheFu on 2013-10-06
If you've ever installed a plain .deb file (dpkg -i something.deb) this can be the result.  We call it "apt-hell" and it isn't fun.  I have 1 server like that now.  Trying to get important services migrated off it today, so an upgrade to 12.04 can happen this week.

OTOH, If you haven't, then there is hope.  Inside synaptic, there is a "fix broken packages" button. Click it. ;)  I'm crossing my fingers for your success.

Also, recreating an OS install isn't really as painful as people think.  I need to write a how-to, but it is the same method that I use for backups.  In short:
* backup critical settings for the machine and programs. Mostly /etc
* backup a list of packages. This list will be used on the other side to install updated versions of the packages again.
* backup any manually installed CPAN/ruby-gems from outside the APT repos.
* backup any important stuff like /var/www and /usr/local - things that aren't part of a package
* dump and backup any RDBMS files.
* backup /home (or where ever you have your HOME)

On the far side, restore in the same order. Just put files back where they belong, do not install anything you don't absolutely need at this point. After all the data, settings, /home, etc are back, use the list of packages to tell APT to install them.  If there are existing settings, those will be migrated to include changes for newer software versions ... or you will be told there is a difference and have an opportunity to merge, overwrite, leave unchanged - your choice.  Broken or missing programs will be noted.

Once you automate this, it is basically the same for every machine, so now you have a nice backup script.  On my desktop it takes about 3 minutes to run nightly, including pushing any changed data to a storage server on the network.  Recovering takes about an hour on broadband, but if you have an **apt-cache-ng** repo on the LAN, it could be 20 minutes.  

[This link]("http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup") has an older version of my backup script which might be useful if you need specific commands.

The restore is basically 3 steps, no script used.

---

### Post by wildmanne39 on 2013-10-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use normal fonts.
Thanks

---

### Post by TheFu on 2013-10-06
> **dan45 said:**
> I tried to install something from Ubuntu Software Centre. It gives me a problem message, asks me if I want it to try and solve it, but it fails.

The message I get is:

[FONT=courier new]installArchives() failed: dpkg: error processing libusb-0.1-4 (--configure):
 libusb-0.1-4:amd64 2:0.1.12-20 cannot be configured because libusb-0.1-4:[COLOR="#FF0000"]i386[/COLOR] is in a different version (2:0.1.12-23.2)
dpkg: error processing libusb-0.1-4:i386 (--configure):
 libusb-0.1-4:i386 2:0.1.12-23.2 cannot be configured because libusb-0.1-4:[COLOR="#FF0000"]amd64[/COLOR] is in a different version (2:0.1.12-20)
[/FONT]

So, you have i386 and amd64 conflicts.  Any idea how that could have happened?

---

### Post by dan45 on 2013-10-07
@The Fu

I took a look at the script - I will see what I can do... Installing rdiff-backup is not an option ;)

 If it turns out to be time consuming, without being sure it will work, I can just migrate everything to an old laptop and only wipe the current one once I am sure it's all there. But thank you very very much for the link to the script, I will certainly use it in the future! Thank you very much for that.

I don't remember installing plain Debian files, but there is a fair amount of scripts I just copied and pasted. I was careful not to pick the wrong version, but I probably got it wrong at some point. Or maybe a bug somewhere did it when I wasn't looking ;)

Thank you very much for your quick reply and the link to your script! 

Dan


PS - I did try the Fix Broken Packages option. They are too broken for that.

---

### Post by dan45 on 2013-10-07
@Wild Man

I will certainly do that in the future. Thanks.

---

### Post by TheFu on 2013-10-07
For you that link was more about the **dpkg** options, not rdiff-backup.

-get-selections and -set-selections .... 

Your old laptop ... is it 64-bit? Fly in the ointment, possibly.

Copy - understand - paste .... leaving out that middle part is dangerous, as you've learned.

---

