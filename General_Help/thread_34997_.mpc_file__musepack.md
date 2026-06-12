---
title: ".mpc file / musepack"
date: 2005-05-17
forum: General Help
---

### Post by ubuntu_demon on 2005-05-17
hi,

I want to be able to play flac / mpc files.

this is my xmms version :
1.2.10-2ubuntu

this is my beep-media-player version :
0.9.7-1ubuntu1 

I've installed these files from musepack.net :

XMMS-Musepack 1.2 RC1
BMP-Musepack 1.2 RC1
libmpcdec 1.2

when I try to run xmss from terminal I get :

libmpcdec.so.3: cannot open shared object file: No such file or directory

I can locate libmpcdec.so.3 and it is where it should be (I think) :

/usr/local/lib/libmpcdec.so.3

also both in xmms and in bmp the input plugins don't show up. 

The reason I want to be able to play flac/mpc files is that I want to play a cd I downloaded directly .. or rip the mpc / flac files out of it.

I've got these files :

CDImage.cue  CDImage.mpc  CDImage.mpc.cue

---

### Post by kassetra on 2005-05-20
[QUOTE=demon666_nl]hi,

I want to be able to play flac / mpc files.

this is my xmms version :
1.2.10-2ubuntu

this is my beep-media-player version :
0.9.7-1ubuntu1 

I've installed these files from musepack.net :

XMMS-Musepack 1.2 RC1
BMP-Musepack 1.2 RC1
libmpcdec 1.2[/QUOTE]Ok, in order to play flac files as well - you'll need the flac plugins (one each for bmp and xmms) as well as the flac libraries.

[QUOTE=demon666_nl] when I try to run xmss from terminal I get :

libmpcdec.so.3: cannot open shared object file: No such file or directory

I can locate libmpcdec.so.3 and it is where it should be (I think) :

/usr/local/lib/libmpcdec.so.3[/QUOTE]Check your PATH variables to see where it's looking - you might need to add a symlink to /usr/local/lib ... because if you can find it - and it can't, it sounds like a PATH issue.

[QUOTE=demon666_nl] also both in xmms and in bmp the input plugins don't show up. [/QUOTE]It might be helpful for me to see the output of this command:
 ```
 ldd /usr/lib/xmms/Input/libmpc.so 
``` 

[QUOTE=demon666_nl]
or rip the mpc / flac files out of it.
[/QUOTE] you'll need the mppenc encoder to be able to rip to mpc format.

---

### Post by ubuntu_demon on 2005-05-21
[QUOTE=kassetra]Ok, in order to play flac files as well - you'll need the flac plugins (one each for bmp and xmms) as well as the flac libraries.

Check your PATH variables to see where it's looking - you might need to add a symlink to /usr/local/lib ... because if you can find it - and it can't, it sounds like a PATH issue.

It might be helpful for me to see the output of this command:
 ```
 ldd /usr/lib/xmms/Input/libmpc.so 
``` 

 you'll need the mppenc encoder to be able to rip to mpc format.[/QUOTE]
 okay cool thnx

So if understand it correct .... the .mpc file is some sort of disk image that can be played directly ?

I'll look into it when I get home!

---

### Post by ubuntu_demon on 2005-05-22
I've put /usr/local/lib in my path ... xmms still gives the same error message.

```

 ldd /usr/lib/xmms/Input/libmpc.so 

        libmpcdec.so.3 => not found
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x4cd5e000)
        libgmodule-1.2.so.0 => /usr/lib/libgmodule-1.2.so.0 (0x41068000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x4cc28000)
        libxmms.so.1 => /usr/lib/libxmms.so.1 (0x41015000)
        libgtk-1.2.so.0 => /usr/lib/libgtk-1.2.so.0 (0x410c1000)
        libgdk-1.2.so.0 => /usr/lib/libgdk-1.2.so.0 (0x41030000)
        libXi.so.6 => /usr/X11R6/lib/libXi.so.6 (0x4100b000)
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0x41874000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0x417ad000)
        libglib-1.2.so.0 => /usr/lib/libglib-1.2.so.0 (0x4109c000)
        libtag.so.1 => /usr/lib/libtag.so.1 (0xb7f9b000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0x41b2b000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x4cc2d000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x4caf9000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x41b1e000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x80000000)
        libgthread-1.2.so.0 => /usr/lib/libgthread-1.2.so.0 (0x41006000)

```

