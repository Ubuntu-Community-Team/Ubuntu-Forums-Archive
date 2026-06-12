---
title: "xrandr scaling and mouse constraint"
date: 2015-01-06
forum: General Help
---

### Post by JDAIII on 2015-01-06
I'm working on getting my resolution dialed in. I have a 4k monitor and a 1080. On the 1080, I scale 2x2 with the command below but it constrains the mouse to the top left quadrant of the screen. I saw a bug report and fix on this however it looks like it requires a recompile of xorg and I haven't been using linux long enough to try something like that. I'm wondering if anyone has any other issues. Someone recommended adding panning with the command such as --panning 3840x2160, but I tried that and to say that it failed would be an understatement.

I'm open to anything if anyone has any ideas.

xrandr --output eDP1 --auto --output HDML1 --auto --scale 2x2 --right-of eDP1

---

### Post by JDAIII on 2015-05-21
bump

So I have done a few things. First, I upgraded to 15.04. the reason for this is because I had hoped this would no longer be an issue.

It is.

So I did find a patch for this. But to my understanding, it requires that I patch and compile xorg from source. Now I would prefer not to blow up my OS and have to reinstall, but if worst comes to worst, I do have a backup of my home folder.

My question is, with the patch at this link, how would I go about doing this? 

I have two other things that I want to verify. I'm using ubuntu gnome which I'm not sure matters, but never hurts to add that. and 2, I have verified that X upgraded successfully to 1.17.1.

[https://launchpadlibrarian.net/206825073/randr_scaling_ubuntu1504.patch](https://launchpadlibrarian.net/206825073/randr_scaling_ubuntu1504.patch)

The page about the bug is here in case that matters: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/883319](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/883319)

---

### Post by JDAIII on 2015-05-22
So I tried to follow the instructions here for installing xorg from source: [http://www.linuxfromscratch.org/blfs/view/svn/x/xorg-server.html](http://www.linuxfromscratch.org/blfs/view/svn/x/xorg-server.html)

But now I'm stuck in dependency hell:

checking for XSERVERCFLAGS... no
configure: error: Package requirements (fixesproto >= 5.0 damageproto >= 1.1 xcmiscproto >= 1.2.0 xtrans >= 1.3.5 bigreqsproto >= 1.1.0 xproto >= 7.0.26 randrproto >= 1.4.0 renderproto >= 0.11 xextproto >= 7.2.99.901 inputproto >= 2.3 kbproto >= 1.0.3 fontsproto >= 2.1.3 pixman-1 >= 0.27.2 videoproto compositeproto >= 0.4 recordproto >= 1.13.99.1 scrnsaverproto >= 1.1 resourceproto >= 1.2.0 xf86driproto >= 2.1.0 glproto >= 1.4.17 dri >= 7.8.0 presentproto >= 1.0 xineramaproto xkbfile  pixman-1 >= 0.27.2 xfont >= 1.4.2 xau xshmfence >= 1.1 xdmcp) were not met:


No package 'xcmiscproto' found
No package 'bigreqsproto' found
No package 'randrproto' found
No package 'renderproto' found
No package 'fontsproto' found
No package 'videoproto' found
No package 'compositeproto' found
No package 'recordproto' found
No package 'scrnsaverproto' found
No package 'resourceproto' found
No package 'xf86driproto' found
No package 'xineramaproto' found
No package 'xkbfile' found
No package 'xfont' found


I'd like to know if I am going about this the right way. I have already applied the patch in the previous post to this, I however did not apply any other patches from the instructions above since I do not use gcc 5 or above and I do not see the use for the others for me.

---

### Post by JDAIII on 2015-05-22
So, I got past the dependency hell, But now I am having an issue that I do not quite understand. This is the latest thing in the output when I'm trying to ./configure

drmmode_display.c: In function 'drmmode_set_cursor':
drmmode_display.c:427:13: error: implicit declaration of function 'drmModeSetCursor2' [-Werror=implicit-function-declaration]
             drmModeSetCursor2(drmmode->fd, drmmode_crtc->mode_crtc->crtc_id,
             ^
drmmode_display.c:427:13: warning: nested extern declaration of 'drmModeSetCursor2' [-Wnested-externs]
cc1: some warnings being treated as errors
Makefile:714: recipe for target 'drmmode_display.lo' failed
make[5]: *** [drmmode_display.lo] Error 1
make[5]: Leaving directory '/home/jd/Downloads/xorg-server-1.17.1/hw/xfree86/drivers/modesetting'
Makefile:573: recipe for target 'all-recursive' failed
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory '/home/jd/Downloads/xorg-server-1.17.1/hw/xfree86/drivers'
Makefile:830: recipe for target 'all-recursive' failed
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory '/home/jd/Downloads/xorg-server-1.17.1/hw/xfree86'
Makefile:644: recipe for target 'all' failed
make[2]: *** [all] Error 2
make[2]: Leaving directory '/home/jd/Downloads/xorg-server-1.17.1/hw/xfree86'
Makefile:589: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/jd/Downloads/xorg-server-1.17.1/hw'
Makefile:757: recipe for target 'all-recursive' failed
make: *** [all-recursive] Error 1

---

