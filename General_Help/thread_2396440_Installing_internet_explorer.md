---
title: "Installing internet explorer"
date: 2018-07-15
forum: General Help
---

### Post by shankara2 on 2018-07-15
Work requires me to use internet explorer to login to ajera.

The first thing I tried was to install wine and cabextract using this website [https://help.ubuntu.com/community/InstallingInternetExplorer](https://help.ubuntu.com/community/InstallingInternetExplorer)

I got to this point 
./ies4linux

and this should happen:

Welcome, ! I'm IEs4Linux.
I can install IE 6, 5.5 and 5.0 for you easily and quickly.
You are just four 'enter's away from your IEs.

I'll ask you some questions now. Just answer y or n (default answer is the bold one)

IE 6 will be installed automatically.
Do you want to install IE 5.5 SP2 too? [ y / n ]

This happened:

IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

No user interface available. Use command-line ies4linux or install pygtk. Details: [http://www.tatanka.com.br/ies4linux/page/No_GUI](http://www.tatanka.com.br/ies4linux/page/No_GUI)

IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

	
Usage: ./ies4linux [OPTIONS]

This script downloads and automagically installs multiple versions of
Microsoft Internet Explorer on Wine.

Without any option, IEs4Linux will:
- install IE6
- install Adobe Flash 9
- create icons on Desktop and Menu
- use folder: /home/dagan/.ies4linux

You can configure other things:

--install-ie55         Install IE5.5 in BASEDIR/ie55/
--install-ie5          Install IE5 in BASEDIR/ie5/

--install-corefonts    Install MS Core Fonts (corefonts.sf.net)

--no-flash             Don't install Adobe Flash Player 9
--no-ie6               Don't install IE 6

--no-desktop-icon      Don't create an icon in Desktop
--no-menu-icon         Don't insert icon on Menu

--full-help            Display all possible options

I ran this command:

dagan@dagan-Latitude-E6420:~$ wine --version
wine-1.6.2
my wine version exceeds the 0.9.x requirement.

At the end of the day I need to use ajera.  When I try and use ajera with xubuntu 18.04 with firefox I get:

Firefox users must install the **Microsoft .NET Framework Assistant** add-on.

Verify that Microsoft .NET Framework 4.5.2 is installed on your workstation.

If installing IE under wine works...great.  If another method works...great

Any help would be appreciated.

thanks

---

### Post by HermanAB on 2018-07-16
Install Oracle Virtualbox and then make a virtual machine with the least annoying version of Microsoft's other OS in there.

---

### Post by Mark Phelps on 2018-07-16
Sorry, but using Wine (or any of its companions) is NOT going to work.  Why? I believe that the last version of IE that Wine supported was version 7 -- and most likely, you would need to use version 11 -- which is not available for Wine.

To stick with Linux, as mentioned, you would need to use a VM and install Windows in that VM.  It will automatically install IE -- but you will need a valid Windows license to do that.

---

