---
title: "ATI 8.32.5 driver on XPRESS 200m Card"
date: 2006-12-14
forum: General Help
---

### Post by btboudreaux on 2006-12-14
Has anyone tried this out to see if the sideport memory works on the XPRESS 200m?

Just want to know because if their is still no sideport memory support then I'll pass on this driver too.

Thanks!

---

### Post by bofphile on 2006-12-14
Yes, it works. :D

---

### Post by oracle5 on 2006-12-14
Works great.

---

### Post by lnxusr on 2006-12-14
Working great for me as well, Including XGL/Beryl.
Here is some info that can help you if you have trouble installing them:
The following scripts will download, build, install, and configure the 8.32.5 drivers:
Dapper:
[http://lnxusr.phpnet.us/ati-8.32.5-builder.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder.sh)
Edgy:
[http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh)
If you still don't have 3D acceleration on Edgy, add the following to your xorg.conf:
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```
If you still have no 3D accel, try the following:
```
sudo rmmod radeon
sudo rmmod drm
sudo morprobe fglrx
ctrl alt backspace (restart X server)
```
If you have any other problems, let them be known.

---

### Post by btboudreaux on 2006-12-14
I am in complete shock that it works! As soon as I get some free time im going to try and install it.

One more question, do you have to have UMA+sideport enabled? or can it just work with only sideport enabled?

---

### Post by btboudreaux on 2006-12-14
Nevermind... it works! awesome!

---

### Post by TDsai on 2006-12-15
> **lnxusr said:**
> Working great for me as well, Including XGL/Beryl.
Here is some info that can help you if you have trouble installing them:
The following scripts will download, build, install, and configure the 8.32.5 drivers:
Dapper:
[http://lnxusr.phpnet.us/ati-8.32.5-builder.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder.sh)
Edgy:
[http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh)
If you still don't have 3D acceleration on Edgy, add the following to your xorg.conf:
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```
If you still have no 3D accel, try the following:
```
sudo rmmod radeon
sudo rmmod drm
sudo morprobe fglrx
ctrl alt backspace (restart X server)
```
If you have any other problems, let them be known.

hi thanks for making it easier for innocent people like me =) but is this script for all ati cards or XPRESS only?

---

### Post by dzoster on 2006-12-15
Xgl, leaves me with a frozen console.   any chance you can post your config files and what you did to make xgl work.

also i am wary of this new update.. i have had a few odd things happen. Some weird stall's and freezes please take caution.. i wouldn't call this stable system ready yet!!!!!!!](*,)

---

### Post by lnxusr on 2006-12-15
> **TDsai said:**
> hi thanks for making it easier for innocent people like me =) but is this script for all ati cards or XPRESS only?
Nope, This should work for any ATI card supported by the proprietary driver. If your card is outdated and no longer supportedm you should try the opensource ATI driver with DRI.

> **dzoster said:**
> Xgl, leaves me with a frozen console.   any chance you can post your config files and what you did to make xgl work.

also i am wary of this new update.. i have had a few odd things happen. Some weird stall's and freezes please take caution.. i wouldn't call this stable system ready yet!!!!!!!](*,)

I used nearly all the stock stuff, other then adding the Section "Extensions" lines in my xorg.conf file. What versions of *ubuntu, Xorg, and the kernel are you using?

---

### Post by jimmyp on 2006-12-15
I have

Section "Extensions"
    Option "Composite" "Disable"
EndSection

in my xorg.conf and fglrx kernel module is loaded but fglrxino still reports

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Any idea why hardware acceleration isn't working?

---

### Post by lnxusr on 2006-12-15
> **jimmyp said:**
> I have

Section "Extensions"
    Option "Composite" "Disable"
EndSection

in my xorg.conf and fglrx kernel module is loaded but fglrxino still reports

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Any idea why hardware acceleration isn't working?

What method did you use to install the driver? It looks like the kernel module might not be loading correctly, or there is something else preventing DRI from loading. Try the following commands:
```
sudo rmmod radeon
sudo rmmod drm
sudo modprobe fglrx
```
then restart X (ctrl alt backspace)

---

### Post by xolot1 on 2006-12-15
thanks lnxusr, i got these drivers working!

i had to include the composite disable option in my xorg.conf file.
will this keep me from running beryl/compiz?
if this is so, how can this be worked around?

thanks again!

willi

---

