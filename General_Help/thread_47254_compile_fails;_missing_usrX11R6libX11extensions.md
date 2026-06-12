---
title: "compile fails; missing /usr/X11R6/lib/X11/extensions"
date: 2005-07-07
forum: General Help
---

### Post by stanwebber on 2005-07-07
i am trying to compile avview 0.80.6 ([http://gatos.sourceforge.net/avview.php](http://gatos.sourceforge.net/avview.php)) under hoary 5.04.  after installing the libzvbi, tcl, tk dev packages i meet all the requirements for configure to finish successfully & generate a makefile; however, make immediately fails with /usr/X11R6/lib/X11/extensions/Xvlib.h:  No such file or directory

what is this file & why is it missing?  my best guess is it's some sort of header file related to xvideo.  god please dont tell me i have to compile my xserver from source to get it

---

### Post by abhaysahai on 2005-07-08
On my system
#sudo  apt-cache search libxv

libxv-dev - X Window System video extension library development files
libxv1 - X Window System video extension library
libxv1-dbg - X Window System video extension library (unstripped)
libxvmc-dev - X Window System video motion compensation extension library development files
libxvmc1 - X Window System video motion compensation extension library
libxvmc1-dbg - X Window System video motion compensation extension library (unstripped)
xlibs-dev - X Window System client library development files transitional package
avifile-xvid-plugin - XviD video encoding plugin for libavifile
libxvidcore4 - High quality ISO MPEG4 codec library
libxvidcore4-dev - High quality ISO MPEG4 codec library -- development files

I understand that your problem will be resolved by installing 
"libxv-dev - X Window System video extension library development files" 

sudo apt-get install libxv-dev

Regards,
Abhay

---

### Post by stanwebber on 2005-07-08
hot damn, that was it!  thanks a million, i was only searching for xvlib, xvideo etc...

---

