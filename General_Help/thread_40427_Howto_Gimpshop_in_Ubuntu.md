---
title: "Howto: Gimpshop in Ubuntu"
date: 2005-06-09
forum: General Help
---

### Post by radhaz on 2005-06-09
The basis of this howto lies with the howto found on this [page](http://linux.suramya.com/tutorials/Install_GIMPShop/ unfortunately)   which unfortunately didn't work for me out of the box so I am going to share my adaptation of it so that Ubuntu users can enjoy GimpShop for themselves.  

*DISCLAIMER* I'm not the sharpest tool in the shed and while this process worked for me it's entirely possible it won't work for you.  Most of us mean to backup our data often but few of us truly do.  Before you undertake this make sure you backup anything you might miss.

1.  Using synaptic download and install the following packages:

checkinstall
libxml-parser-perl
libglib*-dev (Where * is the version of libglib that is currently installed and >= 2.4.5)
libatk*-dev (Where * is the version of libatk that is currently installed and >= 1.0.1)
libgtk*-dev (Where * is the version of libgtk that is currently installed and >= 2.4.4)
libart-*-dev (Where * is the version of libart that is currently installed and >= 2.0)
libjpeg*-dev (Where * is the version of libjpeg that is currently installed)
libpng*-dev (Where * is the version of libpng that is currently installed)
libtiff*-dev (Where * is the version of libtiff that is currently installed)
libgimpprint*-dev (Where * is the version of libgimpprint that is currently installed)

2.  Now uninstall the following packages:

Gimp
libgimp2.0 gimp-data

3. Download the sourcecode for GimpShop from this [page](http://plasticbugs.com/index.php?p=241) 

4. Open a terminal and run the following in the directory where you downloaded the source.

```

tar -jxf GIMPshop-source-2.*.tbz
cd gimp-2.2*
./configure --prefix=/usr
make
sudo checkinstall

```         *Upon completion you will truly appreciate rpm's & deb packages.*

5. Run the program from by typing

```

/usr/bin/gimp

``` 

Enjoy!  Feel free to leave feedback/streamlining the process etc.

---

### Post by bored2k on 2005-06-09
Why don't you use sudo check install instead of make install ?
> checkinstall — generate packages by tracking installation scripts(debian maintained, in other words).

---

### Post by radhaz on 2005-06-09
[QUOTE=bored2k]Why don't you use sudo check install instead of make install ?
(debian maintained, in other words).[/QUOTE]

Honestly, because I didn't know it existed until you mentioned it.  I didn't know it was hard to remove/uninstall software that you compile from source. ](*,)    I looked at checkinstall in synaptic and found it online and see its used in place of the "make install" command so that you can uninstall applications you install by compiling from source.  

I now am left wondering what I am going to do to uninstall gimpshop should the need arise but I guess I will tackle that as it comes.

Thank you very much for pointing this out, as I have definitely learned something.

Respectfully

---

### Post by AgenT on 2005-06-09
[QUOTE=radhaz]Honestly, because I didn't know it existed until you mentioned it. I didn't know it was hard to remove/uninstall software that you compile from source. ](*,) I looked at checkinstall in synaptic and found it online and see its used in place of the "make install" command so that you can uninstall applications you install by compiling from source. 

I now am left wondering what I am going to do to uninstall gimpshop should the need arise but I guess I will tackle that as it comes.

Thank you very much for pointing this out, as I have definitely learned something.

Respectfully[/QUOTE]

You are more than likely safe if you still have your source dir intact. Issue ```
make uninstall
``` to uninstall what you made when using make install. In fact, why not do it *now* (assuming you still have your source folder intact) and follow it up with checkinstall? You already have the program compiled so it will only take a few seconds.

