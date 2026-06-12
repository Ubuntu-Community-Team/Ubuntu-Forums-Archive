---
title: "Howto install vdr with Xine plugin"
date: 2005-08-17
forum: General Help
---

### Post by art2003 on 2005-08-17
HOW TO INSTALL VDR WITH A BUDGET (low-end) SATELLITE CARD DVB-S.

This may help as well those with a budget cable (DVB-C) or terrestrial (DVB-T) card
but it is mainly aimed at those using a satellite card (DVB-S)

First using Synaptic make sure you have at least

        automake-1.8.3
        autoconf-2.59
        libtool-1.5.2
        kernel-headers

or newer installed.

Also make sure your budget card is already detected by Ubuntu otherwise you need
to get the right drivers configured which is beyond the scope of this document.
(I have written a little howto for the Twinhan PCI DVB-S cards)

1st) Get and build VDR 1.3.29
Open a terminal
cd /usr/local/src

You can download it from this site (or any other)
sudo wget [http://www.venson.e7even.com/.themes/vdr-1.3.29.tar.bz2](http://www.venson.e7even.com/.themes/vdr-1.3.29.tar.bz2)

Then unpack it with:
sudo tar xjvf vdr-1.3.29.tar.bz2
create a symbolic link with:
sudo ln -s vdr-1.3.29 VDR
cd VDR/PLUGINS/src

Download vdr-xine with:
sudo wget vdr-xine-0.7.5.tgz
unpack it with:
sudo tar xzvf vdr-xine-0.7.5.tgz
create a symbolic link with:
sudo ln -s vdr-xine-0.7.5.tgz xine
cd /usr/local/src/

Now we need a version of xine-lib that has been patched for VDR.
sudo wget [http://www.venson.e7even.com/.themes/libxine-dev_1.0.1-2_i386.deb](http://www.venson.e7even.com/.themes/libxine-dev_1.0.1-2_i386.deb)

and

sudo wget [http://www.venson.e7even.com/.themes/libxine1_1.0.1-2_i386.deb](http://www.venson.e7even.com/.themes/libxine1_1.0.1-2_i386.deb)

Install them with:
sudo dpkg -i libxine1_1.0.1-2_i386.deb
and
sudo dpkg -i libxine-dev_1.0.1-2_i386.deb
 
You need a rather new version of xine
you can get one from:
sudo wget [http://www.venson.e7even.com/.themes/xine-ui_0.99.3-1_i386.deb](http://www.venson.e7even.com/.themes/xine-ui_0.99.3-1_i386.deb)
Install as usual with dpkg -i xine-ui_0.99.3-1_i386.deb

Now we are almost ready to compile VDR and plugins.
We need to create a symbolic link called DVB to
our linux-headers. In my case this is done with
sudo ln -s /usr/src/linux-headers-2.6.10-5-k7/ DVB


cd VDR
sudo gedit Makefile
edit any options if you need and ... ready to compile!


sudo make
sudo make plugins
sudo make install
cd /video

If you left the default options you should have some .conf files under /video
If you have a diseq 4in1 switch you need to edit diseq.conf
you can get my channels.conf and diseqc.conf from here:

sudo wget [http://www.venson.e7even.com/.themes/diseqc.conf](http://www.venson.e7even.com/.themes/diseqc.conf)
sudo wget [http://www.venson.e7even.com/.themes/channels.conf](http://www.venson.e7even.com/.themes/channels.conf)

and my setup.conf 
sudo wget [http://www.venson.e7even.com/.themes/setup.conf](http://www.venson.e7even.com/.themes/setup.conf)

These files are setup for Astra2 on position A and Astra1 on position D.

North American users will need different settings in channels.conf, diseqc.conf and setup.conf
I suggest checking a howto on [http://www.hoochvdr.info/](http://www.hoochvdr.info/)  for that matter.


You can either define your own keys or get mine from:
sudo wget [http://www.venson.e7even.com/.themes/remote.conf](http://www.venson.e7even.com/.themes/remote.conf)

(C for channels list, O for options, Enter for OK, arrows to move around)


Permissions are important so we need to do:
sudo chown vdr /video/* -Rf

Some final but necessary steps:
sudo mkdir /video/plugins/xine/
sudo cp /usr/local/src/VDR/PLUGINS/src/xine/data/* /video/plugins/xine/

Finally lets create a simple script to start vdr in a terminal

sudo gedit /usr/bin/vdrstart

enter this:
#--------------------------
cd /usr/local/src/VDR/
export LANG="en_GB.iso8859-1"
vdr --plugin=xine
#--------------------------

That should be it!
We haven't compiled a remote control plugin (as I don't have one) so we have to use the keyboard
and the terminal window needs to be on focus when entering keys.
if you need more plugins follow the procedure for xine and make sure to read each plugins
README and INSTALL instructions.

now run vdrstart
and xine
On xine press 'g' to show the controls and then click on the VDR button (if you haven't got one
either you have an old version of xine or you didn't install the patched xine-lib)

Return the window focus to the terminal where we are running vdrstart and press 'C' if all went well you should see a list of channels.

Enjoy!

Notes:
If you get xine-lib and xine-ui in tar balls then you can patch them prior to compiling with this:

  patch -d. -p0 < /soft/src/VDR/PLUGINS/src/xine/patches/xine-lib.patch
  patch -d. -p0 < /soft/src/VDR/PLUGINS/src/xine/patches/xine-ui.patch

where /soft/src/VDR is the path to your VDR sources directory.

---

### Post by c-m on 2005-08-31
the following link returns 404 not found sudo wget [http://www.venson.e7even.com/.theme....0.1-2_i386.deb](http://www.venson.e7even.com/.theme....0.1-2_i386.deb)

also with the symbolic links 
> 
Then unpack it with:
sudo tar xjvf vdr-1.3.29.tar.bz2
create a symbolic link with:
sudo ln -s vdr-1.3.29.tar.bz2 VDR
cd VDR/PLUGINS/src


should it be **sudo ln -s vdr-1.3.29 VDR** and not sudo ln -s vdr-1.3.29.tar.bz2 VDR?

EDIT: managed to manually get those versions of libxine1 etc.. but they will not compile since they have a load of dependancies that are not in synaptic or are the versions that are, are too old.

---

### Post by art2003 on 2005-09-01
Hello,
You were right about the symbolic link, an ovesight on my side. I have corrected it now.
The link to the .deb packages works, just make sure you click on it and not do 'copy' and paste (as this way you get some .... in the middle of the name

Use the .deb packages I provide as they are already patched to work with VDR.

---

### Post by c-m on 2005-09-01
[QUOTE=art2003]Hello,
You were right about the symbolic link, an ovesight on my side. I have corrected it now.
The link to the .deb packages works, just make sure you click on it and not do 'copy' and paste (as this way you get some .... in the middle of the name

Use the .deb packages I provide as they are already patched to work with VDR.[/QUOTE]
 the problem is the .deb packages you provide will not work. here is the output. 

> 
sudo dpkg -i libxine1_1.0.1-2_i386.deb
Selecting previously deselected package libxine1.
(Reading database ... 98479 files and directories currently installed.)
Unpacking libxine1 (from libxine1_1.0.1-2_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing libxine1_1.0.1-2_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/xine/libxine1/fonts/mono-32.xinefont.gz')
Errors were encountered while processing:
 libxine1_1.0.1-2_i386.deb


Done a search but i can't find where to get another copy patched for vdr.

btw libxine_dev depends on libxine1 so you might want to change the install order in the guide and place "sudo" in front of dpkg -i......  just so its easier for noobs to follow.

---

### Post by c-m on 2005-09-01
As the package from [http://www.venson.e7even.com/.themes/libxine-dev_1.0.1-2_i386.deb](http://www.venson.e7even.com/.themes/libxine-dev_1.0.1-2_i386.deb) will not install, I have downloaded the latest xine-lib from the xine website.

How do i patch this for VDR the vdr-plugin instructions are not clear and basically list the same commands as you've posted here:
> 
patch -d. -p0 < /soft/src/VDR/PLUGINS/src/xine/patches/xine-lib.patch
patch -d. -p0 < /soft/src/VDR/PLUGINS/src/xine/patches/xine-ui.patch


where do i go to type this? do i extract the xine-lib first (which is what i've done) then i entred the xine directory and typed patch -d. -p0 < /soft/src/VDR/PLUGINS/src/xine/patches/xine-lib.patch but it returns that the file or directory are not found. where is this directory /sof/src/VDR.........?

---

### Post by art2003 on 2005-09-02
Ok a bit more of instructions on the matter.
I unpacked the VDR source on 
/usr/local/src/VDR
I downloaded vdr-xine plugin version 0.7.5
and extracted it to
/usr/local/src/VDR/PLUGINS/src/xine-0.7.5
then I create a symbolic link 
cd /usr/local/src/VDR/PUGINS/src/
sudo ln -s xine-0.7.5 xine
now change to the directory where you have your xine-lib source
and type
sudo patch -d. -p0 < /usr/local/src/VDR/PLUGINS/src/xine/patches/xine-lib.patch
then change to the directory where you have your xine-ui and type
sudo patch -d. -p0 < /usr/local/src/VDR/PLUGINS/src/xine/patches/xine-ui.patch

---

### Post by art2003 on 2005-09-02
Something else that may be helpful.
I am using gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)

And currently using xine-lib-1.1.0 patched with the previously mentioned patches.

---

### Post by c-m on 2005-09-02
the patch assumes xine-lib is in the directory /cvsroot/xine/xine-lib so i moved it there, but even then the patch seems unable to find the files, so i manually entre the path to them as shown below, but although its says it has succeeded there is still an error about not being able to find something or other;

> 
carl@carl:/cvsroot/xine/xine-lib$ sudo patch -d. -p0 < /usr/local/src/VDR/PLUGINS/src/xine/patches/xine-lib.patch
can't find file to patch at input line 8
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: xine-lib/configure.ac
|===================================================================
|RCS file: /cvsroot/xine/xine-lib/configure.ac,v
|retrieving revision 1.331
|diff -u -r1.331 configure.ac
|--- xine-lib/configure.ac      5 Aug 2005 19:44:34 -0000       1.331
|+++ xine-lib/configure.ac      14 Aug 2005 16:06:47 -0000
--------------------------
File to patch: /cvsroot/xine/xine-lib/configure.ac
patching file /cvsroot/xine/xine-lib/configure.ac
Hunk #1 succeeded at 2391 (offset -113 lines).
Hunk #2 succeeded at 2450 (offset -113 lines).
Hunk #3 succeeded at 2606 (offset -115 lines).
can't find file to patch at input line 40
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
Index: xine-lib/include/xine.h.in
|===================================================================
|RCS file: /cvsroot/xine/xine-lib/include/xine.h.in,v
|retrieving revision 1.144
|diff -u -r1.144 xine.h.in
|--- xine-lib/include/xine.h.in 17 Jul 2005 23:11:33 -0000      1.144
|+++ xine-lib/include/xine.h.in 14 Aug 2005 16:06:54 -0000
--------------------------
File to patch:  /cvsroot/xine/xine-lib/include/xine.h.in
patching file /cvsroot/xine/xine-lib/include/xine.h.in
can't find file to patch at input line 57
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:


I have to manually entre the path to each file, surely something is wrong their. Funny the same doesn't happen for xine-ui that just applies the patch straight away.

I have tried with both the latest version of xine-lib and the CVS version as another thread mentioned this was needed.

All i need to do is get this sorted so i can enjoy satellite TV from my skystar2 card.

---

### Post by art2003 on 2005-09-03
I unpacked xine-ui and xine-lib to /usr/local/src/xine-lib and /usr/local/src/xine-ui respectively. applied the patches and compiled them with make rules/debian binary
 I do not remember having seen skipped files but the patching was reported successfull. Have you tried to compile xine-ui anyway?

---

### Post by art2003 on 2005-09-03
Step by step instruccions on patching xine-lib
cd /usr/local/src
download xine-lib-1.1.0.tar.gz here
sudo tar xzvf xine-lib-1.1.0.tar.gz
sudo ln -s xine-lib-1.1.0.tar.gz xine-lib

the do cd /usr/local/src
to make sure you are in the right directory
 patch -d. -p0 < /usr/local/src/vdr-1.3.30/PLUGINS/src/xine/patches/xine-lib.patch
There should be no skipped files whatsoever.

I have followed today these steps from scratch and this was the output:
 patch -d. -p0 < /usr/local/src/vdr-1.3.30/PLUGINS/src/xine/patches/xine-lib.patch
patching file xine-lib/configure.ac
Hunk #1 succeeded at 2391 (offset -113 lines).
Hunk #2 succeeded at 2450 (offset -113 lines).
Hunk #3 succeeded at 2606 (offset -115 lines).
patching file xine-lib/include/xine.h.in
patching file xine-lib/src/Makefile.am
patching file xine-lib/src/demuxers/demux_mpeg_pes.c
patching file xine-lib/src/libmpeg2/decode.c
patching file xine-lib/src/post/planar/expand.c
patching file xine-lib/src/xine-engine/video_out.c
patching file xine-lib/src/xine-engine/video_overlay.h
patching file xine-lib/src/xine-engine/xine.c
patching file xine-lib/src/xine-engine/xine_internal.h
patching file xine-lib/src/vdr/Makefile.am
patching file xine-lib/src/vdr/input_vdr.c
patching file xine-lib/src/vdr/input_vdr.h
patching file xine-lib/src/vdr/post_vdr.c
patching file xine-lib/src/vdr/post_vdr.h
patching file xine-lib/src/vdr/post_vdr_audio.c
patching file xine-lib/src/vdr/post_vdr_video.c

Then do cd xine-lib
sudo ./configure
and
sudo make debian/rules binary
or
make
make install
If you are still stuck tell me where to upload a 7.8 megabytes file and I can upload the correctly patched sources for xine-lib-1.1.0 as shown above.

---

### Post by bneuro1 on 2005-11-26
Hi!
Your post install vdr xine seems be not update. Vdr has a new version, but you mean that it does't be patch?

Again i wold be interested to know were i can obtain information about a version of xine-lib that has been patched for VDR

---

### Post by hjt4vdr on 2006-04-25
Hi,

i am peter_weber69 or hjt4vdr. The developer of xine-network

now you can use my new ubuntu vdr debs
[http://mitglied.lycos.de/peterweber69/ubuntu/](http://mitglied.lycos.de/peterweber69/ubuntu/)

[http://www.ubuntu-forum.de/artikel/9974/ANNOUNCE-ct-vdr-packages-fuer-dapper-samt-xine-plu.html](http://www.ubuntu-forum.de/artikel/9974/ANNOUNCE-ct-vdr-packages-fuer-dapper-samt-xine-plu.html)

---

### Post by mtron on 2006-04-25
hi peter! Thanks for the debs, but they won't work under hoary and breezy. i think they are for dapper only, right?

---

### Post by hjt4vdr on 2006-04-25
Hi,
yes that's right, only for dapper :( 
so in June, or was it July is dapper stable, is that right?
use it then :-D 

bye
Horst ( peter is fake :rolleyes: )

---

### Post by mtron on 2006-04-25
nice one, thanks! 

maybe also someday with sc ;) ?

---

### Post by hjt4vdr on 2006-04-25
maybe :mrgreen:

---

### Post by mtron on 2006-05-12
Hi horst! 

updated now to dapper and added your repository. but when i try to install your vdr debs i get: 

vdr:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu17 is to be installed
  Depends: libgcc1 (>=1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libstdc++6 (>=4.1.0) but 4.0.3-1ubuntu5 is to be installed

did you install this packages from sid manually, or how did ya resolve it?

---

### Post by hjt4vdr on 2006-08-03
hi,

now i use xineliboutput instead of xine-net plugin because you must not patch libxine1. it works with original xine-main1 and libxine1c2 from dapper.

Horst

---

### Post by hjt4vdr on 2006-08-07
hi,

had found a howto for xineliboutput
[http://www.linuxtv.org/vdrwiki/index.php/DEBIAN_Compiling_VDR_Source_Packages](http://www.linuxtv.org/vdrwiki/index.php/DEBIAN_Compiling_VDR_Source_Packages)

bye

---

### Post by neztiti on 2007-07-08
thanx man

---