### Post by TusharG on 2006-12-15
Yes it works now but it still has following problem:

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

Yet the driver will load and AIGLX will be disabled. glxgear runs fine but 3ddeskd is not working properly. It is failing to grab the desktop current images, instead it remains blank. It used to work well with 8.24 driver.

---

### Post by xolot1 on 2006-12-16
well ive got XGL and beryl running using the new drivers :-)

heres my experience:
[B]
i had to make the packages with sideport+uma enabled.[/B]
this yielded successful returns for fglrxinfo, but starting an X session under XGL (my first attempt at at XGL, not AIGLX) gave only a blank tan screen with a mouse.
**at this point switching back to videocard memory only did the trick** - XGL loads properly and flawlessly now.

my laptop is a HP DV8210 (1.8gz, 512mb) ran glxgears around 460-540FPS, but now displays 1700-1800FPS.

goodluck!

willi

---

### Post by azidrane on 2006-12-16
WOO HOO!

I was running with 8.26.5 with shared RAM only.

Now i'm back to dedicated RAM and its WAY faster

Smoother, faster and sweeeeet.


Thanks chap!

P.S. I'm running Dapper Drake with an ATI Xpress 200m on a Compaq R4125CA with new drivers in XGL

---

### Post by sqef on 2006-12-16
I installed the 8.32.5 driver but had to disable the compositing.
I got beryl to work by installing xgl and using it a session.

[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL)

use the second portion on install xgl/beryl after installing drivers using lnxusr method/links

---

### Post by zophiel on 2006-12-17
> **xolot1 said:**
> well ive got XGL and beryl running using the new drivers :-)

heres my experience:
[B]
i had to make the packages with sideport+uma enabled.[/B]
this yielded successful returns for fglrxinfo, but starting an X session under XGL (my first attempt at at XGL, not AIGLX) gave only a blank tan screen with a mouse.
**at this point switching back to videocard memory only did the trick** - XGL loads properly and flawlessly now.

my laptop is a HP DV8210 (1.8gz, 512mb) ran glxgears around 460-540FPS, but now displays 1700-1800FPS.

goodluck!

willi


doing this has definetly worked for hp dv8000 series, with ATI Radeon Xpress 200M (5955)

now my desktop has rain drops on it!

---

