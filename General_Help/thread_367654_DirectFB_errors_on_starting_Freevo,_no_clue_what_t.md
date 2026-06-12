---
title: "DirectFB errors on starting Freevo, no clue what to do..."
date: 2007-02-22
forum: General Help
---

### Post by Arandil on 2007-02-22
I recently installed Freevo on my Via Epia-system. As base sytem ubuntu server edition is used. Now when I want to start Freevo by giving the command "freevo", I receive a whole lot of output with no significant meaning to me whatsoever. This is what I've managed to capture:

```

Warning: display is set to x11, but the environment has no DISPLAY set. Setting display to fbdev.

Error: VIDEO_SHOW_DATA_DIR not found
ROM_DRIVES: Auto-detected and added "('/media/cdrom0', '/dev/hdc', 'CD-1')"
Warning: Installed mmpython version is old.
Please update mmpython to version 0.4.10 or higher, get it with subversion
svn export svn://svn.freevo.org/kaa/branches/mmpython-0-4/mmpython mmpython-0.4.10

WARNING: PyLirc not found, lirc remo

       ---------------------- DirectFB v0.9.24 ---------------------
             (c) 2000-2002  convergence integrated media GmbH  
             (c) 2002-2004  convergence GmbH                   
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-10-13 15:40) 
(*) Direct/Memcpy: Using linux kernel memcpy()
(!) Direct/Util: opening '/dev/fb0' failed
    --> Permission denied
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!

       ---------------------- DirectFB v0.9.24 ---------------------
             (c) 2000-2002  convergence integrated media GmbH  
             (c) 2002-2004  convergence GmbH                   
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-10-13 15:40) 
(*) Direct/Memcpy: Using libc memcpy()
(!) Direct/Util: opening '/dev/fb0' failed
    --> Permission denied
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!

te control disabled!
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/freevo/main.py", line 137, in ?
    import menu    # The menu widget class
  File "/usr/lib/python2.4/site-packages/freevo/menu.py", line 37, in ?
    import skin
  File "/usr/lib/python2.4/site-packages/freevo/skin.py", line 98, in ?
    get_singleton()
  File "/usr/lib/python2.4/site-packages/freevo/skin.py", line 79, in get_singleton
    exec('import skins.' + config.SKIN_MODULE  + '.' + config.SKIN_MODULE  + \
  File "<string>", line 1, in ?
  File "/usr/lib/python2.4/site-packages/freevo/skins/main/main.py", line 51, in ?
    from area import Skin_Area
  File "/usr/lib/python2.4/site-packages/freevo/skins/main/area.py", line 67, in ?
    import xml_skin
  File "/usr/lib/python2.4/site-packages/freevo/skins/main/xml_skin.py", line 54, in ?
    osd = osd.get_singleton()
  File "/usr/lib/python2.4/site-packages/freevo/osd.py", line 122, in get_singleton
    _singleton = OSD()
  File "/usr/lib/python2.4/site-packages/freevo/osd.py", line 360, in __init__
    pygame.display.init()
pygame.error: DirectFBCreate: Initialization error!

```

I've installed libdrectfb, but that doesn't seem to help. The xserver-xorg-video-via driver is also installed, don't know if it's working however. Can someone please help me out with this?

---

### Post by Jussi Kukkonen on 2007-02-22
So which video output system are you trying to use: framebuffer or X server? (I haven't used Freevo, but I assume both are possible).

If you want to run it in X, you should try setting the DISPLAY variable before starting freevo.

If you want fb, check the ownership and permissions on /dev/fb*. One good solution is to set owner & group as root:video and giving both rw-permissions (this should be the case automatically if I remember correctly). Then add the freevo user to group video.

---

