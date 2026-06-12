---
title: "HOW TO install Internet Explorer"
date: 2007-06-06
forum: General Help
---

### Post by DeathStar on 2007-06-06
Hi All,

I know this might seem like a crazy idea, but if you're a web developer, then testing your site in IE is pretty crucial (since the majority of people still use IE for some reason).

You can get IE installed in UBUNTU using Wine and IES4LINUX. Here's how:


**STEP ONE:** Update your system
Update your system either using the "Update Manager" in the "System" menu, or by opening a terminal and typing:
```
sudo apt-get update
sudo apt-get upgrade
```



**STEP TWO:** Install wine
Wine lets you emulate a Windows environment to run Windows programs. In a terminal window, type:
```
sudo apt-get install wine
```



**STEP THREE:** Install cabextract
Install cabextract to unzip the ies4linux files (step 5)
```
sudo apt-get install cabextract
```



**STEP FOUR:** Download ies4linux
You will need to download the latest version of ies4linux. In a terminal windows, type:
```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
```



**STEP FIVE:** Extract the files
Once ies4linux is downloaded, extract the files by typing:
```
tar zxvf ies4linux-latest.tar.gz
```



**STEP SIX:** Install ies4linux
Firstly, go into the directory where you just extracted the files to:
```
cd ies4linux-*
* being the version number (just type cd ies4linux and then press tab)
```
And then run the installer:
```
./ies4linux
```
As you go through the installer, IE6 will be installed by default. It will ask you whether you want to install IE 5.5 and IE 5.0 as well, but you don't have to. It will also ask you which locale you want to install IE as. If you're happy with the default (EN-US), just press enter. It will then ask you if you want to install the flash 9 plugin and desktop shortcuts. Generally it's better to say "y" to this. You can always delete your desktop shortcuts at a later date (if you don't like them). The installer will then go and do its thing.

And that's it. You're done! Hope this helps.

For more information, please refer to [[COLOR="Blue"]http://www.tatanka.com.br/ies4linux/page/Main_Page[/COLOR]]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

Cheers,
DS

---

### Post by elettronicha on 2007-06-06
> **DeathStar said:**
> 
I know this might seem like a crazy idea, but if you're a web developer, then testing your site in IE is pretty crucial (since the majority of people still use IE for some reason).

Well, a web developer should be interested in following the w3c standard not in IE compatibility... :)

---

### Post by DeathStar on 2007-06-07
True... Web developers shoul be aiming to follow W3C standards...

But unfortunately, so should Microsoft!

DS

---

### Post by borahshadow on 2007-06-07
I agree that web developers should follow W3C standards but there is still a need for it to work right in IE and sometimes you can still follow W3C standards and have it work right in IE even if it is not the best way of doing something You can still (for the most part) follow W3c standards
hope that made sense

---

### Post by TravMan63 on 2007-06-15
as of 2007/6/15 - this didn't work...

too many errors:
Resolving download.microsoft.com... failed: Name or service not known.

macromedia and activex.microsoft.com - files downloaded fine...

the code is either outdated or microsofts servers are down....

TM
(hoping this will fix my problems with office 2003)

---

### Post by Bablefish on 2007-06-15
My question is WHY? I just had too many problems with IE and just plain don't use it ion my Win Pc

---

### Post by TravMan63 on 2007-06-15
I don't use it on my XP box either, but I do use the IE plugin/addon/extension for Firefox - some pages just will not load without it (microsoft update, and some school sites for example...)

And I'm guessing that Firefox NEEDS IE - to use it's rendering engine in that case

[https://addons.mozilla.org/en-US/firefox/addon/1419](https://addons.mozilla.org/en-US/firefox/addon/1419)
[http://johnhaller.com/jh/mozilla/firefox_internet_explorer/](http://johnhaller.com/jh/mozilla/firefox_internet_explorer/)

TM

---

### Post by TravMan63 on 2007-06-23
I got it going finally !!! :guitar:

'simple' as copying the required files over from a windows 98 install, and downloading a few other files...

unfortunately, it didn't fix my powerpoint problem... (still working on that)

TM

---

### Post by benivilch on 2007-06-24
it works (ubuntu 7.04). ty....

---

