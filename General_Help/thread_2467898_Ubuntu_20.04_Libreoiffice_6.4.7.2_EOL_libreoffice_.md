---
title: "Ubuntu 20.04 Libreoiffice 6.4.7.2 EOL libreoffice PPA doesn't work"
date: 2021-10-11
forum: General Help
---

### Post by cscj01 on 2021-10-11
I am using Ubuntu 20.04.3 x64 with Libreoffice 6.4.7.2 (Repro version).  That version of LO Base is unstable for me as I use it quite a bit.  So I added the libreoffice PPA```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade

```That installed Libreoffice 7.2.1.  However, the program would not start.  I found this in Syslog```
libreoffice-base.desktop[97079]: Warning: failed to launch javaldx - java may not function correctly
```Finally I decided to install 7.2.1 from Libreoffice in a separate directory under Home.  I created a bash script to launch all of the 7.2.1 programs, and they all work.  What is driving me nuts is why is the PPA upgrade not working?  I have never had an issue like this before.

Additionally, do the Ubuntu packagers for Libreoffice plan to upgrade the Repro version since 6.4.7.2 is EOL?

---

### Post by grahammechanical on 2021-10-12
> Additionally, do the Ubuntu packagers for Libreoffice plan to upgrade the Repro version since 6.4.7.2 is EOL?

LibreOffice is one of those default programs that are upgraded throughout the support period of the Ubuntu Long Term Support Version. So, the answer is "Yes." I certainly expect it to happen. The developers are soon to release Ubuntu 21.10 and that has LibreOffice 7. So, I expect that a short while after Ubuntu 21.10 has been release Ubuntu 20.04 LTS will get an upgrade to LibreOffice 7. That has been the pattern for years.

Things are going to change. By the time Ubuntu 22.04 LTS is released LibreOffice will be the snap version and not the deb version. That has already happened in Ubuntu 21.10 development version. An upgrade removed the deb version and tried to install the snap version. It failed because I have at the moment a very poor quality landline internet connection. I was able to re-install the LibreOffice deb version and it is version 7.

The change over from deb to snap could be the reason for your problem. There is talk of the LibreOffice deb version being made available through a PPA and not through the repositories. This change over may be something to do with the matter that you are experiencing.

Regards

---

### Post by cscj01 on 2021-10-12
> **grahammechanical said:**
> LibreOffice is one of those default programs that are upgraded throughout the support period of the Ubuntu Long Term Support Version. So, the answer is "Yes." I certainly expect it to happen. The developers are soon to release Ubuntu 21.10 and that has LibreOffice 7. So, I expect that a short while after Ubuntu 21.10 has been release Ubuntu 20.04 LTS will get an upgrade to LibreOffice 7. That has been the pattern for years.

Things are going to change. By the time Ubuntu 22.04 LTS is released LibreOffice will be the snap version and not the deb version. That has already happened in Ubuntu 21.10 development version. An upgrade removed the deb version and tried to install the snap version. It failed because I have at the moment a very poor quality landline internet connection. I was able to re-install the LibreOffice deb version and it is version 7.

The change over from deb to snap could be the reason for your problem. There is talk of the LibreOffice deb version being made available through a PPA and not through the repositories. This change over may be something to do with the matter that you are experiencing.

Regards

Thank you for your reply.  I never thought about Snap in all this because I tend to avid them and use deb (old habits die hard).  After running the following```
snap find libreoffice
Name          Version  Publisher   Notes  Summary
libreoffice   7.2.1.2  canonical&#10003;  -      LibreOffice is a free and open source office suite
projectlibre  1.9.1    jibel       -      Project Management software - alternative to Microsoft Project
```I was surprised to find Libreoffice 7.2.1.2 installed as a Snap version.

This brings up a question as to how to proceed.  Since I used ppa-purge to remove libreoffice/ppa, I now have the distro version of Libreoffice (6.4.7.2) installed.  When I added the libreoffice/ppa to my system and used apt-get upgrade to upgrade what was installed?  Did the PPA install a Snap version or a deb version?  The PPA website [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa]("https://launchpad.net/~libreoffice/+archive/ubuntu/ppa") says nothing about Snap or deb, so I assume it is a deb site.  However, that brings up another question.  How did I get a Snap package of Libreoffice installed in the first place?

Finally, if I want to use Libreoffice 7.2.1.2, how would you suggest I proceed?;  Should I remove the Snap with ```
snap remove libreoffice
``` and proceed with adding the libreoffice/ppa and upgrading?  Or how do I execute a Snap version when the distro version, which is a deb version, is also installed?

One might say my confusion is complete because I have not preferred to work with Snap packages before.  Thanks for any advice you can offer.

---

