---
title: "Wine not starting on lubuntu 17.10."
date: 2018-02-27
forum: General Help
---

### Post by Joao Lacerda on 2018-02-27
Hi Friends

I need some help on this issue.
I am trying to install wine on lubuntu 17.10 and till now i have not succeed.
I follow this " how to " of wine website  [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu).

and that are the error message that i have gotten on the terminal.

Errors were encountered while processing:
 /tmp/apt-dpkg-install-lkxkPN/135-libsane1_1.0.27-1~experimental2ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


after  "wine run" on teminal, I got this message


wine: configuration in '/home/joao/.wine' has been updated.
wine: cannot find L"C:\\windows\\system32\\run.exe"

Thank you for your time.

---

### Post by #&amp;thj^% on 2018-02-27
Just so we are on the same thought process, you did do this:
```
sudo dpkg --add-architecture i386 
```
Which command did you use to install?
```
sudo apt-get install --install-recommends winehq-stable
```

Development branch 	

```
sudo apt-get install --install-recommends winehq-devel
```

Staging branch

(discontinued)
	

```
sudo apt-get install --install-recommends winehq-staging
```
And I don't know why you would not install it without adding the PPA
I'm on Bionic Today, and a quick search shows:
```
apt search wine
Sorting... Done
Full Text Search... Done
fonts-wine/bionic,bionic 3.0-1ubuntu1 all
  Windows API implementation - fonts

gemrb/bionic 0.8.5-1 amd64
  Open-source engine to run Baldur's Gate, Icewind Dale and Planescape: Torment

gnome-colors/bionic,bionic 5.5.1-2ubuntu2 all
  set of GNOME icon themes

gnome-wine-icon-theme/bionic,bionic 5.5.1-2ubuntu2 all
  red variation of the GNOME-Colors icon theme

innoextract/bionic 1.6-1build3 amd64
  Tool for extracting data from an Inno Setup installer

libkwineffects11/bionic-proposed 4:5.12.2-0ubuntu2 amd64
  KDE window manager effects library

libwine/bionic 3.0-1ubuntu1 amd64
  Windows API implementation - library

libwine-dev/bionic 3.0-1ubuntu1 amd64
  Windows API implementation - development files

libwine-development/bionic 3.2-1 amd64
  Windows API implementation - library

libwine-development-dev/bionic 3.2-1 amd64
  Windows API implementation - development files

libwinpr-asn1-0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (ASN1 library)

libwinpr-bcrypt0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (bcrypt library)

libwinpr-credentials0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (credentials library)

libwinpr-credui0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (credeui library)

libwinpr-crt0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (crt library)

libwinpr-crypto0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (crypto library)

libwinpr-dev/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (development files)

libwinpr-dsparse0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (dsparse library)

libwinpr-environment0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (environment library)

libwinpr-error0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (error library)

libwinpr-file0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (file library)

libwinpr-handle0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (handle library)

libwinpr-heap0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (heap library)

libwinpr-input0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (input library)

libwinpr-interlocked0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (interlocked library)

libwinpr-io0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (io library)

libwinpr-library0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (library)

libwinpr-path0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (path library)

libwinpr-pipe0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (pipe library)

libwinpr-pool0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (pool library)

libwinpr-registry0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (registry library)

libwinpr-rpc0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (RPC library)

libwinpr-sspi0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (sspi library)

libwinpr-sspicli0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (sspicli library)

libwinpr-synch0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (synch library)

libwinpr-sysinfo0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (sysinfo library)

libwinpr-thread0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (thread library)

libwinpr-timezone0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (timezone library)

libwinpr-utils0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (utils library)

libwinpr-winhttp0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (winhttp library)

libwinpr-winsock0.1/bionic 1.1.0~git20140921.1.440916e+dfsg1-15ubuntu1 amd64
  Windows Portable Runtime library (winsock library)

libwinpr2-2/bionic,now 2.0.0~git20170725.1.1648deb+dfsg1-6build1 amd64 [installed]
  Windows Portable Runtime library

libwinpr2-dev/bionic 2.0.0~git20170725.1.1648deb+dfsg1-6build1 amd64
  Windows Portable Runtime library (development files)

mingw-w64-i686-dev/bionic,bionic 5.0.3-1 all
  Development files for MinGW-w64 targeting Win32

mingw-w64-x86-64-dev/bionic,bionic 5.0.3-1 all
  Development files for MinGW-w64 targeting Win64

playonlinux/bionic,bionic 4.2.12-1 all
  front-end for Wine

python-neo/bionic,bionic 0.3.3-2 all
  Python IO library for electrophysiological data formats

q4wine/bionic 1.3.6-2 amd64
  Qt GUI for wine (WINE)

shiki-colors/bionic,bionic 4.6-2ubuntu1 all
  set of Metacity/GTK-2+ themes

shiki-wine-theme/bionic,bionic 4.6-2ubuntu1 all
  red variation of the Shiki-Colors theme

tellico/bionic 3.1.1-0.1 amd64
  Collection manager for books, videos, music, etc

tellico-data/bionic,bionic 3.1.1-0.1 all
  Collection manager for books, videos, music, etc [data]

tellico-doc/bionic,bionic 3.1.1-0.1 all
  Collection manager for books, videos, music, etc [doc]

tellico-scripts/bionic,bionic 3.1.1-0.1 all
  Collection manager for books, videos, music, etc [scripts]

twine/bionic,bionic 1.8.1-2 all
  utility for interacting with PyPI

unmass/bionic 0.9-3.1 amd64
  Extract game archive files

wine-binfmt/bionic,bionic 3.0-1ubuntu1 all
  Windows API implementation - binfmt support

wine-development/bionic,bionic 3.2-1 all
  Windows API implementation - standard suite

wine-stable/bionic,bionic 3.0-1ubuntu1 all
  Windows API implementation - standard suite

wine1.6/bionic 1:1.8.4ubuntu1 amd64
  Windows API implementation (transitional package)

wine1.6-amd64/bionic 1:1.8.4ubuntu1 amd64
  Windows API implementation (transitional package 64-bit support)

wine1.6-dev/bionic 1:1.8.4ubuntu1 amd64
  Windows API implementation (transitional package development tools)

wine1.6-i386/bionic 1:1.8.4ubuntu1 i386
  Windows API implementation (transitional package 32-bit support)

wine32/bionic 3.0-1ubuntu1 i386
  Windows API implementation - 32-bit binary loader

wine32-development/bionic 3.2-1 i386
  Windows API implementation - 32-bit binary loader

wine32-development-preloader/bionic 3.2-1 i386
  Windows API implementation - prelinked 32-bit binary loader

wine32-development-tools/bionic 3.2-1 i386
  Windows API implementation - 32-bit developer tools

wine32-preloader/bionic 3.0-1ubuntu1 i386
  Windows API implementation - prelinked 32-bit binary loader

wine32-tools/bionic 3.0-1ubuntu1 i386
  Windows API implementation - 32-bit developer tools

wine64/bionic 3.0-1ubuntu1 amd64
  Windows API implementation - 64-bit binary loader

wine64-development/bionic 3.2-1 amd64
  Windows API implementation - 64-bit binary loader

wine64-development-preloader/bionic 3.2-1 amd64
  Windows API implementation - prelinked 64-bit binary loader

wine64-development-tools/bionic 3.2-1 amd64
  Windows API implementation - 64-bit developer tools

wine64-preloader/bionic 3.0-1ubuntu1 amd64
  Windows API implementation - prelinked 64-bit binary loader

wine64-tools/bionic 3.0-1ubuntu1 amd64
  Windows API implementation - 64-bit developer tools

winefish/bionic 1.3.3-0dl1ubuntu2 amd64
  LaTeX Editor based on Bluefish

winetricks/bionic,bionic 0.0+20180217-1 all
  package manager for Wine to install software easily

winpr-utils/bionic 2.0.0~git20170725.1.1648deb+dfsg1-6build1 amd64
  Windows Portable Runtime library command line utilities


```
I have not added the PPA

