---
title: "Can't install IEs4Linux - cabextract problam"
date: 2008-04-12
forum: General Help
---

### Post by ShaiI769 on 2008-04-12
Hi There
So, I'm trying to install the software. I'm using Gutsy Gibbon (7.10), wine version 0.9.58 and cabextract 1.2-2 (according to synaptic). I'm absolutely sure I did everything right. I followed the instructions in the site and downloaded the repositories, the file itself and tried to install IE 6.

No matter what I try (gui, no gui, no flash, and so forth), I always get this error:

[I]$ ./ies4linux --no-flash --no-gui

IEs4Linux will:
  - Install Internet Explorers: 6.0

  - Using IE locale: EN-US
  - Install everything at: /home/shai/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   0%   SCR56EN.CAB[ OK ].CABP.CABBB

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/shai/.ies4linux/downloads/ie6/EN-US/ADVAUTH.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/CRLUPD.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/HHUPD.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/IEDOM.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/IE_EXTRA.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/IE_S*.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/SETUPW95.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/VGX.CAB: No such file or directory
[COLOR="Red"]An error occured when trying to cabextract some files.[/COLOR]
[/I]
My user have permissions, and everything else seems to be fine, I checked the "/home/shai/.ies4linux/downloads/ie6/EN-US/" but nothing has been downloaded, the folder is just empty.

I tried to find the CAB files myself from the net or from a windows IE install, and run ies4Linux, with no luck. I even Tried to install IE from "Wine Doors" (which goes ok, but in the end when I try to open IE, nothing happens), and copy an existing IE installation from windows' Program files folder (which runs, but in a blank screen with no toolbars and input boxes).

I'm really desperate, I need IE for my work and can't get one to run on Ubuntu. I hate booting up windows just for IE.

Help will be extremely appreciated.


Thanks in advance,
Shai

---

### Post by dcstar on 2008-04-12
> **ShaiI769 said:**
> Hi There
So, I'm trying to install the software. I'm using Gutsy Gibbon (7.10), wine version 0.9.58 and cabextract 1.2-2 (according to synaptic). I'm absolutely sure I did everything right. I followed the instructions in the site and downloaded the repositories, the file itself and tried to install IE 6.

No matter what I try (gui, no gui, no flash, and so forth), I always get this error:

[I]$ ./ies4linux --no-flash --no-gui

IEs4Linux will:
  - Install Internet Explorers: 6.0

  - Using IE locale: EN-US
  - Install everything at: /home/shai/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
**   0%  ** SCR56EN.CAB[ OK ].CABP.CABBB
..............
I'm really desperate, I need IE for my work and can't get one to run on Ubuntu. I hate booting up windows just for IE.

Help will be extremely appreciated.


Thanks in advance,
Shai

Well, it looks like if the file is no longer where it once was and cannot be downloaded, then that is that.

If you don't like booting Windows, then install VMware server, get the free conversion tool from the VMWare website and convert your Windows installation to a VM and run that inside Ubuntu.

---

### Post by lgambett on 2008-04-12
The problem is not in the download, I tried IES4Linux on my Gutsy box and it worked flawlessly. I managed also to install IE7 (Click on Advanced on the first screen)

---

### Post by ShaiI769 on 2008-04-12
> **lgambett said:**
> The problem is not in the download, I tried IES4Linux on my Gutsy box and it worked flawlessly. I managed also to install IE7 (Click on Advanced on the first screen)

Got the same error when trying to install IE7:

IEs4Linux will:
  - Install Internet Explorers: , 7.0
  - Using IE locale: EN-US
  - Install everything at: /home/shai/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   0%   IE7-WindowsXP-x86-enu.exe[ OK ]
[I]
Installing IE
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/shai/.ies4linux/downloads/ie6/EN-US/ADVAUTH.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/CRLUPD.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/HHUPD.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/IEDOM.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/IE_EXTRA.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/IE_S*.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/SETUPW95.CAB: No such file or directory
/home/shai/.ies4linux/downloads/ie6/EN-US/VGX.CAB: No such file or directory
 An error occured when trying to cabextract some files.

