---
title: "Software Updater Error Msg: Package Dependencies Cannot Be Resolved"
date: 2023-07-31
forum: General Help
---

### Post by ozark_hillbilly on 2023-07-31
I am receiving an error message when enabling the Software Updater to install the latest security updates.

I am unchecking the box for ImageMagick as it no longer resides on my Linux installation. This has never created
an issue in the past with security updates..

I am unsure what is the issue so maybe someone can offer some insight.

I have attached two screeenshots of the error message and the updates to be installed.

Ubuntu 20.04.6 LTS

thanks....

---

### Post by Bashing-om on 2023-07-31
ozark_hillbilly - Hello again :D

The terminal is always a friend in deed.

Please activate a terminal interface and post back - using code tags - the outputs of the commands:
```

sudo apt update
sudo apt upgrade

```

[INDENT]a proper place to start looking
[/INDENT]

---

### Post by prcowley on 2023-07-31
The same problem happened in  kernel 6.2.0-25 and is caused by missing header files.  It is a known problem but alas not yet fixed.  It is to do with compiling the kernel modules and not having the header files to do it with.

To resolve it type this in a terminal window:
sudo apt install linux-headers-6.2.0-26-generic

It will download the files and will compile all the kernel modules.
Then reboot and you should be OK .... until the next kernel version.

Cheers
Pete

---

### Post by ozark_hillbilly on 2023-08-01
Terminal output:

