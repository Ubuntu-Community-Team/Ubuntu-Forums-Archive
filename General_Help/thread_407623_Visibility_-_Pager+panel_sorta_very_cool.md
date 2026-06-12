---
title: "Visibility - Pager+panel sorta very cool"
date: 2007-04-12
forum: General Help
---

### Post by jseiser on 2007-04-12
[http://projects.l3ib.org/visibility](http://projects.l3ib.org/visibility)

seen in this screenie 

[http://img517.imageshack.us/img517/5366/screenshotnf6.png](http://img517.imageshack.us/img517/5366/screenshotnf6.png)

and this one

[http://nano.fooo.org/screen-april.png](http://nano.fooo.org/screen-april.png)

the only problem is, i dont understand how to install it, and i cant find a How-To anywhere on the net :)  Can anyone explain how i get those files and install them?

---

### Post by dbbolton on 2007-04-12
it looks like you're going to have to wait until they compile some sort of package, unless you feel like downloading every file yourself and then building it from the ground up.

---

### Post by jseiser on 2007-04-12
[http://aur.archlinux.org/packages/visibility-svn/visibility-svn.tar.gz](http://aur.archlinux.org/packages/visibility-svn/visibility-svn.tar.gz)

i found that through the arch linux aur thing.  I also found it has 2 dependency's which i dont think are in ubuntu's repositories libpng and libsigc++2.0 

[http://www.libpng.org/pub/png/libpng.html](http://www.libpng.org/pub/png/libpng.html)
[http://ftp.gnome.org/pub/GNOME/sources/libsigc++/2.0/libsigc++-2.0.0.tar.gz](http://ftp.gnome.org/pub/GNOME/sources/libsigc++/2.0/libsigc++-2.0.0.tar.gz)

heh, i just dont know how to actually install those files :) i havent looked for a readme inside them yet, so ill post back.

---

### Post by dbbolton on 2007-04-12
oh, i didn't see that. well, this link should be helpful:

[http://www.monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://www.monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

---

### Post by jseiser on 2007-04-13
the file inside of the visibility folder are a PKGBILD and visibility-svn.install .  any idea how to install these.

---

### Post by russellc on 2007-04-16
You'll have to compile the source from SVN (you will need subversion). That package you found is for Arch Linux (or anything that uses the same packaging system). Here are the steps to building from SVN:

1) Create a folder to contain the source code you are about to download from the SVN repository (eg. mkdir ~/Source, whatever you want)
2) Navigate to that folder in the terminal (cd ~/Source or whatever folder you created)
3) Download the source. Using the following command you will checkout the latest source from their SVN repository:```
$ svn checkout http://svn.l3ib.org/visibility/trunk/ visibility
```
4) Navigate to the newly created visibility folder (cd visibility).
5) Make sure dependencies are satisfied (including their development files, usually named with an appending *-dev suffix in the package name) > A list of dependencies and the versions that work for me:

* libpng 1.2.12
* xlib from Xorg 7.0
* libxft 2.1.10
* libsigc++ 2.0.17 (quoted from DEPENDENCIES file)

6) Generate configure script: ```
$ ./bootstrap
```
7) Run configure script: ```
$ ./configure
```  (include any extra flags you would like to set, like --prefix and such.. you can check existing flags by performing ./configure --help)
8 ) If all goes well, compile the source: ```
$ make
```
9) If no compilation errors, install the binaries: ```
# make install
```

Note: # denotes the need for superuser/root privilages. $ denotes regular user privilages.

Hope all that helps!

---

### Post by jseiser on 2007-04-16
tried what you said, go to this part and had a problem

justin@justin-desktop:~/source/visibility$ ./bootstrap
Running autoreconf.
./bootstrap: 3: autoreconf: not found
You can now run ./configure. Enjoy!
justin@justin-desktop:~/source/visibility$ ./configure
bash: ./configure: No such file or directory


synaptic'd autoconf

tried again

