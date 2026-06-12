---
title: "GIMP Crashes Instantly"
date: 2014-08-04
forum: General Help
---

### Post by Giana_Jinx on 2014-08-04
I have Ubuntu 14.04 on what used to be a Windows 7 laptop. I have no partition. Windows is absolutely gone. When I first got Ubuntu, I was thrilled to hear that I can get my beloved GIMP. However, every time I would try to start it, it would load for a few seconds and give me that blue splatter saying it crashed, asking me if I want to relaunch or send an error report. It would always do that. I just left it alone. I REALLY need to use GIMP right now because it is my best choice for what I have to edit, and it still does not work. Earlier today, it gave me that blue splat a couple times and relaunch obviously does not work. My cursor just loads for 10-20 seconds and nothing happens. Now, I am not even getting an error. The cursor just loads for 10-20 seconds and stops. I uninstalled GIMP and reinstalled it twice today, and no more error message. It just loads and stops. I have no idea what to do. I need GIMP and I do not even know what the problem is. I only have this computer. I am really hoping someone can help me. If I were still getting that error report, I could tell you the details, but I am not getting anything anymore but a few seconds of loading. Also, if you are going to walk me through the steps and know how to fix this, please dumb it down as much as possible because I am not very familiar with Ubuntu like I am with Windows. Ubuntu is just upsetting me so much lately with all this trouble it gives me.

---

### Post by Giana_Jinx on 2014-08-04
Bump. I really, really need help. Really. I have tried every other photo editor available, Linux and online, and I just need GIMP.

---

### Post by tgalati4 on 2014-08-04
Welcome to the forums and we're glad that you have rediscovered gimp under linux.  There are several things you can do.  Open a terminal:

```
gimp -h
gimp --stack-trace-mode=always

```  

Cut and paste any errors into this thread.

Understand that if you have reinstalled gimp a few times and it still doesn't work, then perhaps it is another framework that is broken.  gimp is built using a bunch of frameworks and if one of those frameworks is broken, then gimp will be broken.

> tgalati4@Mint14-Extensa ~ $ apt-cache depends gimp
gimp
  Depends: libgimp2.0
  Depends: libgimp2.0
  Depends: gimp-data
  Depends: gimp-data
  Depends: python-gtk2
  Depends: libaa1
  Depends: libbabl-0.1-0
  Depends: libbz2-1.0
  Depends: libc6
  Depends: libcairo2
  Depends: libdbus-1-3
  Depends: libdbus-glib-1-2
  Depends: libexif12
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libgdk-pixbuf2.0-0
  Depends: libgegl-0.2-0
  Depends: libglib2.0-0
  Depends: libgs9
  Depends: libgtk2.0-0
  Depends: libgudev-1.0-0
  Depends: libjasper1
  Depends: libjpeg8
  Depends: liblcms1
  Depends: libmng1
  Depends: libpango1.0-0
  Depends: libpng12-0
  Depends: libpoppler-glib8
  Depends: librsvg2-2
  Depends: libtiff5
  Depends: libwebkitgtk-1.0-0
  Depends: libwmf0.2-7
  Depends: libx11-6
  Depends: libxcursor1
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxmu6
  Depends: libxpm4
  Depends: zlib1g
  Depends: python
  Depends: python2.7
 |Suggests: gimp-help-en
  Suggests: <gimp-help>
    gimp-help-de
    gimp-help-en
    gimp-help-es
    gimp-help-fr
    gimp-help-it
    gimp-help-ko
    gimp-help-nl
    gimp-help-nn
    gimp-help-pl
    gimp-help-ru
    gimp-help-sv
  Suggests: gimp-data-extras
  Suggests: gvfs-backends
    gvfs-backends:i386
  Suggests: libasound2
    liboss4-salsa-asound2
  Recommends: ghostscript
    ghostscript:i386
  Breaks: gimp-plugin-registry
  Breaks: gimp-plugin-registry:i386
  Replaces: gimp-plugin-registry
  Replaces: gimp-plugin-registry:i386
  Conflicts: gimp:i386


---

### Post by Giana_Jinx on 2014-08-05
I got:

gimp: fatal error: Segmentation fault

---

### Post by ibjsb4 on 2014-08-05
You can also try opening gimp in terminal and see if will give you more info to go on.
```
gimp
```

---

### Post by Giana_Jinx on 2014-08-05
When I tried to open from the terminal, I got:

Segmentation fault (core dumped)


Can someone tell me what this means?

---

### Post by ibjsb4 on 2014-08-05
> When I tried to open from the terminal, I got:
Segmentation fault (core dumped)
Can someone tell me what this means?
A short answer would be unauthorize memory access.

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

Did you install gimp using the software center or did you install using a different method?

You say that you also reinstalled gimp.  Did you also purge it?

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by tgalati4 on 2014-08-05
Run *memtest* from the grub bootup menu.  You might have some faulty RAM.  Clean out your machine and reseat the RAM sticks.

---