### Post by d-E-a-D on 2006-12-19
I have made a how to to simple get it working: [http://ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=200m)

Amd just started to working on our ATI Cards!

Bless AMD! Shame on old ATI owners!

---

### Post by michaeljustman on 2006-12-27
I was using 8.24.8 because I couldn't compile the kernel module for any of the other versions. (I used the version in the repository.)

My HP Pavilion zv6000 with ATI Mobility Radeon XPRESS 200M works great.

Was getting 250 FPS with glxgears. Now 1600 FPS! Was using UMA only, but now using Sideport only!!!!

Thank you so much!

---

### Post by scotty64 on 2006-12-28
It works - even with "Sideport only" in the BIOS! The performance difference is more then significant:
Old ati driver (UMA only): glxgears 497 fps, fgl_glxgears 145 fps
ATI 8.32.5 driver: glxgears 1663 fps ! (More than three times faster!), fgl_glxgears 257 fps.
Even the ugly black shadows that were left behind after you opened a menu in Blender have disappeared.
Well done!

---

### Post by usernamebob on 2006-12-31
Using the above install script my install failed in the module-assistant section.. heres the log file

 dh_testroot                                                                &#8593; 
 &#9474; rm -f configure-stamp                                                      &#9646; 
 &#9474; rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a                               &#9618; 
 &#9474; rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd                        &#9618; 
 &#9474; rm -rf .tmp_versions                                                       &#9618; 
 &#9474; rm -rf patch                                                               &#9618; 
 &#9474; dh_clean                                                                   &#9618; 
 &#9474; rm /usr/src/modules/fglrx/debian/control                                   &#9618; 
 &#9474; rm /usr/src/modules/fglrx/debian/dirs                                      &#9618; 
 &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           &#9618; 
 &#9474;         cat /usr/src/modules/fglrx/debian/control.template >               &#9618; 
 &#9474; /usr/src/modules/fglrx/debian/control; \                                   &#9618; 
 &#9474;         fi                                                                 &#9618; 
 &#9474; if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \                   &#9618; 
 &#9474;         mv /usr/src/modules/fglrx/debian/postinst                          &#8595; 
 /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.19-7-generic.postinst; \    &#8593; 
 &#9474;         fi                                                                 &#9618; 
 &#9474; dh_testdir                                                                 &#9618; 
 &#9474; touch configure-stamp                                                      &#9618; 
 &#9474; dh_testdir                                                                 &#9618; 
 &#9474; /usr/bin/make -C /lib/modules/2.6.19-7-generic/build                       &#9618; 
 &#9474; SUBDIRS=/usr/src/modules/fglrx modules                                     &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/linux-headers-2.6.19-7-generic'      &#9646; 
 &#9474;   CC [M]  /usr/src/modules/fglrx/firegl_public.o                           &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:89:26: error: linux/config.h: No    &#9618; 
 &#9474; such file or directory                                                     &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:456: warning: initialization from   &#9618; 
 &#9474; incompatible pointer type                                                  &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_stub_open’:    &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:579: warning: assignment discards   &#8595; 
 qualifiers from pointer target type                                        &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_request_irq’:    &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:2568: warning: passing argument 2   &#9618; 
 &#9474; of ‘request_irq’ from incompatible pointer type                            &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function                        &#9618; 
 &#9474; ‘__ke_smp_call_function’:                                                  &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:4008: warning: passing argument 1   &#9618; 
 &#9474; of ‘smp_call_function’ from incompatible pointer type                      &#9618; 
 &#9474; make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1              &#9618; 
 &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/linux-headers-2.6.19-7-generic'       &#9646; 
 &#9474; make: *** [build] Error 2

---

### Post by michaeljustman on 2006-12-31
Do you have...

```

Section "DRI"
        Mode         0666
EndSection

```

in your xorg.conf?

---

### Post by usernamebob on 2006-12-31
Fixed.. if anyone else has that problem.. try this

sudo mkdir -p /usr/src/modules/fglrx/linux
sudo touch /usr/src/modules/fglrx/linux/config.h

---

### Post by kcallis on 2007-01-01
> **zophiel said:**
> doing this has definetly worked for hp dv8000 series, with ATI Radeon Xpress 200M (5955)

now my desktop has rain drops on it!
Ok, I am almost there (and I swear if I get this graphics issue working, I will not upgrade any kernels, etc.). I got fglrx working... Was feeling bold, so I added the beryl stuff... Dropped the memory on the card back to 128M, and it is till booting and running. With that said, I am almost a very happy camper!!!

Did a glxinfo, and this is what I got:

kcc ~ $ glxinfo 
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 1.2 (2.0.6234 (8.32.5))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon

So, what do I need to do to get DRI and direct rendering working?

As a side note, how does one figure out the frame rate of your graphics card using glxgears?

---

### Post by fancyydk on 2007-01-05
Thanks usernamebob! I had the same problem as you and your solution fixed my problem!

---

### Post by Stochastic on 2007-01-11
What method do people use to get Dapper running beryl or compiz (I don't care which) after they've installed this driver?

---

### Post by Stochastic on 2007-01-11
I just got the new fglrx working on my Xpress 200m.  My fglrxinfo returns: ```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

and my 'glxinfo | grep render' returns: ```
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON XPRESS Series Generic

```

However I can't figure out how to turn off UMA.  My bios only allows me to switch video memory ammounts from 32 to 64 to 128.  I'm running a Compaq Presario V2630CA.  I'd like to get Compiz or Beryl working or at least a better glxgears rate than 400FPS.

---

### Post by locutus42 on 2007-01-13
> **Stochastic said:**
> 
However I can't figure out how to turn off UMA.  My bios only allows me to switch video memory ammounts from 32 to 64 to 128.  I'm running a Compaq Presario V2630CA.  I'd like to get Compiz or Beryl working or at least a better glxgears rate than 400FPS.

You can only turn off UMA if you have hardware with dedicated/on-board/Sideport video memory. Not all systems have this onboard video memory so you might have purchased such a system. It was an option when I purchased my Compaq R4000 laptop and I paid extra for the 128MB of Sideport memory.

---

### Post by locutus42 on 2007-01-13
Thanks for posting/trying this new driver with Sideport-only. I was able to get the new driver working on my Compaq R4000 and I'm sooo happy ATI finally fixed this.

One note to anybody who might have installed the Ubuntu restricted drivers( fglrx ). You'll want to uninstall this and rerun the ATI driver install( script or otherwise ). Before I did that, I was still seeing direct rendering failing to install and tracked it back to the OLD fglrx driver being loaded from the kernel restricted drivers instead of the new ATI fglrx.

FYI, running glxgears from an old Ubuntu Hoary installation( /usr/X11R6/bin/glxgears ) returned an impressive 1620 FPS and the current fgl_gxgears returns 229 FPS using the 2.6.15-27-k7 kernel( R4000 = 3000+ AMD Sempron ). Previously, I was getting ~1200 FPS and 200 FPS respectively.

Thanks again to everyone who posted to this thread. :-)

---

### Post by Stochastic on 2007-01-13
> **locutus42 said:**
> You can only turn off UMA if you have hardware with dedicated/on-board/Sideport video memory. Not all systems have this onboard video memory so you might have purchased such a system. It was an option when I purchased my Compaq R4000 laptop and I paid extra for the 128MB of Sideport memory.

Is there any way to upgrade my system to include this feature now?  I assume it'd be similar to getting a new video card, and if that's the case would it be more/less difficult/expensive to get a new video card.  Is it even possible with a laptop to reconfigure the video card?

---

### Post by xxrealmsxx on 2007-01-14
> **Stochastic said:**
> Is there any way to upgrade my system to include this feature now?  I assume it'd be similar to getting a new video card, and if that's the case would it be more/less difficult/expensive to get a new video card.  Is it even possible with a laptop to reconfigure the video card?

It's impossible to upgrade the video card in our laptops.

There are some vendors working on external video cards right now though so crossing your fingers and waiting is all you can do :(.

---

### Post by locutus42 on 2007-01-16
I was finally able to get Xgl and Compiz working on the ATI Express 200M using the 8.33.6 driver and 128MB of sideport video memory.

here's what I did:
```

Ctl-alt-F1
sudo /etc/init.d/kdm stop
sudo apt-get xserver-xgl compiz compiz-kde compiz-gnome
export LIBGL_DRIVERS_PATH=/usr/lib/dri
export LD_LIBRARY_PATH=/usr/lib/fglrx
sudo Xgl :1 -fullscreen -fp /usr/share/X11/fonts/misc -ac -accel xv:pbuffer -accel glx:pbuffer -br & DISPLAY=:1 xterm

in the xterm open in the new Xgl session( move mouse there to activate input ):
compiz --display :1 --replace gconf cube decoration fade minimize move place resize rotate scale switcher wobbly zoom &
gnome-window-decorator &
startkde

```

You should now have your KDE desktop running on compiz with gnome menus. I had tried starting the kde-windows-decorator but it didn't work so I used the gnome one.

To change virtual 3D desktops use the Ctl-Alt-[right arrow]|[left arrow] keys

To stop this and go back just exit all your open apps except the one xterm originally open. Use Ctl-C there to kill the startkde process and that'll kill KDE. Then go to Ctl-Alt-F1, enter Ctl-C there to kill Xgl and then restart your kdm window manager with "sudo /etc/init.d/kdm start" and you'll be back to your regular login screen and sessions.

Have fun.

---

### Post by sharn on 2007-01-23
> **jimmyp said:**
> I have

Section "Extensions"
    Option "Composite" "Disable"
EndSection

in my xorg.conf and fglrx kernel module is loaded but fglrxino still reports

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Any idea why hardware acceleration isn't working?

I hate replying to such an old topic, but I can't seem to get this either. I get the *exact* same output as this one. ^

I tried this:
> 
sudo rmmod radeon
sudo rmmod drm
sudo modprobe fglrx

It told me both radeon and drm didn't exist. (Or something along those lines) And didn't give any info on the modprobe. I've tried several times to get this to work but haven't been able to. It's a Radeon Xpress 200, (Not M, or G) and I haven't changed anything in the BIOS for the card yet. I've gotten it to load the orange background and mouse, as mentioned above, but I couldn't do anything from there, so I reverted back.

Can anyone help here? (I'm still fairly new to the command line, so no fancy talk if that's possible. :P)

Thanks for any help.

EDIT:
I actually used this one last:
[http://ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=200m)

I got to here:
> And that should work!

Now, let's get XGL and Beryl working:
Add this to your sources.list (/etc/apt/sources.list):

But didn't go any farther, because I don't want to start with Beryl until I get XGL running. I just realised I have to do the next step to get XGL running, I think. Is that true?

---