justin@justin-desktop:~/source/visibility$ ./bootstrap
Running autoreconf.
autoreconf: failed to run aclocal: No such file or directory
You can now run ./configure. Enjoy!
justin@justin-desktop:~/source/visibility$ ./configure
bash: ./configure: No such file or directory

---

### Post by russellc on 2007-04-16
Do you have the primary dependencies needed for building software from source such as the build-essential package?

EDIT: I just found that aclocal is provided by the automake package, so when you get that package, it'll probably work alright.

---

### Post by Meatcart on 2007-07-19
I can't find anything of Visibility anymore, the SVN is down and such. The domain appears to be mostly gone as well..

The only things that are still working is this page [http://projects.l3ib.org/](http://projects.l3ib.org/) and the Trac pages, but the svn sites and stuff are all gone.

Anybody know where to look for it now? I really want this on my openbox lol.

---

### Post by urukrama on 2007-07-19
the source code was posted in the random openbox chatter thread. Let's see if I can find it again.

EDIT: See [here.]("http://ubuntuforums.org/showpost.php?p=2581526&postcount=217")

---

### Post by Meatcart on 2007-07-19
Ah, thanks alot! :D I'm glad it was still around somewhere..  again thanks :)

---

### Post by urukrama on 2007-07-19
Btw are you sure svn is down? In order to use it you need to install the subversion package:

```
sudo apt-get install subversion
```

Then do 

```
svn checkout http://svn.l3ib.org/visibility/trunk/ visibility
```

and you will have the source in your home directory.

---

### Post by Meatcart on 2007-07-19
Yeah, I know about subversion.. I'm using it for alot of other apps too.

It wasn't working for me earlier, I've tried nitrogen as well. But that seems to work as well now too.. Weird ><; Anyhows, thanks again.. I'll go use the SVN version :)

Sorry for the trouble.

---

### Post by dbbolton on 2007-07-22
i decided to try this out. when i run ./configure, it tells me that my c++ compiler can't create executables. build-essential is installed, and i upgraded g++ to version 4.1. which compiler do i need to install?

---

### Post by Meatcart on 2007-07-22
You also need to install the following and **also** their -dev versions if there are any : 

- libpng 1.2.12
- xlib from Xorg 7.0
- libxft 2.1.10
- libsigc++ 2.0.17

---

### Post by dbbolton on 2007-07-22
> **Meatcart said:**
> You also need to install the following and **also** their -dev versions if there are any : 

- libpng 1.2.12
- xlib from Xorg 7.0
- libxft 2.1.10
- libsigc++ 2.0.17
i wasn't having dependency issues. i was having problems with the compiler. 

i just did "sudo apt-get install g++" and it works.

---

### Post by picpak on 2007-08-10
Thanks to this topic, I've managed to get visibility installed and working. I've attached a .deb at the bottom of this post.

To compile it from source:

1) Install the following programs:

```
sudo apt-get install libapr1 libaprutil1 libexpat1-dev libfontconfig1-dev libfreetype6-dev libice-dev libneon26 libpng12-dev libpq5 libsigc++-dev libsigc++0c2 libsm-dev libsvn1 libx11-dev libxau-dev libxdmcp-dev libxext-dev libxft-dev libxi-dev libxmu-dev libxmu-headers libxmuu-dev libxpm-dev libxrandr-dev libxrender-dev libxt-dev libxtrap-dev libxtst-dev libxv-dev pkg-config subversion x-dev x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-trap-dev x11proto-video-dev x11proto-xext-dev xlibs-dev xtrans-dev zlib1g-dev autoconf automake g++ g++-4.1 gcc libstdc++6-4.1-dev checkinstall libsigc++-2.0-dev
```

2) [Download Visibility](http://ubuntuforums.org/attachment.php?attachmentid=31598&d=1178144118) and then run:

```
tar -xvf visibility.tar.gz
cd visibility
```

3) Generate the configure script: 
```
./bootstrap
```

4) Run the configure script: 

```
./configure --prefix=/usr
```

5) If all goes well, then run:

```
make
sudo checkinstall -D
```

Enjoy!

For the lazy ones, just use this deb: v