[/I]

Why can't my machine download the cab files?

---

### Post by ShaiI769 on 2008-04-12
Hi,
I solved it!
I apparently had a problem downloading the files needed to the ies4linux install (problems in wget?). I already knew what the files were (the program tells you when a file is missing), but I couldn't get them from anywhere. And then I remembered what open source is all about and just open the installation file in the text editor. There, I found the answer.

The file "install.sh" which is located in the lib directory, contains the paths to the files. The part that I needed, concerning IE6, is this:

```
	# Basic downloads for IE6
	URL_IE6_CABS=http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP
	IE6_CABS="ADVAUTH CRLUPD HHUPD IEDOM IE_EXTRA IE_S1 IE_S2 IE_S5 IE_S4 IE_S3 IE_S6 SETUPW95 FONTCORE FONTSUP VGX"
	# other possible cabs BRANDING GSETUP95 IEEXINST README SWFLASH (SCR56EN)

	# All MS downloads
	subsection $MSG_DOWNLOADING_FROM microsoft.com:

	download http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE
	download http://activex.microsoft.com/controls/vc/mfc42.cab
	download http://download.microsoft.com/download/win98SE/Update/5072/W98/EN-US/249973USA8.exe

	mkdir -p "$DOWNLOADDIR/ie6/EN-US"
	mkdir -p "$DOWNLOADDIR/ie6/$IE6_LOCALE"

	for cab in $IE6_CABS; do
		download "$URL_IE6_CABS/$IE6_LOCALE/$cab.CAB"
	done

	# SCR56EN is always downloaded from EN-US
	download "$URL_IE6_CABS/EN-US/SCR56EN.CAB"
```

So, i just copied and pasted in firefox, and walla!

1. The files needed to be copied into /home/shai/.ies4linux/downloads/ie6/EN-US/ (replace "shai" with your user) are:

ADVAUTH.CAB
CRLUPD.CAB
HHUPD.CAB
IEDOM.CAB
IE_EXTRA.CAB
IE_S1.CAB
IE_S2.CAB
IE_S5.CAB
IE_S4.CAB
IE_S3.CAB
IE_S6.CAB
SETUPW95.CAB
FONTCORE.CAB
FONTSUP.CAB
VGX.CAB
They are all located in the path:
```
http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/
```
assuming you language is "EN-US". You can change it to whatever you want.
(except for SCR56EN.CAB, which is always downloaded from EN-US)

2. These 3 files are needed to be downloaded from the following paths and copied to the directory:
/home/shai/.ies4linux/downloads/

```
http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE
http://activex.microsoft.com/controls/vc/mfc42.cab
http://download.microsoft.com/download/win98SE/Update/5072/W98/EN-US/249973USA8.exe
```

4. I ran the ies4linux installer, and it went just fine, not before I renamed some of the files (e.g. VGX.cab to VGX.CAB. Appreantly it's case-sensitive).

Just thought I'd share, if it might be useful to someone.

---

### Post by tefflox on 2008-04-12
It works!  Thanks for the excellent instructions :KS

---

### Post by TheCarNinja on 2008-05-13
To make this easier on everyone.
```
URL_IE6_CABS=http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP
        IE6_CABS="ADVAUTH CRLUPD HHUPD IEDOM IE_EXTRA IE_S1 IE_S2 IE_S5 
IE_S4 IE_S3 IE_S6 SETUPW95 FONTCORE FONTSUP VGX BRANDING GSETUP95 IEEXINST README SWFLASH SCR56EN"

        for cab in $IE6_CABS; do
                echo "<a href=\042$URL_IE6_CABS/EN-US/$cab.CAB\042>$cab</a>"
        done

```

---

### Post by andyst on 2008-05-20
I've had the same problem downloading the CAB files and it turned out to be a problem with my proxy settings.

Have a look in System -> Network Proxy and check that the HTTP proxy settings are correct.

The clue for me was when i couldn't download the google home page using:

```
wget www.google.co.uk
```

Hope this helps.

---

