---
title: "Howto: Make Qt/KDE apps look like Gnome ones!"
date: 2008-06-19
forum: General Help
---

### Post by Vadi on 2008-06-19
A while ago something called [QGtkStyle]("http://labs.trolltech.com/page/Projects/Styles/GtkStyle") was announced - it makes your Qt/KDE programs look similarly to GTK ones. But there were no easy .debs for a long while, so I decided to make my own. They aren't top-notch quality, but they've been tested on several machines, and they do work. (If you can make better quality ones, please let me know).

[CENTER][SIZE="5"]Install[/SIZE][/CENTER]

If you're on **32bit Ubuntu**, or you don't know download and install this ([click, and download *gtkstyle-unofficial-0.1-i386.deb*]("http://drop.io/qgtkstyleIvadi"))

If you're on **64bit Ubuntu**, download and install this ([click, and download *gtkstyle-unofficial-r850-amd64.deb*]("http://drop.io/qgtkstyleIvadi"))

[CENTER][SIZE="5"]Apply the theme[/SIZE][/CENTER]

Go to System - Preferences - Qt4 Settings, and choose GTK for the GUI style. Then press File - Save. 
[B]
That's it![/B] Your Qt and KDE programs should now take on the look of your GTK theme.

[CENTER][SIZE="4"]Skype issues[/SIZE][/CENTER]

If Skype isn't obeying your theme, try starting it by pressing Alt+F2, and typing "skype --disable-cleanlooks". It should remember your choice after this. ([via]("http://ubuntuforums.org/showpost.php?p=6178608&postcount=34"))

---

### Post by kahlil88 on 2008-08-05
Oddly enough, I can't seem to find the Qt4 Settings even though it's installed.

---

### Post by Vadi on 2008-08-05
It should be in System - Preferences.

---

### Post by kahlil88 on 2008-08-05
Right, but for some reason it isn't. I tried opening the Menu Editor to see if it had been disabled, but it doesn't even show up as a disabled program. I might have deleted it, or just forgot to install the configuration tool. What's the command to just run it?

---

### Post by Vadi on 2008-08-05
"qtconfig-qt4"

---

### Post by kahlil88 on 2008-08-05
Hmmm...I installed qt4-qtconfig and followed your instructions, but the only program that actually uses the GTK theme is the qtconfig program...

---

### Post by Vadi on 2008-08-05
Qt 3 programs, KDE 3 programs aren't affected by this. Purely Qt 4 ones should, KDE 4 ones will... do it half-way because KDE is odd like that.

---

### Post by MasterProg on 2008-08-22
I suggest making an universal package with both 32 bit and 64 bit versions included. That would allow 32 bit applications to use this style on 64 bit Ubuntu.

One last thing to mention. Libraries in the packages you have made have debugging information. Is it really necessary? It is possible to reduce their size.

---

### Post by Vadi on 2008-08-22
Ubuntu splits it's packages by architecture, so I'm going with that...

And this is really in alpha stages, so debugging info is there in case someone is told to use gdb or something on this. Feel free to recompile for yourself though if you worry about it :)

---

### Post by Mikebo on 2008-09-18
It looks great but I can't change the default font in qt-config.

---

### Post by jensbw on 2008-09-18
> **Mikebo said:**
> It looks great but I can't change the default font in qt-config.

You can't because the font is currently controlled by your current GTK settings and not qtconfig while using QGtkStyle. If you change your application font in GNOME, your Qt apps shoul respect that.

---

### Post by Saint Angeles on 2008-09-18
> **Vadi said:**
> Qt 3 programs, KDE 3 programs aren't affected by this. Purely Qt 4 ones should, KDE 4 ones will... do it half-way because KDE is odd like that.

is there a kde3 version?

i'd like amarok to look like my gtk theme.

---

### Post by Vadi on 2008-09-18
No kde 3 or kde 4 versions, sorry. Kde is annoying like that and overrides Qt settings.

(if a mod could fix the title, that would be great. I didn't realize that the time of writing)

---

### Post by Mikebo on 2008-09-18
> **jensbw said:**
> You can't because the font is currently controlled by your current GTK settings and not qtconfig while using QGtkStyle. If you change your application font in GNOME, your Qt apps shoul respect that.

I've set Trebuchet MS for my gnome apps, but qgtk usues a different font (I think it's Sans)

Update on the font problem:
instead of using the deb i've compiled the style from svn and it now respects my gnome font setting.

---

### Post by rimmugygur on 2008-09-18
Does anybody howto make skype use your gtk theme. I have installed it through mediubuntu repositery but it seems that skype only changes it is fonts. I have tried starting it with --disable-cleanlooks but that only makes look even worse. Any advise?

---

### Post by Mikebo on 2008-09-18
> **rimmugygur said:**
> Does anybody howto make skype use your gtk theme. I have installed it through mediubuntu repositery but it seems that skype only changes it is fonts. I have tried starting it with --disable-cleanlooks but that only makes look even worse. Any advise?

