---
title: "Skype: Refusing to initialize GTK+"
date: 2014-06-07
forum: General Help
---

### Post by chaosdesigner on 2014-06-07
Hi guys,

I recently upgraded to 14.04 and now I'm having problems starting skype. Everytime I start the application I get the following error:

```
(process:20970): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
```

If I start the program as root it actually boots up but there is no sound and after a few minutes a disturbing noise appears that only goes away after closing skype. 

I have reinstalled skype countless times, both from the website and the Canonical Partner Repository with nothing chaning.

Does anybody have any clues on what I have to do to solve this problem?

Thank you!

---

### Post by bzhao on 2014-06-07
Please run command:
    sudo ldd  /usr/bin/skype  
and then check output lines and see if it have line containing "> not found" string.

If so, Please install the relevant lib 

my result is:
	linux-gate.so.1 =>  (0xf7795000)
	libasound.so.2 => /usr/lib/i386-linux-gnu/libasound.so.2 (0xf588f000)
	libXv.so.1 => /usr/lib/i386-linux-gnu/libXv.so.1 (0xf5889000)
	libXss.so.1 => /usr/lib/i386-linux-gnu/libXss.so.1 (0xf5884000)
	librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf587b000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf5876000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf5742000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf572f000)
	libQtDBus.so.4 => /usr/lib/i386-linux-gnu/libQtDBus.so.4 (0xf56b1000)
	libQtWebKit.so.4 => /usr/lib/i386-linux-gnu/libQtWebKit.so.4 (0xf35ac000)
	libQtXml.so.4 => /usr/lib/i386-linux-gnu/libQtXml.so.4 (0xf3569000)
	libQtGui.so.4 => /usr/lib/i386-linux-gnu/libQtGui.so.4 (0xf2ab5000)
	libQtNetwork.so.4 => /usr/lib/i386-linux-gnu/libQtNetwork.so.4 (0xf296e000)
	libQtCore.so.4 => /usr/lib/i386-linux-gnu/libQtCore.so.4 (0xf2685000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf2669000)
	libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf2580000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf253a000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf251d000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf236d000)
	/lib/ld-linux.so.2 (0xf7796000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf234b000)
	libdbus-1.so.3 => /lib/i386-linux-gnu/libdbus-1.so.3 (0xf2300000)
	libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf22e6000)
	libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf22db000)
	libjpeg.so.8 => /usr/lib/i386-linux-gnu/libjpeg.so.8 (0xf227f000)
	libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xf2257000)
	libxslt.so.1 => /usr/lib/i386-linux-gnu/libxslt.so.1 (0xf2219000)
	libxml2.so.2 => /usr/lib/i386-linux-gnu/libxml2.so.2 (0xf20bf000)
	libgstapp-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0 (0xf20b1000)
	libgstpbutils-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstpbutils-1.0.so.0 (0xf208b000)
	libgstvideo-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstvideo-1.0.so.0 (0xf2043000)
	libgstaudio-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstaudio-1.0.so.0 (0xf1ff1000)
	libgstbase-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstbase-1.0.so.0 (0xf1f8d000)
	libgstreamer-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstreamer-1.0.so.0 (0xf1e8a000)
	libgobject-2.0.so.0 => /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 (0xf1e37000)
	libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xf1d2b000)
	libsqlite3.so.0 => /usr/lib/i386-linux-gnu/libsqlite3.so.0 (0xf1c6e000)
	libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xf1c33000)
	libQtOpenGL.so.4 => /usr/lib/i386-linux-gnu/libQtOpenGL.so.4 (0xf1b37000)
	libGL.so.1 => /usr/lib32/nvidia-331-updates/libGL.so.1 (0xf1a32000)
	libaudio.so.2 => /usr/lib/i386-linux-gnu/libaudio.so.2 (0xf1a18000)
	libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf1978000)
	libSM.so.6 => /usr/lib/i386-linux-gnu/libSM.so.6 (0xf196f000)
	libICE.so.6 => /usr/lib/i386-linux-gnu/libICE.so.6 (0xf1955000)
	libXi.so.6 => /usr/lib/i386-linux-gnu/libXi.so.6 (0xf1943000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf193f000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf1938000)
	liblzma.so.5 => /lib/i386-linux-gnu/liblzma.so.5 (0xf1912000)
	liborc-0.4.so.0 => /usr/lib/i386-linux-gnu/liborc-0.4.so.0 (0xf1881000)
	libgsttag-1.0.so.0 => /usr/lib/i386-linux-gnu/libgsttag-1.0.so.0 (0xf1849000)
	libgmodule-2.0.so.0 => /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0 (0xf1844000)
	libffi.so.6 => /usr/lib/i386-linux-gnu/libffi.so.6 (0xf183d000)
	libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf17ff000)
	libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf17d5000)
	libnvidia-tls.so.331.38 => /usr/lib32/nvidia-331-updates/tls/libnvidia-tls.so.331.38 (0xf17d1000)
	libnvidia-glcore.so.331.38 => /usr/lib32/nvidia-331-updates/libnvidia-glcore.so.331.38 (0xef58d000)
	libXt.so.6 => /usr/lib/i386-linux-gnu/libXt.so.6 (0xef531000)
	libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0xef52b000)

---