---

### Post by chochem on 2008-04-29
Thanks, picpak - the .deb worked beautifully. Since the developers has obviously abandoned it and even the documentation is gone, I had some problems configuring it (no --help, no man, no web page). However [somebody]("http://enjoy4fun.cn/blog/archives/2007/12/visibility.html") left a sample config file on his/her blog. I'll just copy it here for the sake of preservation:

```
# a sample config file for visibility.
# this file goes in ~/.config/visibility/config
# it can be used to set a theme and override specific options.
# uncomment this option to use the theme 'magicaltheme'
# themes are stored in ~/.themes/theme_name/visibility/theme
# theme syntax is identical to the syntax of this config file.
# (yes, a theme could 'inherit' from another theme by specifying a theme!)
#theme magicaltheme
orientation top_right    # set this to the corner of the desktop that you
                            # would like visibility to be placed. valid options:
                            # top_left, top_right, bottom_left, bottom_right
gap_x 2                  # the amount of space to leave between the pager and
                           # the side of the desktop.
gap_y 2                    # the amount of space to leave between the pager and
                            # the top or bottom of the desktop.
image_size 16               # the pixel size of an icon; icons are square.
spacing 5                   # the amount of space to leave between icons as well
                            # as between the edge of the window and the icons.
border_width 1              # the width of the border around the window. can be 
                            # set to 0 if your window manager (like openbox!) 
                            # can provide its own borders for borderless
                            # windows.
desktop_separation 20       # the amount of space to leave between desktops.
show_desktop_names true     # whether or not to show desktop names. these names
                            # are specified by your window manager. valid
                            # options are 'true' and 'false'.
single_desktop_mode false   # whether or not to show only windows from the
                            # current desktop.
#bg_colour 4c4c4c            # the background colour
bg_colour 000000
border_colour FFFFFF        # the border colour
active_text_colour ffffff   # the colour of the name of the active desktop.
inactive_text_colour 888888 # the colour of the name an inactive desktop.
font nu                     # the name of the font to use. this is an xft name,
                            # so one could use 'verdana:pixelsize=10' or
                            # 'verdana-10'.
inactive_bg_colour 000000   # the background colour of inactive desktops.
active_bg_colour 000000     # the background colour of active desktops.
                            # if you hate this setting, set it to the same as
                            # bg_colour and inactive_bg_colour, and you will
                            # probably be a happy camper.
set_partial_strut false     # whether or not to reserve space on the desktop
                            # edge. this is useful if you do not want windows
                            # to maximize over visibility.
set_window_type true        # if true, visibility sets itself to be of 'dock'
                            # type, which is meant for panels. this is useful if
                            # you want it to be 'always on top', and other
                            # panel-like things.
tooltip_padding 3           # the amount of padding to have inside tooltips.
tooltip_time 0.5            # the number of seconds before a tooltip shows up.
tooltip_bg_colour 000000    # the tooltip background colour.
tooltip_border_colour ffffff# the tooltip border colour.
tooltip_text_colour ffffff  # the colour of text in tooltips
tooltip_font nu             # the font to use in tooltips
text_spacing 6              # the amount of spacing to leave between the
                            # desktop name and first icon.
active_tint 000000          # the colour to tint the active window with
active_tint_amount 0        # the amount to tint the active window (0..1)
inactive_tint ffffff        # the colour to tint inactive windows with
inactive_tint_amount 0.3    # the amount to tint active windows (0..1)
iconified_tint 0            # the colour to tint iconified (and 'hidden')
                            # windows with
iconified_tint_amount 0.55  # the amount to tint iconified windows (0..1) 
```

---

### Post by chochem on 2008-07-10
In case anybody else has had/will have /might will have had the problem in getting visibility to appear on all desktops (sticky) that I've had, I've found a solution of sorts. Running two instances of visibility should do the trick for the some bizarre reason.

```
#! /bin/bash

if [ -z "$(pgrep [v]isibility)" ]; then
	visibility &
	visibility &
else
	killall visibility
fi

```

---