ed@ed-G41MT-S2PT:~$ sudo apt update
[sudo] password for ed: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease                      
Hit:2 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                  
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease               
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease              
Hit:5 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) focal InRelease     
Hit:6 [https://apt.syncthing.net](https://apt.syncthing.net) syncthing InRelease
Hit:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
16 packages can be upgraded. Run 'apt list --upgradable' to see them.
ed@ed-G41MT-S2PT:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libavformat58 libavfilter7 libmagickcore-6.q16-6-extra libswresample3
  libzmq5 libmagickwand-6.q16-6 python3-rsa libpostproc55 imagemagick-6.q16
  libavcodec58 libavutil56 libswscale5 libopenexr24 libmysofa1
  libmagickcore-6.q16-6 imagemagick-6-common
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
#
# An OpenSSL vulnerability has recently been fixed with USN-6188-1 & 6119-1:
# CVE-2023-2650: possible DoS translating ASN.1 object identifiers.
# Ensure you have updated the package to its latest version.
#
The following packages will be upgraded:
  gcc-10-base imagemagick-6-common imagemagick-6.q16 libatomic1 libcc1-0 libgcc-s1 libgomp1 libitm1 liblsan0 libmagickcore-6.q16-6
  libmagickcore-6.q16-6-extra libmagickwand-6.q16-6 libquadmath0 libstdc++6 libtsan0 libubsan1
16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 standard LTS security updates
Need to get 7,040 kB of archives.
After this operation, 65.5 kB of additional disk space will be used.
Do you want to continue? [Y/n]


Why the updater does not realize ImageMagick has been removed/purged beats me. It seems intent on updating something no longer there. ???
Can I proceed with the terminal upgrade even though ImageMagick is not present?

---

### Post by ozark_hillbilly on 2023-08-01
Terminal output:

ed@ed-G41MT-S2PT:~$ sudo apt install linux-headers-6.2.0-26-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-6.2.0-26-generic
E: Couldn't find any package by glob 'linux-headers-6.2.0-26-generic'
ed@ed-G41MT-S2PT:~$

---

### Post by ActionParsnip on 2023-08-01
What is the output of
```

apt-cache policy libatomic1 gcc10-base liblsan0 libquadmath0 libtsan0 libubsan1

```

---

### Post by deadflowr on 2023-08-01
> Why the updater does not realize ImageMagick has been removed/purged beats me. It seems intent on updating something no longer there. ???
Can I proceed with the terminal upgrade even though ImageMagick is not present?
i gave an answer abut that in your other thread:
[https://ubuntuforums.org/showthread.php?t=2489037&p=14151276#post14151276]("https://ubuntuforums.org/showthread.php?t=2489037&p=14151276#post14151276")
As you can see from the output in post #4 here you have several imagemagick packages, but none are simply called imagemagick.
They're all libmagick-something or something related.
They're all built from the imagemagick source.

---

### Post by ozark_hillbilly on 2023-08-01
Terminal output of  'apt-cache policy libatomic1 gcc10-base liblsan0 libquadmath0 libtsan0 libubsan1':


ed@ed-G41MT-S2PT:~$ apt-cache policy libatomic1 gcc10-base liblsan0 libquadmath0 libtsan0 libubsan1
libatomic1:
  Installed: 10.3.0-1ubuntu1~20.04
  Candidate: 10.5.0-1ubuntu1~20.04
  Version table:
     10.5.0-1ubuntu1~20.04 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
 *** 10.3.0-1ubuntu1~20.04 100
        100 /var/lib/dpkg/status
     10-20200411-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
liblsan0:
  Installed: 10.3.0-1ubuntu1~20.04
  Candidate: 10.5.0-1ubuntu1~20.04
  Version table:
     10.5.0-1ubuntu1~20.04 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
 *** 10.3.0-1ubuntu1~20.04 100
        100 /var/lib/dpkg/status
     10-20200411-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
libquadmath0:
  Installed: 10.3.0-1ubuntu1~20.04
  Candidate: 10.5.0-1ubuntu1~20.04
  Version table:
     10.5.0-1ubuntu1~20.04 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
 *** 10.3.0-1ubuntu1~20.04 100
        100 /var/lib/dpkg/status
     10-20200411-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
libtsan0:
  Installed: 10.3.0-1ubuntu1~20.04
  Candidate: 10.5.0-1ubuntu1~20.04
  Version table:
     10.5.0-1ubuntu1~20.04 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
 *** 10.3.0-1ubuntu1~20.04 100
        100 /var/lib/dpkg/status
     10-20200411-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
libubsan1:
  Installed: 10.3.0-1ubuntu1~20.04
  Candidate: 10.5.0-1ubuntu1~20.04
  Version table:
     10.5.0-1ubuntu1~20.04 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
 *** 10.3.0-1ubuntu1~20.04 100
        100 /var/lib/dpkg/status
     10-20200411-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
N: Unable to locate package gcc10-base
ed@ed-G41MT-S2PT:~$

---

### Post by ozark_hillbilly on 2023-08-01
As you recommended in your response in the other referenced thread I went ahead and did the 'dpkg -l | grep magick' terminal command:

ed@ed-G41MT-S2PT:~$ dpkg -l | grep magick
ii  imagemagick-6-common                       8:6.9.10.23+dfsg-2.1ubuntu11.7      all          image manipulation programs -- infrastructure
ii  imagemagick-6.q16                          8:6.9.10.23+dfsg-2.1ubuntu11.7      amd64        image manipulation programs -- quantum depth Q16
ii  libmagickcore-6.q16-6:amd64                8:6.9.10.23+dfsg-2.1ubuntu11.7      amd64        low-level image manipulation library -- quantum depth Q16
ii  libmagickcore-6.q16-6-extra:amd64          8:6.9.10.23+dfsg-2.1ubuntu11.7      amd64        low-level image manipulation library - extra codecs (Q16)
ii  libmagickwand-6.q16-6:amd64                8:6.9.10.23+dfsg-2.1ubuntu11.7      amd64        image manipulation library -- quantum depth Q16
ed@ed-G41MT-S2PT:~$ 

So does this indicate libraries remain that make the updater think it still needs to actively update ImageMagick related resources?

---

### Post by #&amp;thj^% on 2023-08-02
You are having a tough time understanding what deadflowr and I are trying to say, Naming is where a lot of folks get lost, Ubuntu ships with  imagemagick in the core of the OS, not to be confused with JUST imagemagick the application.
If you was to try and remove all:
```
ii imagemagick-6-common 8:6.9.10.23+dfsg-2.1ubuntu11.7 all image manipulation programs -- infrastructure
ii imagemagick-6.q16 8:6.9.10.23+dfsg-2.1ubuntu11.7 amd64 image manipulation programs -- quantum depth Q16
ii libmagickcore-6.q16-6:amd64 8:6.9.10.23+dfsg-2.1ubuntu11.7 amd64 low-level image manipulation library -- quantum depth Q16
ii libmagickcore-6.q16-6-extra:amd64 8:6.9.10.23+dfsg-2.1ubuntu11.7 amd64 low-level image manipulation library - extra codecs (Q16)
ii libmagickwand-6.q16-6:amd64 8:6.9.10.23+dfsg-2.1ubuntu11.7 amd64 image manipulation library -- quantum depth Q16
ed@ed-G41MT-S2PT:~$ 
```
You would break your system. (But it is your system to do with what you want)
One more look:
```
 apt policy imagemagick
imagemagick:
  Installed: (none)
  Candidate: 8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1
  Version table:
     8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/universe amd64 Packages
     8:6.9.11.60+dfsg-1.6 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages

```

ImageMagick is a suite of command line tools and libraries for working with images and packages that depend on it or uses parts of it to function.
Cups uses it for its filters and while it's possible that you don't use any filters that use ImageMagick, I'd recommend that you keep it, because removing it may break Cups.(Or More)
One more look here:
```
sudo dpkg --purge --force-all imagemagick
dpkg: warning: ignoring request to remove imagemagick which isn't installed

```
EDIT: To show how:
```
apt depends cups-filters
cups-filters
  Depends: bc
  Depends: cups-filters-core-drivers (>= 2.0~rc1-0ubuntu1.2)
  Depends: ghostscript
  Depends: poppler-utils
  Depends: libc6 (>= 2.34)
  Depends: libcups2 (>= 2.3~b6)
  Depends: libcupsfilters2 (>= 2.0~b4-0ubuntu1)
  Depends: libppd2 (>= 2:2.0~b4-0ubuntu1)
  Conflicts: foomatic-filters
  Conflicts: foomatic-filters-beh
  Conflicts: <ghostscript-cups>
  Recommends: colord
  Recommends: <printer-driver-braille>
 |Recommends: liblouisutdml-bin
  Recommends: liblouis-bin
  Suggests: antiword
  Suggests: docx2txt
 |Suggests: foomatic-db-compressed-ppds
  Suggests: foomatic-db
    foomatic-db-compressed-ppds
 [B][COLOR="#FF0000"] Suggests: imagemagick
    graphicsmagick-imagemagick-compat
    imagemagick-6.q16[/COLOR][/B]
  Suggests: lynx
  Replaces: foomatic-filters
    cups-filters
  Replaces: foomatic-filters-beh
    cups-filters
  Replaces: <ghostscript-cups>
    cups-filters

```
Or, and you most likely don't use conky but I'll show anyway to prove a point here:
```
apt depends conky-manager2
conky-manager2
  Depends: libc6 (>= 2.34)
  Depends: libgdk-pixbuf-2.0-0 (>= 2.22.0)
  Depends: libgee-0.8-2 (>= 0.8.3)
  Depends: libglib2.0-0 (>= 2.37.3)
  Depends: libgtk-3-0 (>= 3.16.2)
  Depends: libjson-glib-1.0-0 (>= 1.5.2)
  Depends: coreutils
  Depends: conky
  Depends: p7zip-full
  Depends: rsync
  [B][COLOR="#FF0000"][COLOR="#FF0000"]Depends: imagemagick
    graphicsmagick-imagemagick-compat[/COLOR][/COLOR][/B]
    imagemagick-6.q16

```

---

### Post by ozark_hillbilly on 2023-08-02
Ok, I get what you are saying. This was all precipitated when I started to run very low on my filesystem root partition space available.
I deleted inagemagick in an attempt to free up space. Since then the low memory issue has been resolved.

Do you suggest the best path forward is to put imagemagick back/reinstall to overcome the security update errors? 

My aim is to have clean uneventful updates and if putting imagemagick back will alleviate that issue so be it.

---

### Post by #&amp;thj^% on 2023-08-02
Just take the updates with imagemagick then check with "apt policy imagemagick"
I'm now curious is all.
You say Root was getting full?
```
du -h /boot
du: cannot read directory '/boot/efi': Permission denied
4.0K	/boot/efi
2.3M	/boot/grub/fonts
132K	/boot/grub/locale
3.5M	/boot/grub/x86_64-efi
8.3M	/boot/grub
507M	/boot

```
Now Root
```
sudo du -h /root
[sudo] password for me: 
292K	/root/.synaptic/log
4.0K	/root/.synaptic/tmp
308K	/root/.synaptic
4.0K	/root/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/toolbar
4.0K	/root/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/statusbar
4.0K	/root/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/images/Bitmaps
8.0K	/root/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/images
4.0K	/root/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/popupmenu
4.0K	/root/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/menubar
28K	/root/.config/libreoffice/4/user/config/soffice.cfg/modules/swriter
32K	/root/.config/libreoffice/4/user/config/soffice.cfg/modules
36K	/root/.config/libreoffice/4/user/config/soffice.cfg
76K	/root/.config/libreoffice/4/user/config
4.0K	/root/.config/libreoffice/4/user/autocorr
1016K	/root/.config/libreoffice/4/user/database/biblio
1.0M	/root/.config/libreoffice/4/user/database
4.0K	/root/.config/libreoffice/4/user/psprint
12K	/root/.config/libreoffice/4/user/gallery
8.0K	/root/.config/libreoffice/4/user/autotext
8.0K	/root/.config/libreoffice/4/user/pack/config
20K	/root/.config/libreoffice/4/user/pack/database/biblio
28K	/root/.config/libreoffice/4/user/pack/database
8.0K	/root/.config/libreoffice/4/user/pack/autotext
16K	/root/.config/libreoffice/4/user/pack/basic/Standard
28K	/root/.config/libreoffice/4/user/pack/basic
100K	/root/.config/libreoffice/4/user/pack
4.0K	/root/.config/libreoffice/4/user/uno_packages/cache/uno_packages
8.0K	/root/.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
8.0K	/root/.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
40K	/root/.config/libreoffice/4/user/uno_packages/cache/registry
48K	/root/.config/libreoffice/4/user/uno_packages/cache
52K	/root/.config/libreoffice/4/user/uno_packages
8.0K	/root/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
8.0K	/root/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
40K	/root/.config/libreoffice/4/user/extensions/bundled/registry
48K	/root/.config/libreoffice/4/user/extensions/bundled
4.0K	/root/.config/libreoffice/4/user/extensions/tmp/extensions
8.0K	/root/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
8.0K	/root/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
40K	/root/.config/libreoffice/4/user/extensions/tmp/registry
48K	/root/.config/libreoffice/4/user/extensions/tmp
8.0K	/root/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
8.0K	/root/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
4.0K	/root/.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
40K	/root/.config/libreoffice/4/user/extensions/shared/registry
48K	/root/.config/libreoffice/4/user/extensions/shared
152K	/root/.config/libreoffice/4/user/extensions
16K	/root/.config/libreoffice/4/user/basic/Standard
28K	/root/.config/libreoffice/4/user/basic
1.5M	/root/.config/libreoffice/4/user
1.5M	/root/.config/libreoffice/4
1.5M	/root/.config/libreoffice
12K	/root/.config/Mousepad
8.0K	/root/.config/gtk-2.0
8.0K	/root/.config/dconf
8.0K	/root/.config/xfce4/xfconf/xfce-perchannel-xml
12K	/root/.config/xfce4/xfconf
12K	/root/.config/xfce4/terminal
28K	/root/.config/xfce4
4.0K	/root/.config/ibus/bus
8.0K	/root/.config/ibus
12K	/root/.config/gtk-3.0
16K	/root/.config/Thunar
8.0K	/root/.config/system-monitoring-center
1.6M	/root/.config
16K	/root/.cache/thumbnails/normal
20K	/root/.cache/thumbnails
8.0K	/root/.cache/mesa_shader_cache/71
8.0K	/root/.cache/mesa_shader_cache/f1
8.0K	/root/.cache/mesa_shader_cache/bb
8.0K	/root/.cache/mesa_shader_cache/f6
8.0K	/root/.cache/mesa_shader_cache/b8
8.0K	/root/.cache/mesa_shader_cache/1a
8.0K	/root/.cache/mesa_shader_cache/f2
8.0K	/root/.cache/mesa_shader_cache/af
8.0K	/root/.cache/mesa_shader_cache/d6
8.0K	/root/.cache/mesa_shader_cache/79
8.0K	/root/.cache/mesa_shader_cache/a7
8.0K	/root/.cache/mesa_shader_cache/0c
8.0K	/root/.cache/mesa_shader_cache/d4
8.0K	/root/.cache/mesa_shader_cache/99
8.0K	/root/.cache/mesa_shader_cache/9e
8.0K	/root/.cache/mesa_shader_cache/29
8.0K	/root/.cache/mesa_shader_cache/dc
8.0K	/root/.cache/mesa_shader_cache/57
8.0K	/root/.cache/mesa_shader_cache/59
8.0K	/root/.cache/mesa_shader_cache/52
8.0K	/root/.cache/mesa_shader_cache/70
8.0K	/root/.cache/mesa_shader_cache/60
12K	/root/.cache/mesa_shader_cache/62
8.0K	/root/.cache/mesa_shader_cache/aa
8.0K	/root/.cache/mesa_shader_cache/00
8.0K	/root/.cache/mesa_shader_cache/67
8.0K	/root/.cache/mesa_shader_cache/d8
8.0K	/root/.cache/mesa_shader_cache/9a
12K	/root/.cache/mesa_shader_cache/f3
8.0K	/root/.cache/mesa_shader_cache/13
8.0K	/root/.cache/mesa_shader_cache/20
8.0K	/root/.cache/mesa_shader_cache/e5
8.0K	/root/.cache/mesa_shader_cache/b4
8.0K	/root/.cache/mesa_shader_cache/fe
8.0K	/root/.cache/mesa_shader_cache/be
8.0K	/root/.cache/mesa_shader_cache/66
8.0K	/root/.cache/mesa_shader_cache/e9
8.0K	/root/.cache/mesa_shader_cache/98
8.0K	/root/.cache/mesa_shader_cache/2f
8.0K	/root/.cache/mesa_shader_cache/46
8.0K	/root/.cache/mesa_shader_cache/30
16K	/root/.cache/mesa_shader_cache/fd
8.0K	/root/.cache/mesa_shader_cache/16
8.0K	/root/.cache/mesa_shader_cache/32
8.0K	/root/.cache/mesa_shader_cache/23
8.0K	/root/.cache/mesa_shader_cache/37
8.0K	/root/.cache/mesa_shader_cache/a5
8.0K	/root/.cache/mesa_shader_cache/06
8.0K	/root/.cache/mesa_shader_cache/3a
8.0K	/root/.cache/mesa_shader_cache/89
8.0K	/root/.cache/mesa_shader_cache/8c
552K	/root/.cache/mesa_shader_cache
8.0K	/root/.cache/dconf
4.0K	/root/.cache/gvfsd
24K	/root/.cache/nvidia/GLCache/b79cbf418447ffb8035dd0ae7776efbb/5f16e64abada9c3a
28K	/root/.cache/nvidia/GLCache/b79cbf418447ffb8035dd0ae7776efbb
32K	/root/.cache/nvidia/GLCache
36K	/root/.cache/nvidia
4.0K	/root/.cache/at-spi
4.0K	/root/.cache/doc
60K	/root/.cache/webkit/icondatabase
64K	/root/.cache/webkit
324K	/root/.cache/gstreamer-1.0
4.0K	/root/.cache/gvfs
4.0K	/root/.cache/zenity/CacheStorage
4.0K	/root/.cache/zenity/WebKitCache/Version 16/Blobs
12K	/root/.cache/zenity/WebKitCache/Version 16
16K	/root/.cache/zenity/WebKitCache
24K	/root/.cache/zenity
1.2M	/root/.cache
44K	/root/.local/share/gvfs-metadata
4.0K	/root/.local/share/Mousepad
4.0K	/root/.local/share/webkitgtk/deviceidhashsalts/1
8.0K	/root/.local/share/webkitgtk/deviceidhashsalts
8.0K	/root/.local/share/webkitgtk/storage
4.0K	/root/.local/share/webkitgtk/localstorage
4.0K	/root/.local/share/webkitgtk/databases/indexeddb/v1
8.0K	/root/.local/share/webkitgtk/databases/indexeddb
12K	/root/.local/share/webkitgtk/databases
4.0K	/root/.local/share/webkitgtk/serviceworkers
52K	/root/.local/share/webkitgtk
4.0K	/root/.local/share/keyrings
4.0K	/root/.local/share/inxi
4.0K	/root/.local/share/zenity/deviceidhashsalts/1
8.0K	/root/.local/share/zenity/deviceidhashsalts
8.0K	/root/.local/share/zenity/storage
32K	/root/.local/share/zenity
144K	/root/.local/share
148K	/root/.local
2.2M	/root/.launchpadlib/api.launchpad.net/cache
2.2M	/root/.launchpadlib/api.launchpad.net
2.3M	/root/.launchpadlib
4.0K	/root/.gvfs
4.0K	/root/.nano
4.0K	/root/Desktop
4.0K	/root/.ssh
24K	/root/.gnupg
12K	/root/.dbus/session-bus
16K	/root/.dbus
5.6M	/root

```
I'll grep for imagemagick
```
 sudo du -h /root | grep imagemagick
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
No signs of it.

---

### Post by ozark_hillbilly on 2023-08-02
1Fallen,

"Just take the updates with imagemagick then check with "apt policy imagemagick"

Ok, I just completed the latest updates and had checked all the boxes. Everything went fine. Not sure what is different at this point but the fact all updates installed
with no errors is encouraging.
Do you know if there is a way to capture or log the Software Updater "details" that scroll up the screen as the updates are installed? 

Here is:

ed@ed-G41MT-S2PT:~$ apt policy imagemagick
imagemagick:
  Installed: (none)
  Candidate: 8:6.9.10.23+dfsg-2.1ubuntu11.9
  Version table:
     8:6.9.10.23+dfsg-2.1ubuntu11.9 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 Packages
     8:6.9.10.23+dfsg-2.1ubuntu11 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
ed@ed-G41MT-S2PT:~$ 

"You say Root was getting full?"

Yes, every time I ran Deja Dup backup it filled my root filesystem up even though I explicitly told it to use a backup partition on a different physical drive.
I now just manually copy/transfer whatever personal data files I want to save. Much easier but not efficient certainly.

Here is the results of those terminal commands you were curious about:

ed@ed-G41MT-S2PT:~$ du -h /boot
2.5M	/boot/grub/i386-pc
2.3M	/boot/grub/fonts
7.1M	/boot/grub
183M	/boot
ed@ed-G41MT-S2PT:~$ sudo du -h /root
[sudo] password for ed: 
4.0K	/root/backups
16K	/root/Desktop
4.0K	/root/.cache/gvfs
4.0K	/root/.cache/doc
4.0K	/root/.cache/keyring-YN8911
4.0K	/root/.cache/keyring-IQYA71
20K	/root/.cache
4.0K	/root/snap/snap-store/common
4.0K	/root/snap/snap-store/959
4.0K	/root/snap/snap-store/638
16K	/root/snap/snap-store
20K	/root/snap
4.0K	/root/.config/goa-1.0
4.0K	/root/.config/pulse
8.0K	/root/.config/dconf
8.0K	/root/.config/bleachbit
8.0K	/root/.config/gedit
4.0K	/root/.config/gtk-3.0
4.0K	/root/.config/yelp
4.0K	/root/.config/enchant
4.0K	/root/.config/nautilus
56K	/root/.config
4.0K	/root/.synaptic/tmp
68K	/root/.synaptic/log
80K	/root/.synaptic
4.0K	/root/.local/share/webkitgtk/deviceidhashsalts/1
8.0K	/root/.local/share/webkitgtk/deviceidhashsalts
8.0K	/root/.local/share/webkitgtk/storage/yI27T_ZARg_SLvmcEPyLkSg_Z720G9yBLnRofvMjy-Y/yI27T_ZARg_SLvmcEPyLkSg_Z720G9yBLnRofvMjy-Y
12K	/root/.local/share/webkitgtk/storage/yI27T_ZARg_SLvmcEPyLkSg_Z720G9yBLnRofvMjy-Y
20K	/root/.local/share/webkitgtk/storage
32K	/root/.local/share/webkitgtk
112K	/root/.local/share/gvfs-metadata
8.0K	/root/.local/share/gedit
4.0K	/root/.local/share/Trash/files
4.0K	/root/.local/share/Trash/info
12K	/root/.local/share/Trash
84K	/root/.local/share/tracker/data
88K	/root/.local/share/tracker
4.0K	/root/.local/share/flatpak/db
8.0K	/root/.local/share/flatpak
4.0K	/root/.local/share/keyrings
4.0K	/root/.local/share/nano
4.0K	/root/.local/share/nautilus/scripts
8.0K	/root/.local/share/nautilus
292K	/root/.local/share
296K	/root/.local
8.0K	/root/.dbus/session-bus
12K	/root/.dbus
520K	/root
ed@ed-G41MT-S2PT:~$ 


ed@ed-G41MT-S2PT:~$ sudo du -h /root | grep imagemagick 
ed@ed-G41MT-S2PT:~$ 

That last command returned a big fat 0.... is that expected?

Appreciate your assistance on all this..... 2 Thumbs Up...

edit -

I forgot to mention I ran Bleachbit in an attempt to reduce spaced used in filesystem root.
It opened up about 13 GB IIRC....

---

### Post by #&amp;thj^% on 2023-08-03
Ahh, that explains a lot then for root "Deja Dup"
And this is a good thing,  sudo du -h /root | grep imagemagick>>>returned a big fat 0.... is that expected? Yes Sir!
Good Job
Regards

---

