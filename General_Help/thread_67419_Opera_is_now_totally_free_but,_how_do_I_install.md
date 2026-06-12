---
title: "Opera is now totally free but, how do I install?"
date: 2005-09-20
forum: General Help
---

### Post by Holdem on 2005-09-20
Opera web browser has now been released add free [http://www.opera.com/pressreleases/en/2005/09/20/](http://www.opera.com/pressreleases/en/2005/09/20/)
So I have downloaded the Ubuntu deb file from their website 
[http://www.opera.com/download/linux.html?platform=linux&x=170&y=20](http://www.opera.com/download/linux.html?platform=linux&x=170&y=20)
And have tried installing it via the shell but get a dependency error.
```
$ sudo dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb (Reading database ... 61752 files and directories currently installed.)
Preparing to replace opera 8.50-20050916.5 (using opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb) ...
Unpacking replacement opera ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3c102-mt; however:
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera
```
Can anyone advise how to rectify?

---

### Post by xaverx on 2005-09-20
free from banner and ads, but no free = freedom  [-X

---

### Post by macgyver2 on 2005-09-20
[QUOTE=Holdem]Can anyone advise how to rectify?[/QUOTE]
Yes, that .deb doesn't work.  According to another thread, [this one]("ftp://ftp.opera.com/pub/opera/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb") should.  I'm about to try it myself. :)

---

### Post by macgyver2 on 2005-09-20
[QUOTE=xaverx]free from banner and ads, but no free = freedom  [-X[/QUOTE]
Yet.  I suggest emailing them.  Maybe if enough of us do then someday it will be Free.  It's worth a try!

---

### Post by Holdem on 2005-09-20
[QUOTE=xaverx]free from banner and ads, but no free = freedom  [-X[/QUOTE]

Yawn. When was the last time you produced a piece of software for free. Less posturing and more solution this is a technical forum

---

### Post by aysiu on 2005-09-20
I just ran into this problem myself, actually. It's weird, because it didn't happen in the last version of Opera (which I downloaded only a couple of weeks ago).

Download [the dependency](http://ftp.us.debian.org/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb) to your desktop and ```
cd Desktop
sudo dpkg -i libqt3c102-mt_3.3.4-3_i386.deb
```

It may ask you to uninstall some other lib and programs that lib depends on (for me, that was Kolourpaint, KWord, and JuK), but that's okay.

Then sudo dpkg -i the opera .deb (I forget the full title of the .deb).

Then ```
sudo apt-get install
``` all the programs that got uninstalled.

---

### Post by Holdem on 2005-09-20
[QUOTE=macgyver2]Yes, that .deb doesn't work.  According to another thread, [this one]("ftp://ftp.opera.com/pub/opera/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb") should.  I'm about to try it myself. :)[/QUOTE]

OK thanks.

---

### Post by mario8723 on 2005-09-20
It installed great! Only problem I have now is trying to install Flashplayer?

---

### Post by kreek on 2005-09-20
[QUOTE=Holdem]Opera web browser has now been released add free [http://www.opera.com/pressreleases/en/2005/09/20/](http://www.opera.com/pressreleases/en/2005/09/20/)
So I have downloaded the Ubuntu deb file from their website 
[http://www.opera.com/download/linux.html?platform=linux&x=170&y=20](http://www.opera.com/download/linux.html?platform=linux&x=170&y=20)
And have tried installing it via the shell but get a dependency error.
```
$ sudo dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb (Reading database ... 61752 files and directories currently installed.)
Preparing to replace opera 8.50-20050916.5 (using opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb) ...
Unpacking replacement opera ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3c102-mt; however:
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera
```
Can anyone advise how to rectify?[/QUOTE]

When you select the distribution vendor, select "Other/Static DEB".
That one works just fine!  :smile:

---

### Post by Holdem on 2005-09-21
[QUOTE=kreek]When you select the distribution vendor, select "Other/Static DEB".
That one works just fine!  :smile:[/QUOTE]

Bingo, thanks for that.
 Had to enable Java which is easy, follow this [http://www.opera.com/support/search/supsearch.dml?index=459](http://www.opera.com/support/search/supsearch.dml?index=459)

Does anyone know how to make shortcuts? At the moment the only way to run Opera is from a command shell.

---

### Post by macgyver2 on 2005-09-21
[QUOTE=Holdem]Does anyone know how to make shortcuts? At the moment the only way to run Opera is from a command shell.[/QUOTE]
To get it in my Gnome menu I made a file called

/usr/share/applications/opera.desktop

Then (using the Firefox .desktop file as a guide) I put this in the file:
```
[Desktop Entry]
Encoding=UTF-8
Name=Opera Web Browser
Comment=Opera Web Browser
Exec=opera
Terminal=false
MultipleArgs=false
Type=Application
Icon=/usr/X11R6/include/X11/bitmaps/opera.xpm
Categories=Application;Network
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd;mozilla.xul+xml;application/rss+xml;application/rdf+xml;x-directory/webdav;x-directory/webdav-prefer-directory;image/gif;image/jpeg;image/png
```
I might tweak the MimeType thing, but other than that it shows up in the Applications --> Internet menu and works fine.

---

### Post by ogami1972 on 2005-09-21
Why use opera vs. firefox? (or mozilla, or epiphany, or konqueror, etc., etc.)
Seriously...

---

### Post by macgyver2 on 2005-09-21
[QUOTE=ogami1972]Why use opera vs. firefox? (or mozilla, or epiphany, or konqueror, etc., etc.)
Seriously...[/QUOTE]
Opera *flies* compared to firefox on my old notebook.  When I open multiple tabs in Firefox it hangs while rendering.  I even tried suggestions I found on sites about tweaking Firefox.  Epiphany is better.  I was using Epiphany for the past week.  Then I tried Opera when I heard about it being free (in price).  Huge improvement over both of them.

---

### Post by aysiu on 2005-09-21
[QUOTE=ogami1972]Why use opera vs. firefox? (or mozilla, or epiphany, or konqueror, etc., etc.)
Seriously...[/QUOTE] Opera's faster than Firefox.
I prefer Firefox, personally, for extensions and other things, but there are good reasons to use Opera if you want to use it.

---

### Post by Name on 2005-09-21
it wont open for me. I followed the instructions but for some reason it fails to open when I click the Icon...

---

### Post by Holdem on 2005-09-21
[QUOTE=Name]it wont open for me. I followed the instructions but for some reason it fails to open when I click the Icon...[/QUOTE]

I tried the intructions here 
[https://wiki.ubuntu.com/OperaBrowser?](https://wiki.ubuntu.com/OperaBrowser?)
But it didnt even give me an icon.

I have the icon in /usr/share/applications which works but how do I now get that in to Applications-Internet menu?

---

### Post by trash on 2005-09-21
Always use the static deb, as somebody already mentioned. I prefer Opera because if i close opera with many tabs open, upon next start it opens those tabs open, also the wand for remembering passwords is way more useful than other browsers i've tried.

Create a panel launcher for Opera:

sudo cp /usr/share/opera/images/opera.xpm /usr/share/pixmaps

then add to panel a custom application launcher and you will find an opera icon
for command just put in 'opera'

---

### Post by rwabel on 2005-09-21
for me the guide is working fine!
Only the part to open files lilke videos, pdf etc doesn't work as it should under gnome

Opera is much much faster than firefox. Firefox under Linux is still slow!! But extensions are great in firefox.

---

### Post by mario8723 on 2005-09-27
Still haven't figured out how to install Flashplayer in Opera. 

Started using it last week, and love it! I'm a big Firefox fan and have advocated it for a long time, but Opera is catching up if not surpassing it in my mind.

Just want to install Flashplayer and I will be complete.

Anybody?

---

### Post by jpkotta on 2005-09-27
[QUOTE=mario8723]Still haven't figured out how to install Flashplayer in Opera. 

Started using it last week, and love it! I'm a big Firefox fan and have advocated it for a long time, but Opera is catching up if not surpassing it in my mind.

Just want to install Flashplayer and I will be complete.

Anybody?[/QUOTE]

I assume you have already installed a flashplayer.  I use macromedia's (flashplugin-nonfree).  Find one of the directories that libflashplayer.so is installed in:
```
locate libflashplayer.so
```
Add one (or all) of them to the plugin path.  Do this with Tools -> Preferences -> Advanced -> Content -> Plugin Options...  (Yes, it's buried.  The preferences in opera 7 were much better.)

IMHO, opera was *always* ahead of mozilla and firefox.  Used to use mozilla before I found opera (this was before firefox).  I loved how stable it was but it was so *heavy*.  Opera was (and still is) fast and light.  It also has great features that work out of the box, and in most cases they work better than the mozilla equivalent.

---

### Post by bugmenot on 2005-09-27
People that can use the shared deb should prefer that over the static version. Only use static as fallback.
If you're using Breezy use this one [ftp://ftp.opera.com/pub/opera/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb](ftp://ftp.opera.com/pub/opera/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb) It's depending on the qt libs in Breezy. Don't replace those.

---

