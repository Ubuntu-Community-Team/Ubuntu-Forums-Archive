---
title: "Luvcview for webcam"
date: 2008-01-25
forum: General Help
---

### Post by heather on 2008-01-25
Hi

i am trying to install Luvcview
i get an error saying dependency Problem Prevent Configuration of Luvcview
Luvciew depends on lib6 (>=2.6.1-1); however:
version of lib6 on system is 2.5-ubuntu14.
dpkg:error processing Luvciew (--install):

any ideas?

i am trying to use this so i can use tilt and pan controls on an Logitech Orbit camera

i already have pwcview but need Luvciew

Thank You

---

### Post by geirha on 2008-01-25
Are you trying to install the luvcview package from the hardy repository? You'll need at least gutsy to be able to install that package. Don't think there's any package for older ubuntu-releases. Your best bet is to compile it yourself. There are some instructions here: [https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy](https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy). You should go get the latest source-code though, and not the sourcecode from 2006 used in that page.

---

### Post by heather on 2008-01-25
HI

Actually yes from package also tried a tarball file as well and i got that same problem

Thanks

---

### Post by heather on 2008-01-25
Hi

after going to the link you sent
Everythign above Luvcview installed

Luvcview still wont install


heather:~/trunk/luvcview-20060920$ sudo make
gcc -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DUSE_SDL -O2 -DLINUX -DVERSION=\"0.1.7\" -I/usr/src/modules/linux-uvc -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -c -o frmfmtenum.o frmfmtenum.c
In file included from frmfmtenum.c:36:
v4l2_enumfrmfmt.h:8: error: nested redefinition of ‘enum v4l2_frmsizetypes’
v4l2_enumfrmfmt.h:8: error: redeclaration of ‘enum v4l2_frmsizetypes’
v4l2_enumfrmfmt.h:9: error: redeclaration of enumerator ‘V4L2_FRMSIZE_TYPE_DISCRETE’
/usr/include/linux/videodev2.h:282: error: previous definition of ‘V4L2_FRMSIZE_TYPE_DISCRETE’ was here
v4l2_enumfrmfmt.h:10: error: redeclaration of enumerator ‘V4L2_FRMSIZE_TYPE_CONTINUOUS’
/usr/include/linux/videodev2.h:283: error: previous definition of ‘V4L2_FRMSIZE_TYPE_CONTINUOUS’ was here
v4l2_enumfrmfmt.h:11: error: redeclaration of enumerator ‘V4L2_FRMSIZE_TYPE_STEPWISE’
/usr/include/linux/videodev2.h:284: error: previous definition of ‘V4L2_FRMSIZE_TYPE_STEPWISE’ was here
v4l2_enumfrmfmt.h:14: error: nested redefinition of ‘enum v4l2_frmivaltypes’
v4l2_enumfrmfmt.h:14: error: redeclaration of ‘enum v4l2_frmivaltypes’
v4l2_enumfrmfmt.h:15: error: redeclaration of enumerator ‘V4L2_FRMIVAL_TYPE_DISCRETE’
/usr/include/linux/videodev2.h:322: error: previous definition of ‘V4L2_FRMIVAL_TYPE_DISCRETE’ was here
v4l2_enumfrmfmt.h:16: error: redeclaration of enumerator ‘V4L2_FRMIVAL_TYPE_CONTINUOUS’
/usr/include/linux/videodev2.h:323: error: previous definition of ‘V4L2_FRMIVAL_TYPE_CONTINUOUS’ was here
v4l2_enumfrmfmt.h:17: error: redeclaration of enumerator ‘V4L2_FRMIVAL_TYPE_STEPWISE’
/usr/include/linux/videodev2.h:324: error: previous definition of ‘V4L2_FRMIVAL_TYPE_STEPWISE’ was here
v4l2_enumfrmfmt.h:24: error: redefinition of ‘struct v4l2_frmsize_discrete’
v4l2_enumfrmfmt.h:32: error: redefinition of ‘struct v4l2_frmsize_stepwise’
v4l2_enumfrmfmt.h:52: error: redefinition of ‘struct v4l2_frmsizeenum’
v4l2_enumfrmfmt.h:73: error: redefinition of ‘struct v4l2_frmival_stepwise’
v4l2_enumfrmfmt.h:84: error: redefinition of ‘struct v4l2_frmivalenum’
In file included from frmfmtenum.c:36:
v4l2_enumfrmfmt.h:116:1: warning: "VIDIOC_ENUM_FRAMESIZES" redefined
In file included from /usr/include/linux/videodev.h:15,
                 from frmfmtenum.c:34:
/usr/include/linux/videodev2.h:1243:1: warning: this is the location of the previous definition
In file included from frmfmtenum.c:36:
v4l2_enumfrmfmt.h:117:1: warning: "VIDIOC_ENUM_FRAMEINTERVALS" redefined
In file included from /usr/include/linux/videodev.h:15,
                 from frmfmtenum.c:34:
/usr/include/linux/videodev2.h:1244:1: warning: this is the location of the previous definition
make: *** [frmfmtenum.o] Error 1
electricity@liq:~/trunk/luvcview-20060920$

---

### Post by randyrick on 2008-02-08
> **heather said:**
> Hi

i am trying to install Luvcview
i get an error saying dependency Problem Prevent Configuration of Luvcview
Luvciew depends on lib6 (>=2.6.1-1); however:
version of lib6 on system is 2.5-ubuntu14.
dpkg:error processing Luvciew (--install):



How are you doing the above?  Have you tried `sudo aptitude install $package`?

**sorry, I thought this was a package from one of the repositories...

---

### Post by geirha on 2008-02-08
Sorry, I forgot to answer this thread. Try with the latest version of luvcview instead of the one from 2006. The steps should be 
```

wget http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz
tar zxf luvcview-20070512.tar.gz
cd luvcview-20070512/
make

```
Note that this should not be done as root, that's bad practice. So don't use sudo for any of those commands.

If make succeeds, you can test luvcview by typing "./luvcview". If it works, install it (this is the only step you need to use sudo with)
```
sudo make install
```
Now you should be able to run it by typing "luvcview" in a terminal.

---

