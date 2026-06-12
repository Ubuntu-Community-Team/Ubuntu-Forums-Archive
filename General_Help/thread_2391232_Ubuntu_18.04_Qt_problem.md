---
title: "Ubuntu 18.04 Qt problem"
date: 2018-05-07
forum: General Help
---

### Post by fulton-gonzalez on 2018-05-07
Fresh install of Bionic went well. I install Texmaker for work but it fails to start, with the message: 

[COLOR=#000000][FONT=Verdana]This application failed to start because it could not find or load the Qt platform plugin "xcb" in "".

Any fixes?  Attempting to start Texstudio or Texworks results in the same error message. 


[/FONT][/COLOR]

---

### Post by spjackson on 2018-05-07
Welcome to the forums.

How did you install Texmaker? Do you have libqt5gui5 installed? (This provides /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so.)

---

### Post by fulton-gonzalez on 2018-05-07
Thanks, I find the forums very useful!

Yes, all dependencies, including libqtgui5, were installed as part of the normal installation (apt install) process for Texmaker. The libqxcb.so file exists and is where it should be.

I'm wondering if there is some sort of environment variable I should set?
[COLOR=#000000]
[/COLOR]

---

### Post by monkeybrain20122 on 2018-05-07
Please run ldd on the binary of texmaker and post the output here

e.g if the executable is /usr/bin/texmaker (I don't know exactly what it is, I don't have it installed)

run

```

ldd /usr/bin/textmaker
```

---

### Post by fulton-gonzalez on 2018-05-08
ldd /usr/bin/texmaker 
	linux-vdso.so.1 (0x00007ffe2452e000)
	libsynctex.so.1 => /usr/lib/x86_64-linux-gnu/libsynctex.so.1 (0x00007f901c321000)
	libQt5PrintSupport.so.5 => /usr/lib/x86_64-linux-gnu/libQt5PrintSupport.so.5 (0x00007f901c0b2000)
	libQt5Widgets.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (0x00007f901b86b000)
	libQt5Gui.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5 (0x00007f901b102000)
	libQt5Xml.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Xml.so.5 (0x00007f901aec6000)
	libQt5Network.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Network.so.5 (0x00007f901ab3a000)
	libQt5Script.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Script.so.5 (0x00007f901a6a4000)
	libQt5Core.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Core.so.5 (0x00007f9019f59000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f9019d3a000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f90199ac000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f901960e000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f901921d000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f9019000000)
	libGL.so.1 => /usr/lib/x86_64-linux-gnu/libGL.so.1 (0x00007f9018d74000)
	libpng16.so.16 => /usr/lib/x86_64-linux-gnu/libpng16.so.16 (0x00007f9018b42000)
	libharfbuzz.so.0 => /usr/lib/x86_64-linux-gnu/libharfbuzz.so.0 (0x00007f90188a4000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f901868c000)
	libicui18n.so.60 => /usr/lib/x86_64-linux-gnu/libicui18n.so.60 (0x00007f90181eb000)
	libicuuc.so.60 => /usr/lib/x86_64-linux-gnu/libicuuc.so.60 (0x00007f9017e34000)
	libdouble-conversion.so.1 => /usr/lib/x86_64-linux-gnu/libdouble-conversion.so.1 (0x00007f9017c23000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f9017a1f000)
	libglib-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f9017709000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f901d106000)
	libGLX.so.0 => /usr/lib/x86_64-linux-gnu/libGLX.so.0 (0x00007f90174d8000)
	libGLdispatch.so.0 => /usr/lib/x86_64-linux-gnu/libGLdispatch.so.0 (0x00007f9017222000)
	libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f9016f6e000)
	libgraphite2.so.3 => /usr/lib/x86_64-linux-gnu/libgraphite2.so.3 (0x00007f9016d41000)
	libicudata.so.60 => /usr/lib/x86_64-linux-gnu/libicudata.so.60 (0x00007f9015198000)
	libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f9014f26000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f9014bed000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f90149c5000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f90147c1000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f90145bb000)
	libbsd.so.0 => /lib/x86_64-linux-gnu/libbsd.so.0 (0x00007f90143a6000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f901419e000)

---

### Post by dino99 on 2018-05-08
Be sure to run a gnome on xorg session, not a wayland one (install gnome-session if needed)

---

### Post by spjackson on 2018-05-09
Perhaps this solution to a similar problem will help. [https://ubuntuforums.org/showthread.php?t=2391244](https://ubuntuforums.org/showthread.php?t=2391244)

---

