---
title: "Commercial app symbol lookup error gdk_rgb_init"
date: 2014-08-12
forum: General Help
---

### Post by akimb0 on 2014-08-12
Hello,

im trying to run a commercial linux app (sitex air) which fails due to missing symbols.
```
~$ /usr/local/air/bin/airshow
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
/usr/local/air/bin/airshow: symbol lookup error: /usr/local/air/bin/airshow: undefined symbol: gdk_rgb_init
```

The app itself is a 32bit executable and im running a 64bit ubuntu system (14.04)
```
~$ file /usr/local/air/bin/airshow 
/usr/local/air/bin/airshow: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
```

It seems like all needed libs are present
```
~$ ldd /usr/local/air/bin/airshow 
    linux-gate.so.1 =>  (0xf778d000)
    libglib-1.2.so.0 => /lib/i386-linux-gnu/libglib-1.2.so.0 (0xf765c000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf7640000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf763a000)
    libgdk-1.2.so.0 => /usr/lib/i386-linux-gnu/libgdk-1.2.so.0 (0xf7595000)
    libgtk-1.2.so.0 => /usr/lib/i386-linux-gnu/libgtk-1.2.so.0 (0xf7046000)
    libgdk_pixbuf.so.2 => /usr/lib/i386-linux-gnu/libgdk_pixbuf.so.2 (0xf7023000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf6e73000)
    libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf6e34000)
    /lib/ld-linux.so.2 (0xf778e000)
    libpangocairo-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0 (0xf6e27000)
    libcairo-gobject.so.2 => /usr/lib/i386-linux-gnu/libcairo-gobject.so.2 (0xf6e20000)
    libgio-2.0.so.0 => /usr/lib/i386-linux-gnu/libgio-2.0.so.0 (0xf6c9f000)
    libXinerama.so.1 => /usr/lib/i386-linux-gnu/libXinerama.so.1 (0xf6c9b000)
    libXi.so.6 => /usr/lib/i386-linux-gnu/libXi.so.6 (0xf6c89000)
    libXrandr.so.2 => /usr/lib/i386-linux-gnu/libXrandr.so.2 (0xf6c7e000)
    libXcursor.so.1 => /usr/lib/i386-linux-gnu/libXcursor.so.1 (0xf6c73000)
    libXcomposite.so.1 => /usr/lib/i386-linux-gnu/libXcomposite.so.1 (0xf6c6f000)
    libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xf6c6b000)
    libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf6c64000)
    libwayland-client.so.0 => /usr/lib/i386-linux-gnu/libwayland-client.so.0 (0xf6c58000)
    libxkbcommon.so.0 => /usr/lib/i386-linux-gnu/libxkbcommon.so.0 (0xf6c1c000)
    libwayland-cursor.so.0 => /usr/lib/i386-linux-gnu/libwayland-cursor.so.0 (0xf6c13000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf6adf000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf6acb000)
    libcairo.so.2 => /usr/lib/i386-linux-gnu/libcairo.so.2 (0xf69a8000)
    libpango-1.0.so.0 => /usr/lib/i386-linux-gnu/libpango-1.0.so.0 (0xf695b000)
    libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xf6920000)
    libgobject-2.0.so.0 => /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 (0xf68ce000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf6887000)
    libgmodule-2.0.so.0 => /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0 (0xf6882000)
    libatk-1.0.so.0 => /usr/lib/i386-linux-gnu/libatk-1.0.so.0 (0xf6861000)
    libatk-bridge-2.0.so.0 => /usr/lib/i386-linux-gnu/libatk-bridge-2.0.so.0 (0xf6837000)
    libpangoft2-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0 (0xf6821000)
    libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf6780000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf6766000)
    libselinux.so.1 => /lib/i386-linux-gnu/libselinux.so.1 (0xf6743000)
    libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf672b000)
    libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf6720000)
    libffi.so.6 => /usr/lib/i386-linux-gnu/libffi.so.6 (0xf6718000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf670f000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf66ed000)
    libpixman-1.so.0 => /usr/lib/i386-linux-gnu/libpixman-1.so.0 (0xf6643000)
    libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xf661b000)
    libxcb-shm.so.0 => /usr/lib/i386-linux-gnu/libxcb-shm.so.0 (0xf6616000)
    libxcb-render.so.0 => /usr/lib/i386-linux-gnu/libxcb-render.so.0 (0xf660c000)
    libthai.so.0 => /usr/lib/i386-linux-gnu/libthai.so.0 (0xf6602000)
    libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf65d9000)
    libatspi.so.0 => /usr/lib/i386-linux-gnu/libatspi.so.0 (0xf65af000)
    libdbus-1.so.3 => /lib/i386-linux-gnu/libdbus-1.so.3 (0xf6563000)
    libharfbuzz.so.0 => /usr/lib/i386-linux-gnu/libharfbuzz.so.0 (0xf650d000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6509000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6502000)
    libdatrie.so.1 => /usr/lib/i386-linux-gnu/libdatrie.so.1 (0xf64f8000)
    libgraphite2.so.3 => /usr/lib/i386-linux-gnu/libgraphite2.so.3 (0xf64dc000)
```