I think that skype in medibuntu i slightly modified (static qt?). Maybe try a deb from skype website.

---

### Post by rimmugygur on 2008-09-18
Thanks for the advise, but I am running 64-bit Ubuntu Hardy and they only have 32-bit versions available.

---

### Post by rolandixor on 2008-09-20
How do you compile this from svn? I tried and tried, but qmake, qmake && make, and make alone, all give me a silly error about different styles not being declared, bla bla.

Can someone make a deb from the SVN version?
isn't it just an .so that someone can upload? and how long till QT 4.5?

---

### Post by Vadi on 2008-09-20
> **rimmugygur said:**
> Thanks for the advise, but I am running 64-bit Ubuntu Hardy and they only have 32-bit versions available.

Umm... did you check the first post of this thread?

@rolandixor: I'll update the .debs soon.

---

### Post by rimmugygur on 2008-09-25
Yeah, thanks for the deb but I was referring to the skype pakage on their own webpage.

---

### Post by Vadi on 2008-09-25
Aa... add the [Medibuntu]("http://www.medibuntu.org/") repository, then you can install Skype.

---

### Post by Vadi on 2008-09-25
For some strange reason, the 64bit version compiled fine, but the 32bit one gives an error.

---

### Post by ukdmbfan on 2008-10-01
Bit of a problem - for some reason I cannot get the Gtk theme to appear under "Select GUI Style" in qt4-config.

sudo make install wanted to install the theme under /usr/local/Trolltech/Qt-4.4.2-snapshot-20080904/plugins/styles and I also copied the file to /usr/lib/qt4/plugins/styles but neither seems to have any effect. Should this file be somewhere in particular for qt4-config to pick it up and use it?

---

### Post by Vadi on 2008-10-01
See where other styles are installed, and try placing it into there?

---

### Post by conscious on 2008-10-29
Are these debs for Hardy only? I'd like to install QGtkStyle on Intrepid.
Also, you can set up a PPA in Launchpad so that people can install QGtkStyle with apt/Synaptic and receive updates via Update Manager.

---

### Post by Vadi on 2008-10-29
I can't setup a PPA, I don't know how to do one (and learning one is a very, very complex process which I don't have time for).

Intrepid, hmm I'm not sure.

---

### Post by rebegin on 2008-10-30
> **Vadi said:**
> I can't setup a PPA, I don't know how to do one (and learning one is a very, very complex process which I don't have time for).

Intrepid, hmm I'm not sure.

i'm running it on xubuntu intrepid, works great, the only problem that whenever a qt4 program started, my desktop background disappears, so i have to run xfdesktop to get it back(anyway i had this problem on hardy too...).
any solution for that?
great app. by the way ;)

---

### Post by Vadi on 2008-10-30
No idea. I didn't make the app; it's made by a Qt employee: [http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/](http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/)

---

### Post by rebegin on 2008-11-01
i installed it from svn it works fine now :D

in case someone else has the same poblem with the deb installed on the top of this thread, here's how you can install itt from svn:

```
sudo apt-get install libgtk2.0-dev libqt4-dev build-essential libqt4-dev subversion checkinstall
```

```
svn co svn://labs.trolltech.com/svn/styles/gtkstyle
```

```
cd gtkstyle/
```

```
qmake && make
```

```
checkinstall
```

```
sudo dpkg -i gtkstyle<TAB>
```

---

### Post by rebegin on 2008-11-01
> **kahlil88 said:**
> Hmmm...I installed qt4-qtconfig and followed your instructions, but the only program that actually uses the GTK theme is the qtconfig program...

you can make it work like this:

```
sudo apt-get install kdebase-workspace systemsettings
```
it installs some other packages but then you can find systemsettings in the menu and change the theme and colors as you want easily.

---

### Post by mexlinux on 2008-11-07
I can confirm
This debs also work on intrepid ibex 8.10

---

### Post by morgengenuss on 2008-11-13
hey, just wanted to give quick feedback on the .deb package in the first post.
i installed the 32bit version in xubuntu intrepid and within qt4config everything seems fine. in skype (installed through the skype-repos, not medibuntu) the scrollbars still have that qt-look. any idea why that is?

(btw, the gtk-theme i'm using is murrine-svn, just in case this matters.)

---

### Post by morgengenuss on 2008-11-13
ok, sorry, now it works. for some reason i had to restart skype a few times and fiddle a bit in the menu of qt4config (even though i didn't change anything).

_________________________


edit: well. actually. there's an issue. if i change the settings in qtconfig (e.g. the font) and then click "save", skype gets the gtk-theme applied. on restart of skype all those changes are gone again. wtf? (even tried running qtconfig as root, just to be sure it could save the changes.)

---

### Post by morgengenuss on 2008-11-14
found the solution myself just now: you have to add the commandline-switch "-- disable-cleanlooks" as it is hardcoded in skype. then the qt-style gets applied correctly and skype "remembers" it at each startup...

---

### Post by Vadi on 2008-11-14
Glad you got it working.

---

### Post by flamepanther on 2008-11-17
Looks like I got to this thread a bit late. Mediafire says the files are no longer available.

---

### Post by ellalan on 2008-11-18
> **flamepanther said:**
> Looks like I got to this thread a bit late. Mediafire says the files are no longer available.
I checked this morning and its still available, could you try again please.

---

### Post by Vadi on 2008-11-18
I made an updated package for 64bit, however 32bit is refusing to compile:

```
$ make
g++ -c -pipe -fpermissive -g -fvisibility=hidden -fvisibility-inlines-hidden -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -D_REENTRANT -Wall -W -fPIC -DQT_SHARED -DQT_PLUGIN -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o main.cpp
In file included from main.cpp:24:
qgtkstyle.h:35: error: expected constructor, destructor, or type conversion before ‘typedef’
In file included from /usr/include/qt4/QtCore/qplugin.h:48,
                 from /usr/include/qt4/QtGui/qstyleplugin.h:47,
                 from /usr/include/qt4/QtGui/QStylePlugin:1,
                 from main.cpp:25:
/usr/include/qt4/QtCore/qpointer.h:51: error: expected constructor, destructor, or type conversion before ‘typedef’
make: *** [main.o] Error 1
```

Any ideas?

---

### Post by eternalnewbee on 2008-11-18
I downloaded the package and got this message (see screenshot)

---

### Post by Vadi on 2008-11-18
Firefox bugs out like that sometimes. Right-click and use 'save as' to download the .deb, then double-click on it.

---

### Post by eternalnewbee on 2008-11-18
> Firefox bugs out like that sometimes. Right-click and use 'save as' to download the .deb, then double-click on it.
You see, this is a typical example of why Ubuntu is a success! It's the community that rocks! Thanks vadi=D>

---

### Post by eternalnewbee on 2008-11-18
So, Ive succeeded in installing the program, but when running the command "qtconfig-qt4" I get this message:

(<unknown>:8812): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:8812): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(<unknown>:8812): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:8812): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed
Any idea what that means?

---

### Post by Vadi on 2008-11-18
Does it come up though?

---

### Post by eternalnewbee on 2008-11-18
> Does it come up though?
I'm going to make a fool of myself now.
Before my previous post I was already starting to scratch my head. **"Make Qt/KDE apps look like Gnome ones!"**.
But... I'm running Gnome!!! There you go. laugh](*,)
I decided to post any way, because I've got KDE installed, and a lot of KDE apps are present.:)
So yes, it's running, but nothing changes.

---

### Post by funkydan2 on 2008-11-19
@eternalnewbee - don't bash your head.  I think this is exactly what you want.  This thread is meant to help you run your KDE/QT apps in gnome, so that they look like the rest of your Gnome.  (So, you can be using gnome as your desktop environment, but have programs like Skype look like the rest of your programs.)

I'm not sure if having KDE installed fully on your system would make any differences...

---

### Post by eternalnewbee on 2008-11-19
Why thanks for boosting my confidence;)

