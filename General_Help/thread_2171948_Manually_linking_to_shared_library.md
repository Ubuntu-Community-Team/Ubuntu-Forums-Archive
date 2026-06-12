---
title: "Manually linking to shared library"
date: 2013-09-02
forum: General Help
---

### Post by paul-aspras on 2013-09-02
First off here is the output of ldd 
> 
    linux-gate.so.1 =>  (0xf77b8000)
    libSDL2-2.0.so.0 => not found
    libGL.so.1 => /usr/lib32/fglrx/libGL.so.1 (0xf76b5000)
    libGLU.so.1 => not found
    libfmodex-4.42.03.so => not found
    libfmodevent-4.42.03.so => not found
    libfmodeventnet-4.42.03.so => not found
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf769e000)
    libsteam_api.so => not found
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7698000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf767d000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf7598000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf756c000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf754d000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf73a4000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf7392000)
    /lib/ld-linux.so.2 (0xf77b9000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf725e000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf723d000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf7238000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf7231000)


I download and built SDL 2 from source, the libraries themselves are now installed in /usr/local/lib. So I open /etc/ld.so.conf I add /usr/local/lib and save it then run ldconfig however ldd still cannot find libSDL2-2.0.so.0 .

---