### Post by ibjsb4 on 2014-08-05
> **tgalati4 said:**
> Run *memtest* from the grub bootup menu.  You might have some faulty RAM.  Clean out your machine and reseat the RAM sticks.
Good call :)

---

### Post by Giana_Jinx on 2014-08-05
I did purge Gimp before I reinstalled. I reinstalled so many times trying to get it to work. I've done it via terminal and Software Center.

---

### Post by Giana_Jinx on 2014-08-05
I'm sorry, but I'm Linux illiterate. What is this "grub bootup menu" and how do I get there?

---

### Post by Giana_Jinx on 2014-08-05
Also, if I clear out the RAM or whatever you're asking me to do, will this affect anything else in my system or make me lose data and/or personal files?

---

### Post by Giana_Jinx on 2014-08-05
I ran a memtest and it told me that everything was fine and I had no errors.

---

### Post by ibjsb4 on 2014-08-05
> **Giana_Jinx said:**
> Also, if I clear out the RAM or whatever you're asking me to do, will this affect anything else in my system or make me lose data and/or personal files?
When you first boot up your computer you get a screen that looks something like this
[ATTACH=CONFIG]255272[/ATTACH]
Pick the first memory test and this will check all your ram for defects.
This is a test and will not harm your system.
Also this test usually takes a long time to run.  I suggest you start it at night and see what results you have in the morning.

[COLOR=#ff0000]Edit:[/COLOR] Looks like [COLOR=#ff0000]our[/COLOR] timing is in sync :)

---

### Post by Giana_Jinx on 2014-08-05
I suppose it is in sync!

---

### Post by ibjsb4 on 2014-08-05
Ok, I been looking through here

[https://www.google.com/search?client=ubuntu&channel=fs&q=Segmentation+fault+gimp&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Segmentation+fault+gimp&ie=utf-8&oe=utf-8)

Some older post suggest it could be the theme.  May be worth trying.  There are other ideas too, take a look for yourself.

This one looks good

[https://forum.manjaro.org/index.php?topic=1932.0](https://forum.manjaro.org/index.php?topic=1932.0)

Try opening gimp in your guest account.

---

### Post by Giana_Jinx on 2014-08-05
Dude, it opened in Guest /: . Do you know why that is?

---

### Post by tgalati4 on 2014-08-06
Did you add any personal themes or other customizations to your account?  It's possible the guest account is "clean" and therefore *gimp* runs OK.  What customizations have you done recently?

As suggested by ibjsb4:

```
cd
ls -la .gimp*
```

It should look something like:

> 
tgalati4@Mint14-Extensa ~ $ cd
tgalati4@Mint14-Extensa ~ $ ls -la .gimp*
total 528
drwxr-xr-x 24 tgalati4 tgalati4   4096 Jul 28 19:49 .
drwxr-xr-x 59 tgalati4 tgalati4   4096 Jul 28 19:49 ..
drwxr-xr-x  2 tgalati4 tgalati4   4096 Jul 28 19:43 brushes
-rw-------  1 tgalati4 tgalati4    739 Jul 28 19:49 colorrc
-rw-------  1 tgalati4 tgalati4   1863 Jul 28 19:49 controllerrc
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 curves
-rw-------  1 tgalati4 tgalati4    343 Jul 28 19:49 dockrc
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 dynamics
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 environ
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 fonts
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 fractalexplorer
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 gfig
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 gflare
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 gimpressionist
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 gradients
-rw-r--r--  1 tgalati4 tgalati4    430 Apr  1  2013 gtkrc
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 interpreters
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 levels
-rw-r--r--  1 tgalati4 tgalati4  77320 Jul 28 19:49 menurc
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 modules
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 palettes
-rw-------  1 tgalati4 tgalati4    102 Jul 28 19:49 parasiterc
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 patterns
-rw-r--r--  1 tgalati4 tgalati4 280885 Jul 28 19:42 pluginrc
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 plug-ins
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 scripts
-rw-------  1 tgalati4 tgalati4   1956 Jul 28 19:49 sessionrc
-rw-r--r--  1 tgalati4 tgalati4  34483 Jul 28 19:49 tags.xml
-rw-------  1 tgalati4 tgalati4   4817 Jul 28 19:49 templaterc
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 templates
-rw-r--r--  1 tgalati4 tgalati4    312 Jul 28 19:42 themerc
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 themes
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 tmp
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 tool-options
drwxr-xr-x  2 tgalati4 tgalati4   4096 Apr  1  2013 tool-presets
-rw-------  1 tgalati4 tgalati4   3996 Jul 28 19:49 toolrc
-rw-------  1 tgalati4 tgalati4   1178 Jul 28 19:49 unitrc


---

### Post by keitai1948 on 2014-10-27
I had exactly the same problem. After trying many things at random what finally worked for me was simply going to the terminal and typing

```
gimp-console
```

This command did not show anything and blocked the terminal. So after waiting for some 3 minutes, I did a Control+C to terminate the process and now magically Gimp works fine!

---