```
~$ objdump -T /usr/local/air/bin/airshow 

/usr/local/air/bin/airshow:     file format elf32-i386

DYNAMIC SYMBOL TABLE:
080783a0      DF *UND*    0000010d              g_print
080783b0      DF *UND*    0000002a              g_free
.
.
.
08078960      DF *UND*    000002df              gdk_rgb_init
.
.
.
080a7e04 g    DO *ABS*    00000000  Base        _end
```

But somehow the symbol gdk_rgb_init which is needed is not found. 

Is there a way i could fix this? 
Or can i determine which lib provides this symbol and add this to the LD_LIBRARY_PATH?

Thanks for a light here :-)

---

### Post by TheFu on 2014-08-12
Does **nm** help?

---

### Post by akimb0 on 2014-08-14
Sorry for the delay, im also talking to the devs for this issue. Im not sure about nm, never used it before, any tips how i could solve this with nm? Is there a manual page i could refer to?

---

### Post by TheFu on 2014-08-14
yes, there is a manpage.  I'm confused why you ask?  **man nm** will display it.

---

### Post by steeldriver on 2014-08-14
How did you install libglib / libgdk / libgtk version **1.2**? did you do that specifically in order to run the 'airshow' app?

FWIW, gdk_rgb_init is defined in libgdk-x11-**2.0**.so on my 32-bit 12.04 system (specifically, /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10)

---

### Post by akimb0 on 2014-08-15
> **TheFu said:**
> yes, there is a manpage.  I'm confused why you ask?  **man nm** will display it. Ah yes... i always forget about that man comand... thanks for that hint :-)

> **steeldriver said:**
> How did you install libglib / libgdk / libgtk version **1.2**? did you do that specifically in order to run the 'airshow' app?

FWIW, gdk_rgb_init is defined in libgdk-x11-**2.0**.so on my 32-bit 12.04 system (specifically, /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10)

Well not that i could remember, i didnt installed any specific package for airshow. libgdk-x11-2.0.so.0.2400.23 is present in my /usr/lib/i386-linux-gnu folder and a ```
nm -D /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.23 | grep gdk_rgb
00030cc0 T gdk_rgb_cmap_free
00030bc0 T gdk_rgb_cmap_new
00030de0 T gdk_rgb_colormap_ditherable
00030e40 T gdk_rgb_ditherable
00042130 T gdk_rgb_dither_get_type
00030b90 T gdk_rgb_find_color
00030fa0 T gdk_rgb_gc_set_background
00030f70 T gdk_rgb_gc_set_foreground
00030e00 T gdk_rgb_get_colormap
000316b0 T gdk_rgb_get_visual
00030b40 T gdk_rgb_init
00030b00 T gdk_rgb_set_install
00030b20 T gdk_rgb_set_min_colors
00030ae0 T gdk_rgb_set_verbose
00030f10 T gdk_rgb_xpixel_from_rgb
```