---

### Post by jensbw on 2008-11-19
> **eternalnewbee said:**
> So, Ive succeeded in installing the program, but when running the command "qtconfig-qt4" I get this message:

(<unknown>:8812): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:8812): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

Any idea what that means?

I'm guessing you are running the Murrine GTK engine as the warning sounds like it's coming from the fact that your theme is detecting if it should use RGBA textures. I believe you will not get this warning if you compile the style directly from svn as opposed to using the latest package.

---

### Post by morgengenuss on 2008-11-29
@Vadi: just a quick note. you have a typo in your section "Skype Issues" in the first post of this thread. instead of "skype -- disable-cleanlooks" it should be "skype --disable-cleanlooks".
/typo

---

### Post by Vadi on 2008-11-29
Thanks, fixed

---

### Post by RPG Master on 2009-08-18
Well, VLC looks nice and GTK-ish but Digikam stays the same... whats wrong?

---

### Post by exoren22 on 2010-06-01
YAY!! I just want to comment that the amd64 package still works with (X)ubuntu 10.04 Lucid, for anybody who stumbles upon this at another time in the future. VLC looks native again!!!! And also, it's worth noting that Skype no longer requires this to look normal in GTK environments. 

Again, THANKS!!

---

### Post by osfight.de on 2010-09-21
I cannot make it work. I did set in qtconfig4 and systemsettings the style option to GTK+ and in both preview windows my Gnome style is shown correctly (see the first two screenshots). However, either Mathematica nor Skype are using the Gnome theme. What am I doing wrong?

thanks for help

> **exoren22 said:**
> YAY!! I just want to comment that the amd64 package still works with (X)ubuntu 10.04 Lucid, for anybody who stumbles upon this at another time in the future. VLC looks native again!!!! And also, it's worth noting that Skype no longer requires this to look normal in GTK environments. (the --disable-cleanlooks shows no effect)

Again, THANKS!!

That it interesting, because since QT 4.4 or so qgtkstyle is automatically included, so it should be working without the unofficial package. I tried manually installing it too, but had no success.

---