BIG HINT: make sure you do not have any program using your apt database running. This means make sure apt-get and Synaptic are closed or else you will make a small mess (deb's will not be installed because database will be lost).

But it is always wise to use checkinstall. There should be some kind of official sticky page about this program because it is, well, wonderful. Comming from a non-Debian distro I had no idea such a program existed.

---

### Post by kvidell on 2005-06-09
Blargh.
```
Selecting previously deselected package gimp-2.2.4.
(Reading database ... 91534 files and directories currently installed.)
Unpacking gimp-2.2.4 (from .../gimp-2.2.4_2.2.4-1_i386.deb) ...
dpkg: error processing /home/kvidell/src/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgimp-2.0.so.0.200.7', which is also in package libgimp2.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/kvidell/src/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb
```
Ideas? (Used the CheckInstall method)
- Kev

---

### Post by kvidell on 2005-06-09
[QUOTE=kvidell]Blargh.
```
Selecting previously deselected package gimp-2.2.4.
(Reading database ... 91534 files and directories currently installed.)
Unpacking gimp-2.2.4 (from .../gimp-2.2.4_2.2.4-1_i386.deb) ...
dpkg: error processing /home/kvidell/src/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgimp-2.0.so.0.200.7', which is also in package libgimp2.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/kvidell/src/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb
```
Ideas? (Used the CheckInstall method)
- Kev[/QUOTE]
 Nevermind. Just ahd to apt-get remove a few things and all was well :)
- Kev

---

### Post by rwabel on 2005-06-09
nice trick with checkinstall!!
thanks for that
actually why does it make a packe with 386 and not 686, because I'm running a AMD Athlon? Or is there a way to make a 686 package?

Didn't know that making a debian package is that easy :-)

---

### Post by radhaz on 2005-06-09
[QUOTE=AgenT]You are more than likely safe if you still have your source dir intact. Issue ```
make uninstall
``` to uninstall what you made when using make install. In fact, why not do it *now* (assuming you still have your source folder intact) and follow it up with checkinstall? You already have the program compiled so it will only take a few seconds..[/QUOTE]Thanks for the advice, I followed through with it and it went with only a minor hiccup.[QUOTE=kvidell]Nevermind. Just ahd to apt-get remove a few things and all was well :)[/QUOTE]What exactly did you have to remove?  I'm guessing you still had the base gimp install already installed prior to trying to install gimpshop? If you don't mind sharing I will add the data to the original post to make the install easier for other folks[QUOTE=rwabel]actually why does it make a packe with 386 and not 686, because I'm running a AMD Athlon? Or is there a way to make a 686 package?[/QUOTE]I can't say for sure but I don't think there is a 686 optimized source code, but I do know that it works just fine for me and I too am running the 686 kernel.

---

### Post by kvidell on 2005-06-09
Well.. lesse.. No, I had removed the base gimp install.. but some of the stuff you told us to install at the beginning caused conflicts.
Here's all my output:```
61/kvidell: sudo dpkg -i gimp-2.2.4_2.2.4-1_i386.deb
(Reading database ... 91534 files and directories currently installed.)
Unpacking gimp-2.2.4 (from gimp-2.2.4_2.2.4-1_i386.deb) ...
dpkg: error processing gimp-2.2.4_2.2.4-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgimp-2.0.so.0.200.7', which is also in package libgimp2.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gimp-2.2.4_2.2.4-1_i386.deb
62/kvidell: sudo apt-get remove libgimp2.0
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gimp-python libgimp2.0 xsane
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 2869kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91533 files and directories currently installed.)
Removing gimp-python ...
dpkg - warning: while removing gimp-python, directory `/usr/lib/gimp/2.0/environ' not empty so not removed.
Removing xsane ...
Removing libgimp2.0 ...
63/kvidell: sudo dpkg -i gimp-2.2.4_2.2.4-1_i386.deb
(Reading database ... 91424 files and directories currently installed.)
Unpacking gimp-2.2.4 (from gimp-2.2.4_2.2.4-1_i386.deb) ...
dpkg: error processing gimp-2.2.4_2.2.4-1_i386.deb (--install):
 trying to overwrite `/usr/share/gimp/2.0/brushes/10x10squareBlur.gbr', which is also in package gimp-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gimp-2.2.4_2.2.4-1_i386.deb
