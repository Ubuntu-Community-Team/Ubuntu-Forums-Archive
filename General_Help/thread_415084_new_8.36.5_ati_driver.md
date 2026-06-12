---
title: "new 8.36.5 ati driver"
date: 2007-04-20
forum: General Help
---

### Post by FFfanatic on 2007-04-20
ok, I downloaded the new driver but when I try to install it, it gives me this:

Created directory fglrx-install.ZT8628
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.36.5...............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.2.x

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.ZT8628

Do I have the newest one already because I have X.Org 7.2.x? Or would I have to downgrade to get to this driver (if it's better than the one I already have)? If so, how would I downgrade?

---

### Post by undercover90 on 2007-04-20
I've the same problem!

---

### Post by Inspire1997 on 2007-04-22
Same here!

---

### Post by kerrin on 2007-04-23
Same message with feisty..   Site says it should support xorg 7.2...

---

### Post by kerrin on 2007-04-23
creating then installing the packages worked for me...

./ati-driver-installer-8.36.5-x86.x86_64.run --buildpkg Ubuntu/feisty

---

### Post by Burkey on 2007-04-23
Same, i followed the guide here..

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

and all went well for me (ps, created the debs using that)

---

### Post by hellfried on 2007-04-23
i followed the link provided in the above post but after installation this is my fglrxinfo output:

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

Without 3D acceleration i cannot install beryl. help!:confused: 

when i try to look at my xorg.conf i realised that i don't even have one in etc/X11!

---

### Post by Burkey on 2007-04-23
Did you run aticonfig to create the initial file?  You may need to look at your kernel logs and xorg log files under /var/log

I am no expert but the messages it spits out usually help a lot to work it out.

The other "gotcha" is if you did not blacklist the ubuntu fglrx module?  Sorry I am not a great help.. was a while since I done my initial install

---

### Post by hellfried on 2007-04-23
i manually changed the entry in 'devices' from 'ati' to 'fgrlx', but to no avail. i have also blacklisted the ubuntu fglrx module.  the worse part is i cannot change my screen resolution. its currently a horrible ' 1024 x 768' and there are no options for it to go higher. btw my graphics card is an ati x550.

---

### Post by deathbyswiftwind on 2007-04-23
Did you notice any performance gain from the new drivers?

---

### Post by lavinog on 2007-04-23
same message here.
I just upgraded from edgy with working 8.35 drivers using the update manager.
i have been successful pretty much every version from 8.28 using the ati linux driver wiki page.
I'll keep trying though, but it could be a bug...actually isn't the whole issue of using this driver a bug?
after finals i will be able to wipe my hd and start over.

---

### Post by mrThefter on 2007-04-25
Hmmm...
I've got a worse problem.

The drivers cause my Xserver to be unable to boot due to Signal 11.

Could it be that I'm running 64bit Feisty?

EDIT: For reference, the backtrace is...
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2adc78b54d40]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlDalHelperValidateModeFromDAL+0x549) [0x2adc7ab76d29]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x2adc7ab5770e]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x877) [0x2adc7ab52e37]
5: /usr/X11R6/bin/X(InitOutput+0x9bc) [0x4657ec]
6: /usr/X11R6/bin/X(main+0x275) [0x436e55]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x2adc78b418e4]
8: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x241) [0x436339]

Fatal server error:
Caught signal 11.  Server aborting

This happens right before the fb submodule is loaded. How do I know? Old fglrx logs.

EDIT: I found out that ddc is the offending module. After reading the modelines for a monitor, then attempting to set a modeline, it crashes. When I disabled the ddc module (hacky method..don't ask for it) I was able to boot into X. However, I don't have acceleration. GART wasn't initialized. Still looking into this.

EDIT2: GART initialization was my problem. Fixed. (fglrx module didn't load. I forgot to do a depmod) Disabling DDC might help, but since NoDDC doesn't work for the fglrx drivers, just comment it out up a bit in xorg.conf, then rename /usr/lib/xorg/modules/libddc.so to something recognizable (so you can restore it later)

---

