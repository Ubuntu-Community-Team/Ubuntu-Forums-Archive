---
title: "App cannon run, it requests libpng.so.3"
date: 2014-07-04
forum: General Help
---

### Post by obake2 on 2014-07-04
I'm trying to run [Super Mario War ]("http://supermariowar.supersanctuary.net/")(you can [download here]("https://code.google.com/p/supermariowar/")), but I'm getting the following error.

```
Dark@Dart:~/Downloads/Super Mario usr/games$ ./smw
./smw: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory


```

I tried looking for libpng.so.3 or similar, so I installed libpng3 from the repository, but the results are the same.

```
Dark@Dart:~/Downloads/Super Mario usr/games$ find / -iname "libpng*.so*" 2>/dev/null
/lib/x86_64-linux-gnu/libpng12.so.0.50.0
/lib/x86_64-linux-gnu/libpng12.so.0
/lib/i386-linux-gnu/libpng12.so.0.50.0
/lib/i386-linux-gnu/libpng12.so.0
/usr/lib/x86_64-linux-gnu/libpng.so.3
/usr/lib/x86_64-linux-gnu/libpng12.so.0
/usr/lib/i386-linux-gnu/libpng12.so.0
/usr/lib/vlc/plugins/codec/libpng_plugin.so


```

```
Dark@Dart:~/Downloads/Super Mario usr/games$ ldd smw
    linux-gate.so.1 =>  (0xf77c8000)
    libSDL-1.2.so.0 => /usr/lib/i386-linux-gnu/libSDL-1.2.so.0 (0xf770c000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf76f0000)
    libSDL_image-1.2.so.0 => /usr/lib/i386-linux-gnu/libSDL_image-1.2.so.0 (0xf76d1000)
    libSDL_mixer-1.2.so.0 => /usr/lib/i386-linux-gnu/libSDL_mixer-1.2.so.0 (0xf767f000)
    libpng.so.3 => not found
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf7596000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7550000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf7532000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7383000)
    libasound.so.2 => /usr/lib/i386-linux-gnu/libasound.so.2 (0xf728d000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7288000)
    libpulse-simple.so.0 => /usr/lib/i386-linux-gnu/libpulse-simple.so.0 (0xf7283000)
    libpulse.so.0 => /usr/lib/i386-linux-gnu/libpulse.so.0 (0xf7233000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf70ff000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf70ec000)
    libcaca.so.0 => /usr/lib/i386-linux-gnu/libcaca.so.0 (0xf7020000)
    /lib/ld-linux.so.2 (0xf77c9000)
    libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xf6ff8000)
    libjpeg.so.8 => /usr/lib/i386-linux-gnu/libjpeg.so.8 (0xf6f9c000)
    libtiff.so.5 => /usr/lib/i386-linux-gnu/libtiff.so.5 (0xf6f29000)
    libwebp.so.5 => /usr/lib/i386-linux-gnu/libwebp.so.5 (0xf6ed9000)
    libmikmod.so.2 => /usr/lib/i386-linux-gnu/libmikmod.so.2 (0xf6e98000)
    libfluidsynth.so.1 => /usr/lib/i386-linux-gnu/libfluidsynth.so.1 (0xf6dc3000)
    libvorbisfile.so.3 => /usr/lib/i386-linux-gnu/libvorbisfile.so.3 (0xf6db8000)
    libFLAC.so.8 => /usr/lib/i386-linux-gnu/libFLAC.so.8 (0xf6d84000)
    libmad.so.0 => /usr/lib/i386-linux-gnu/libmad.so.0 (0xf6d6c000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf6d63000)
    libpulsecommon-4.0.so => /usr/lib/i386-linux-gnu/pulseaudio/libpulsecommon-4.0.so (0xf6cf3000)
    libjson-c.so.2 => /lib/i386-linux-gnu/libjson-c.so.2 (0xf6ce8000)
    libdbus-1.so.3 => /lib/i386-linux-gnu/libdbus-1.so.3 (0xf6c9d000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf6c7b000)
    libslang.so.2 => /lib/i386-linux-gnu/libslang.so.2 (0xf6b4c000)
    libncursesw.so.5 => /lib/i386-linux-gnu/libncursesw.so.5 (0xf6b15000)
    libtinfo.so.5 => /lib/i386-linux-gnu/libtinfo.so.5 (0xf6af2000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf6ad8000)
    liblzma.so.5 => /lib/i386-linux-gnu/liblzma.so.5 (0xf6ab2000)
    libjbig.so.0 => /usr/lib/i386-linux-gnu/libjbig.so.0 (0xf6aa3000)
    libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xf6997000)
    libjack.so.0 => /usr/lib/i386-linux-gnu/libjack.so.0 (0xf6944000)
    libsndfile.so.1 => /usr/lib/i386-linux-gnu/libsndfile.so.1 (0xf68d2000)
    libreadline.so.6 => /lib/i386-linux-gnu/libreadline.so.6 (0xf6894000)
    libvorbis.so.0 => /usr/lib/i386-linux-gnu/libvorbis.so.0 (0xf6868000)
    libogg.so.0 => /usr/lib/i386-linux-gnu/libogg.so.0 (0xf685f000)
    libwrap.so.0 => /lib/i386-linux-gnu/libwrap.so.0 (0xf6854000)
    libasyncns.so.0 => /usr/lib/i386-linux-gnu/libasyncns.so.0 (0xf684d000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6849000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6842000)
    libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf6804000)
    libvorbisenc.so.2 => /usr/lib/i386-linux-gnu/libvorbisenc.so.2 (0xf668b000)
    libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xf6672000)
    libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf665a000)
Dark@Dart:~/Downloads/Super Mario usr/games$ 


```

What should I do?
Thank you in advance.

---

### Post by kostkon on 2014-07-04
I'm guessing you are on a 64bit installation and the game is 32bit, so try installing the 32bit version of libpng3, i.e.:
```
sudo apt-get install libpng3:i386
```

---

### Post by obake2 on 2014-07-04
Awesome! That did the trick [COLOR=#000000]kostkon. :)
[/COLOR]
Hmmm... so I can intall 32bit version of some packages, but only with the Terminal? I don't see it with Synaptic.

---

