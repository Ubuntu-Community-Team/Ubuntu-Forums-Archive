---
title: "Java Browser in 2019"
date: 2019-03-13
forum: General Help
---

### Post by timfinley on 2019-03-13
Hello, 

I've been running into some old hardware lately that still use Java applets for their web gui. I googled around to learn that Chrome and Firefox both nixed support for NPAPI support for Java applets, meaning I can't use Java on these browsers. I tried to install the plugin to Firefox regardless, but it's not working. Firefox doesn't recognize that the plugin is installed and Java doesn't work on their test site, nor does it work on my hardware's web gui.

Does anyone know a browser that still supports Java? I also learned that Opera is in the same boat as Chrome and Firefox, so I didn't even bother installing it. If not a different browser, is there a way to make Java work with the big three (Chrome, Firefox, or Opera)?

---

### Post by Holger_Gehrke on 2019-03-13
If the web GUI for those devices is contained in one applet, you might find some success using the appletviewer included in the JDK. See its manpage for details. If it's a mix of HTML, javascript and multiple applets you've got a problem ...
 
Holger

---

### Post by rred on 2019-06-23
> **timfinley said:**
> Hello, 

I've been running into some old hardware lately that still use Java applets for their web gui. I googled around to learn that Chrome and Firefox both nixed support for NPAPI support for Java applets, meaning I can't use Java on these browsers. I tried to install the plugin to Firefox regardless, but it's not working. Firefox doesn't recognize that the plugin is installed and Java doesn't work on their test site, nor does it work on my hardware's web gui.

Does anyone know a browser that still supports Java? I also learned that Opera is in the same boat as Chrome and Firefox, so I didn't even bother installing it. If not a different browser, is there a way to make Java work with the big three (Chrome, Firefox, or Opera)?

I had the same problem. My simple recipe: Firefox 51 (32-bit) under Wine 32-bit with "Windows version" = "Windows XP".

1) Install Wine and select 32-bit prefix

sudo apt-get install wine-stable
sudo apt-get install winetricks
export WINEARCH=win32

2) Run "winecfg" and set "Windows Version" to "Windows XP"

winecfg

3) Install ie8

winetricks ie8

4) Download Java 32-bit off-line installer from java.com and install it in "silent" mode from a terminal like so: 

wine jre-8u211-windows-i586.exe /s

5) Install Firefox 51 from winetricks

winetricks firefox 

6) Turn off Internet, start Firefox and disable auto-updates: Options / Advanced / Update >>> Never check for updates
7) Turn on Internet
8) Enjoy!

---

### Post by rred on 2019-06-24
More stable recipe: Firefox 33.0.3 (32-bit) under Wine with "Windows version" = "Windows XP" and Java 7

1) Install Wine

sudo apt-get install wine-stable

2) Run "winecfg" and set "Windows Version" to "Windows XP"

4) Install Java 7 Windows x86 Offline version ([https://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html)) from a terminal like so: 

wine jre-7u76-windows-i586.exe

5) Install Firefox 33.0.3 ([https://ftp.mozilla.org/pub/firefox/releases/33.0.3/win32/](https://ftp.mozilla.org/pub/firefox/releases/33.0.3/win32/)) like so:

wine Firefox Setup 33.0.3.exe

6) Type "wine control", double-click Java icon and set for Java "Security Level" to "Medium"
7) Before first start Firefox turn off Internet. Then start Firefox and disable auto-updates: Options / Advanced / Update >>> Never check for updates
8) Turn on internet and use stable Java Browser!

---

### Post by dragonfly41 on 2019-06-24
> [COLOR=#000000][INDENT]is there a way to make Java work with the big three (Chrome, Firefox, or Opera)?[/INDENT]
[/COLOR]


If you are open to some development work you could create an [Electron app (which is Chrome browser) with Java backend]("https://github.com/wuruoyun/electron-vue-spring"). 

I use [Atom editor]("http://atom.io") for Electron development.

---

