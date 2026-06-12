---
title: "How to compile mplayer with vesa support?"
date: 2006-10-17
forum: General Help
---

### Post by randomshinichi on 2006-10-17
It says it needs vbe.h so I installed xserver-xorg-dev and I ran ./configure --with-extraincdir=/usr/include/xorg so that it could pick up vbe.h. However, it seems there are more problems. 
```
============ Checking for VESA support ============

#include <vbe.h>
int main(void) { vbeVersion(); return 0; }

cc -O4 -march=c3 -mtune=c3 -pipe -ffast-math -fomit-frame-pointer -I/usr/include/xorg   -o /tmp/mplayer-conf-18707-325.o /tmp/mplayer-conf-17684-325.c -lvbe -llrmi
In file included from /usr/include/xorg/vbe.h:15,
                 from /tmp/mplayer-conf-17684-325.c:1:
/usr/include/xorg/xf86int10.h:65: error: syntax error before 'BusType'
/usr/include/xorg/xf86int10.h:65: warning: no semicolon at end of struct or union
/usr/include/xorg/xf86int10.h:74: error: syntax error before '}' token
/usr/include/xorg/xf86int10.h:74: warning: data definition has no type or storage class

ldd /tmp/mplayer-conf-18707-325.o
ldd: /tmp/mplayer-conf-18707-325.o: No such file or directory

Result is: no 
```

Any way I can fix this? I looked into the files, and.... well, I didn't see anything wrong, granted, my C isn't that great to begin with. VESA always compiled when I was on Gentoo :( awesome OS.

---

### Post by kuja on 2006-10-17
Why do you need VESA support exactly anyway? Do other things (eg: xv,x11,gl) not work well for you?

---

### Post by randomshinichi on 2006-10-18
Somebody please just help me... libdha.so complains about not finding savage_vid.so even though it's clearly there (run ldconfig?) when I try to run xvidix - even aa/caca is slow, svga doesn't work. This is only the first of a few I need to work on. You might not believe this, but xv isn't exactly running smoothly either. A VIA C3 is a weak processor. Paired with a restricted graphics chip (ProSavage) that only accepts YV12, I need to get the most out of this.

---

### Post by keith.burgoyne on 2007-11-22
Too bad this problem never reached a solution that was posted on the forum! I've found myself in need of compiling mplayer with vesa support. 

I have a thinkpad 390x, which has a neomagic 256av video card in it. I need the s-video output to play videos, and apparently (according to the mplayer documentation), I can only make it work by running it with vesa as the video output. Sadly, the mplayer binary that's available in the Ubuntu Gutsy repo does not support vesa!

The documentation I found is available here:
[http://www.pcbypaul.com/absolute/programs/mplayer/#tvout-neomagic](http://www.pcbypaul.com/absolute/programs/mplayer/#tvout-neomagic)

---

### Post by dspdude on 2007-12-19
vbe.h can be grabbed from MPlayer's subversion server: 

$ svn checkout svn://svn.mplayerhq.hu/vesautils/trunk vesautils

This will place VESA-related files in the directory "vesautils"

sym-link, or copy,  vbe.h from "vesautils/libvbe/vbe.h" to the "MPlayer-1.0rc/libvo" directory

You'll need to compile the libvbe library.

Hope that helps.

---