64/kvidell: sudo apt-get remove gimp-data
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gimp-data
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 18.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91423 files and directories currently installed.)
Removing gimp-data ...
65/kvidell: sudo dpkg -i gimp-2.2.4_2.2.4-1_i386.deb
(Reading database ... 90457 files and directories currently installed.)
Unpacking gimp-2.2.4 (from gimp-2.2.4_2.2.4-1_i386.deb) ...
Setting up gimp-2.2.4 (2.2.4-1) ...
66/kvidell:
```sorry if it's hard to read through.
- Kev

---

### Post by rwabel on 2005-06-09
o sorry, my bad! Should have give it a 2nd thought...it's obvious that it depends on the source if it's 386 or 686 optimized :-)

but it's working great!

---

### Post by mike998 on 2005-06-09
I got the following error when using checkinstall...
```
Selecting previously deselected package gimp-2.2.4.
(Reading database ... 76533 files and directories currently installed.)
Unpacking gimp-2.2.4 (from .../gimp-2.2.4_2.2.4-1_i386.deb) ...
dpkg: error processing /home/mike/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb (--install):
 trying to overwrite `/usr/bin/gimp-2.2', which is also in package gimp
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/mike/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb

```
I then removed gimp (which removed ubuntu-desktop - don't you love meta packages!) and then still failed to install....  No errors printed this time (at least no data)... 
Tried make uninstall, removed the gimp-2.2 directory from my home directory, tried again, and this time got this message:

```
(Reading database ... 76328 files and directories currently installed.)
Unpacking gimp-2.2.4 (from .../gimp-2.2.4_2.2.4-1_i386.deb) ...
dpkg: error processing /home/mike/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgimp-2.0.so.0.200.7', which is also in package libgimp2.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/mike/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb
``` 

Now, I'm at a loss...

---

### Post by kvidell on 2005-06-09
[QUOTE=mike998]I got the following error when using checkinstall...
```
Selecting previously deselected package gimp-2.2.4.
(Reading database ... 76533 files and directories currently installed.)
Unpacking gimp-2.2.4 (from .../gimp-2.2.4_2.2.4-1_i386.deb) ...
dpkg: error processing /home/mike/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb (--install):
 trying to overwrite `/usr/bin/gimp-2.2', which is also in package gimp
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/mike/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb

```
I then removed gimp (which removed ubuntu-desktop - don't you love meta packages!) and then still failed to install....  No errors printed this time (at least no data)... 
Tried make uninstall, removed the gimp-2.2 directory from my home directory, tried again, and this time got this message:

```
(Reading database ... 76328 files and directories currently installed.)
Unpacking gimp-2.2.4 (from .../gimp-2.2.4_2.2.4-1_i386.deb) ...
dpkg: error processing /home/mike/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgimp-2.0.so.0.200.7', which is also in package libgimp2.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/mike/gimp-2.2.4/gimp-2.2.4_2.2.4-1_i386.deb
``` 

Now, I'm at a loss...[/QUOTE]
 Read my reply? :)

Just apt-get remove anything that gives you trouble and you'll be fine.

sudo apt-get remove libgimp2.0 gimp-data
is what I had to do. then just dpkg -i the gimpshop package again.
- Kev

---

### Post by mike998 on 2005-06-09
Worked, thanks...

---

### Post by kvidell on 2005-06-09
[QUOTE=mike998]Worked, thanks...[/QUOTE]
 Glad it worked :)
Cheers,
- K

---

### Post by radhaz on 2005-06-09
[QUOTE=kvidell]
sudo apt-get remove libgimp2.0 gimp-data
is what I had to do. then just dpkg -i the gimpshop package again.
- Kev[/QUOTE]

DOH! I must have already removed that package at some point before using checkinstall.  Thanks for sharing the info, Ive updated the OP accordingly.

---

### Post by zAo on 2005-06-30
Thanks. 
Everything went fine. Now, when I run gimp, I get the Gimpshop-splash but I get into Gimp!

What did I do wrong? Thanks :)

NM: My bad: I expected something else. The picturewindow is just like PS, thanks!

---