### Post by cscj01 on 2021-10-12
I just found something quite interesting in my system if I issue the command```
snap find libreoffice
```I get the following```
Name          Version  Publisher   Notes  Summary
libreoffice   7.2.1.2  canonical&#10003;  -      LibreOffice is a free and open source office suite
projectlibre  1.9.1    jibel       -      Project Management software - alternative to Microsoft Project
```This is as above.  However, if I issue the command```
sudo snap remove libreoffice
```I get the followeing```
snap "libreoffice" is not installed
```If I give the command```
snap list
```I get```
Name                     Version                     Rev    Tracking         Publisher   Notes
bare                     1.0                         5      latest/stable    canonical&#10003;  base
chromium                 94.0.4606.81                1781   latest/stable    canonical&#10003;  -
core                     16-2.51.7                   11743  latest/stable    canonical&#10003;  core
core18                   20210722                    2128   latest/stable    canonical&#10003;  base
core20                   20210928                    1169   latest/stable    canonical&#10003;  base
gnome-3-28-1804          3.28.0-19-g98f9e67.98f9e67  161    latest/stable    canonical&#10003;  -
gnome-3-34-1804          0+git.3556cb3               72     latest/stable/…  canonical&#10003;  -
gnome-3-38-2004          0+git.6ba6040               76     latest/stable    canonical&#10003;  -
gnome-system-monitor     40.1-2-ga819fb4b55          163    latest/stable/…  canonical&#10003;  -
gtk-common-themes        0.1-59-g7bca6ae             1519   latest/stable/…  canonical&#10003;  -
kde-frameworks-5-core18  5.61.0                      32     latest/stable    kde&#10003;        -
puddletag-snap           2.0.1                       3      latest/stable    tschlaeppi  -
shotcut                  21.09.20                    474    latest/stable    meltytech&#10003;  classic
snap-store               3.38.0-64-g23c4c77          547    latest/stable/…  canonical&#10003;  -
snapd                    2.52                        13270  latest/stable    canonical&#10003;  snapd
zoom-client              5.8.0.16                    160    latest/stable    ogra        -
```So I DO NOT have Libreoffice 7.2.1 installed.  Now I am completely confused.  I checked the PPA again, and they are using debs.  So I have no idea why i can't get the PPA version to function.

---

### Post by Dennis N on 2021-10-12
**snap find libreoffice** doesn't find installed packages. It finds things you could install. 
To show installed snaps, run: **snap list** (which you did - showing it's not installed)
If you want to install the snap, run **snap install libreoffice**

The snap will install without interfering with the regular version. You could launch either one.

---

### Post by tea for one on 2021-10-12
```
snap find libreoffice
```
This will only find the software in the snap-store.
It will not install it unless you run
```
sudo snap install libreoffice
```

Whoops - a bit too slow

---

### Post by cscj01 on 2021-10-12
Does anyone have any ideas as to why the libreoffice/ppa will upgrade okay (at least with no errors), but the programs will not open?  If I run in a terminal, I get```
libreoffice --base
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'


Fatal exception: Signal 6
Stack:
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3e9a3)[0x7fef3bb259a3]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3eb1a)[0x7fef3bb25b1a]
/lib/x86_64-linux-gnu/libc.so.6(+0x46210)[0x7fef3b91d210]
/lib/x86_64-linux-gnu/libc.so.6(gsignal+0xcb)[0x7fef3b91d18b]
/lib/x86_64-linux-gnu/libc.so.6(abort+0x12b)[0x7fef3b8fc859]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x9e911)[0x7fef38a8a911]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0xaa38c)[0x7fef38a9638c]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0xaa3f7)[0x7fef38a963f7]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0xaa6a9)[0x7fef38a966a9]
/usr/lib/libreoffice/program/libmergedlo.so(+0xe76f38)[0x7fef3c9c4f38]
/usr/lib/libreoffice/program/libmergedlo.so(+0x14b4bad)[0x7fef3d002bad]
/usr/lib/libreoffice/program/libmergedlo.so(+0x14d1c95)[0x7fef3d01fc95]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2ce093d)[0x7fef3e82e93d]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2ce0c3a)[0x7fef3e82ec3a]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN3utl10ConfigItemC2ERKN3rtl8OUStringE14ConfigItemMode+0x82)[0x7fef3e828872]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2d15b16)[0x7fef3e863b16]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN19SvtSysLocaleOptionsC1Ev+0x129)[0x7fef3e864fa9]
/usr/lib/libreoffice/program/libmergedlo.so(+0x316d396)[0x7fef3ecbb396]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0xeff56)[0x7fef34b63f56]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0xf1a5d)[0x7fef34b65a5d]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0xffc1b)[0x7fef34b73c1b]
/usr/lib/libreoffice/program/libmergedlo.so(_Z7InitVCLv+0x502)[0x7fef3ecc7df2]
/usr/lib/libreoffice/program/libmergedlo.so(_Z10ImplSVMainv+0x115)[0x7fef3ecc90b5]
/usr/lib/libreoffice/program/libmergedlo.so(soffice_main+0xa3)[0x7fef3dd04b93]
/usr/lib/libreoffice/program/soffice.bin(+0x10b0)[0x55d3c73550b0]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x7fef3b8fe0b3]
/usr/lib/libreoffice/program/soffice.bin(+0x10ee)[0x55d3c73550ee]
```and```
libreoffice -write
terminate called after throwing an instance of 'com::sun::star::container::NoSuchElementException'
```

---

### Post by Dennis N on 2021-10-12
Well, if you search for the message "terminate called after throwing an instance of 'com::sun::star::container::NoSuchElementException" you will get numerous results. I didn't examine them, but you might find something there. Some go back years.

If you don't discover anything, and no solution arises, I would go with either the Snap, Flatpak or AppImage. I've tried them all on different machines, and they are all good. The AppImage allowed installation of just the Writer component. Since that's all I ever use of LibreOffice, it's my favorite.

---