---

### Post by ubuntu_demon on 2005-06-01
*bump*

---

### Post by RaymondQE on 2005-06-01
I wonder if it will work if you add a symlink to the file from /usr/lib

```
 sudo ln -s /usr/local/lib/libmpcdec.so.3 /usr/lib/libmpcdec.so.3
```

---

### Post by ubuntu_demon on 2005-06-02
[QUOTE=RaymondQE]I wonder if it will work if you add a symlink to the file from /usr/lib

```
 sudo ln -s /usr/local/lib/libmpcdec.so.3 /usr/lib/libmpcdec.so.3
```[/QUOTE]
 thnx!
seems to work (stupid that I didn't think of that) xmms doesn't give an error when starting up anymore.

When I try to load the mpc in xmms I get a segmentation fault. I doesn't load in beep-media-player either. 

I'm gonna google for an mpc file (those .flac files from [http://www.musepack.net/samples/](http://www.musepack.net/samples/) worked already)

I think I''m gonna try burning the file as a cd-image. Since these are the filenames :

CDImage.cue CDImage.mpc CDImage.mpc.cue

---

### Post by RaymondQE on 2005-06-02
Checkout the musepack thread.

[http://www.musepack.net/forum/viewtopic.php?t=202](http://www.musepack.net/forum/viewtopic.php?t=202)

It appears to be a problem with libtag.

---

### Post by ubuntu_demon on 2005-06-02
[QUOTE=RaymondQE]Checkout the musepack thread.

[http://www.musepack.net/forum/viewtopic.php?t=202](http://www.musepack.net/forum/viewtopic.php?t=202)

It appears to be a problem with libtag.[/QUOTE]
 I've got these installed :

```

ii  libtag1        1.3.1-1        TagLib Audio Meta-Data Library
ii  libtag1-dev    1.3.1-1        TagLib Audio Meta-Data Library [development]
ii  libtagc0       1.3.1-1        TagLib Audio Meta-Data Library (C bindings)

```

these are installable :

```

libtag1 - TagLib Audio Meta-Data Library
libtag1-dev - TagLib Audio Meta-Data Library [development]
libtag1-doc - TagLib Audio Meta-Data Library [documentation]
libtagc0 - TagLib Audio Meta-Data Library (C bindings)
libtagc0-dev - TagLib Audio Meta-Data Library (C bindings) [development]
libtagcoll-dev - Functions used to manipulate tagged collections (development version)
libtagcoll0 - Functions used to manipulate tagged collections

```

---

### Post by RaymondQE on 2005-06-02
I compiled the libtag from subversion and it appears to work for me.  These are the steps I followed.

1. Made sure that I had autoconf>2.53, subversion, and automake>1.6.1 installed, all of which are available on the repository.

2. ran the command
```
svn co svn://anonsvn.kde.org/home/kde/trunk/kdesupport
```

3. entered kdesupport subdirectory after subversion completed the download

4. Then ran the next two commands
```
make -f Makefile.cvs
./configure --prefix=/usr
```

5. entered the taglib directory

6. ran
```
sudo make install
```

note -> if you have checkinstalled installed, you can run 'sudo checkinstall' and it will create a deb for you.

7. compiled the xmms-musepack plugin

Now mpc works for me.  Hope this helps.

---

### Post by ubuntu_demon on 2005-06-02
thnx I'll try soon :)

---

### Post by oofnik on 2005-06-27
Thanks RaymondQE! After building libmpcdec several thousand times, I did:
```
sudo ln -s /usr/local/lib/libmpcdec.so.3 /usr/lib/libmpcdec.so.3
```, and then followed your steps, and now xmms plays my mpc files. And it doesn't suck up resources. Thanks guys! :smile:

---

### Post by nrayever on 2005-06-28
oofnik and RaymondQE thanks a lot for this mini howto for musepack!!
really easy and fast!! really help full. work execelent.  :razz:  :razz:

---

### Post by vassie on 2005-06-29
xmms-musepack has been added to backports :)

[http://ubuntuforums.org/showthread.php?t=44252&highlight=xmms-musepack](http://ubuntuforums.org/showthread.php?t=44252&highlight=xmms-musepack)

Ben

---