---

### Post by Dennis N on 2018-02-27
> after "wine run" on teminal, I got this message
wine: configuration in '/home/joao/.wine' has been updated.
wine: cannot find L"C:\\windows\\system32\\run.exe"
The wine command uses an executable windows program file as an argument:
```
wine program.exe
```
Wine appears to be working. So in your question, wine looks for a Windows program named 'run' (apparently it will add the .exe if missing) and can't find it where expected. Don't know how much you know about Wine, but you should first run **winecfg** in the terminal to configure the wine environment. Then, you need to first run the installer of a Windows program before hoping to run the program itself.

---

### Post by #&amp;thj^% on 2018-02-27
Nice catch Dennis N. :)
I must have been reading the link and by-past that info. :(
Cheers

---

### Post by Joao Lacerda on 2018-02-27
Thank you for your time.

I don't know much about wine. I have it installed on ubuntu 16.04 on other pc and it works fine.

the problem is on lubuntu 17.04. 
I can run winecfg and it works.
but I can not install any exe file the system do not recognize it.

---

### Post by #&amp;thj^% on 2018-02-27
> **Joao Lacerda said:**
> Thank you for your time.

I don't know much about wine. I have it installed on ubuntu 16.04 on other pc and it works fine.
I can run winecfg and it works.
but I can not install any exe file the system do not recognize it.

Can you give us an example?

---

### Post by Joao Lacerda on 2018-02-27
Thank you 1Fallen for your time.

I do not have installed the " [COLOR=#333333][FONT=Menlo]winehq-staging' 
only the winehq-stable.[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-02-27
Great! I was hoping you'd say that. :)
On any .exe is there any right click mouse options now? (Let me know if I'm to vague)

---

### Post by Joao Lacerda on 2018-02-27
1fallen thank you very much.

the right click :) ! 

Thank you very much.

---

### Post by #&amp;thj^% on 2018-02-27
Great! ;)
Enjoy.

---