confirms that. 
But im a little bit lost what a should do now??

---

### Post by steeldriver on 2014-08-15
I think it would be more useful to find what point release your 1.2 version(s) are - it *may* be possible to upgrade to a newer release (but still 1.2 since that appears to be what the app requires) - maybe starting with

```

readlink -f /usr/lib/i386-linux-gnu/libglib-1.2.so

readlink -f /usr/lib/i386-linux-gnu/libgdk-1.2.so

readlink -f /usr/lib/i386-linux-gnu/libgtk-1.2.so

```

---

### Post by akimb0 on 2014-08-17
Thanks steeldriver for your help. Well first of all i found this here in the doc files included

```
[COLOR=#000000][FONT=Arial]**Libraries** 
The user-interface tools such as Air Show and Vshade rely on older  versions of GTK, GDK, and related libraries.  You may need to add the  32-bit version of these libraries to your Linux installation if they are  not already present.  You can see a full list of dependencies with,  e.g., 
[TABLE="width: 100%"]
[TR]
[TD="width: 14"][/TD]
[TD][COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Courier New]ldd $AIRHOME/bin/airshow  
[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]
[TABLE="width: 100%"]
[TR]
[TD="width: 14"][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=Arial]The [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]air[/FONT][/COLOR][COLOR=#000000][FONT=Arial] binaries and other command line tools do not depend on GTK, GDK or the related interface libraries. [/FONT][/COLOR][/FONT][/COLOR]
```

So it seems to me more that maybe an older version of the libs are needed?

This is what readlink gives me as answers:
```
readlink -f -v /usr/lib/i386-linux-gnu/libgdk-1.2.so
/usr/lib/i386-linux-gnu/libgdk-1.2.so

readlink -f -v /usr/lib/i386-linux-gnu/libgtk-1.2.so.0 
/usr/lib/i386-linux-gnu/libgtk-3.so.0.1000.8

```

However libglib-1.2.so.0 is not present in /usr/lib/i386-linux-gnu but it is in 

```
locate libglib-
/lib/i386-linux-gnu/libglib-1.2.so.0
/lib/i386-linux-gnu/libglib-2.0.so.0
/lib/i386-linux-gnu/libglib-2.0.so.0.4000.0
/lib/x86_64-linux-gnu/libglib-1.2.so.0
/lib/x86_64-linux-gnu/libglib-2.0.so.0
/lib/x86_64-linux-gnu/libglib-2.0.so.0.4000.0
```

I also tried to install the older libglib-1.2 packages (6 years old...) this results in a SIGSEV from airshow but the missing symbol error messages are gone. I purged the old packages aftert this try to hold a clean system.

---

### Post by steeldriver on 2014-08-17
```

**readlink** -f -v /usr/lib/i386-linux-gnu/libgtk-[COLOR=#ff0000]**1.2**[/COLOR].so.0 
/usr/lib/i386-linux-gnu/libgtk-[COLOR=#ff0000]**3**[/COLOR].so.0.1000.8

```

seems suspect to me - but I don't really know how you'd go about fixing it without possibly breaking other stuff. Really for such an old library / application it might have been better to keep all its shared libraries in a local directory and used a wrapper script with LD_LIBRARY_PATH (one of the few cases where using LD_LIBRARY_PATH makes sense)

---

### Post by akimb0 on 2014-08-17
Mhmmm maybe thats an idea i could follow and check if an older extracted lib path included in the app directory did the trick. 
I will try that and feedback here.


***EDIT***
This works, app is starting but sadly this is some kind of a really old (and ugly) build...

---

