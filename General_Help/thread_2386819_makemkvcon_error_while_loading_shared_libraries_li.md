---
title: "makemkvcon: error while loading shared libraries: libcrypto.so.1.1"
date: 2018-03-10
forum: General Help
---

### Post by VMC on 2018-03-10
```
makemkvcon: error while loading shared libraries: libcrypto.so.1.1
```
Here's the steps on my install:
```
INSTALL TOOLS CHECK:

$ sudo apt-get install build-essential pkg-config libc6-dev libssl-dev libexpat1-dev libavcodec-dev libgl1-mesa-dev libqt4-dev zlib1g-dev
[sudo] password for vmc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
libqt4-dev is already the newest version (4:4.8.7+dfsg-5ubuntu2).
pkg-config is already the newest version (0.29.1-0ubuntu1).
libc6-dev is already the newest version (2.23-0ubuntu10).
libexpat1-dev is already the newest version (2.1.0-7ubuntu0.16.04.3).
libgl1-mesa-dev is already the newest version (17.2.8-0ubuntu0~16.04.1).
libssl-dev is already the newest version (1.0.2g-1ubuntu4.10).
zlib1g-dev is already the newest version (1:1.2.8.dfsg-2ubuntu4.1).
libavcodec-dev is already the newest version (7:2.8.11-0ubuntu0.16.04.1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




OSS MAKE:


$ ./configure


checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking for gawk... gawk
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for -objcopy... no
checking for objcopy... objcopy
checking for -ld... /usr/bin/ld -m elf_x86_64
checking for a BSD-compatible install... /usr/bin/install -c
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for compress2 in -lz... yes
checking openssl/opensslconf.h usability... yes
checking openssl/opensslconf.h presence... yes
checking for openssl/opensslconf.h... yes
checking for AES_encrypt in -lcrypto... yes
checking expat.h usability... yes
checking expat.h presence... yes
checking for expat.h... yes
checking for XML_ParserCreate in -lexpat... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ffmpeg... yes
checking whether LIBAVCODEC_VERSION_MAJOR is declared... yes
checking LIBAVCODEC_VERSION_MAJOR... 56
checking for AVFrame.nb_samples... yes
checking whether AV_SAMPLE_FMT_U8P is declared... yes
checking for avcodec_encode_audio2... yes
checking for AVCodecContext.refcounted_frames... yes
checking whether avcodec_free_frame is declared... yes
checking whether av_frame_free is declared... yes
checking for av_log_format_line... yes
checking for enum AVCodecID... yes
checking whether AV_CODEC_ID_NONE is declared... yes
checking whether av_frame_get_channels is declared... yes
checking whether av_frame_get_sample_rate is declared... yes
checking whether av_frame_set_channel_layout is declared... yes
checking for AVCodecParserContext.duration... yes
checking whether AV_CH_TOP_BACK_CENTER is declared... yes
checking for qt5... no
checking for qt4... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libffabi/src/ffabicfg.h
config.status: executing libtool commands


$ make


type "sudo make install" to install


$ sudo make install
 
/usr/bin/install -c -D -m 644 out/libdriveio.so.0 /usr/lib/libdriveio.so.0
/usr/bin/install -c -D -m 644 out/libmakemkv.so.1 /usr/lib/libmakemkv.so.1
/usr/bin/install -c -D -m 644 out/libmmbd.so.0 /usr/lib/libmmbd.so.0
ldconfig
/usr/bin/install -c -D -m 755 out/makemkv /usr/bin/makemkv
/usr/bin/install -c -D -m 644 makemkvgui/share/makemkv.desktop /usr/share/applications/makemkv.desktop
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/16x16/makemkv.png /usr/share/icons/hicolor/16x16/apps/makemkv.png
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/22x22/makemkv.png /usr/share/icons/hicolor/22x22/apps/makemkv.png
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/32x32/makemkv.png /usr/share/icons/hicolor/32x32/apps/makemkv.png
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/64x64/makemkv.png /usr/share/icons/hicolor/64x64/apps/makemkv.png
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/128x128/makemkv.png /usr/share/icons/hicolor/128x128/apps/makemkv.png


BIN MAKE:


$ make
type "sudo make install" to install
$ sudo make install
[sudo] password for vmc: 
rm -f /usr/bin/makemkvcon
rm -f /usr/bin/mmdtsdec
rm -f /usr/share/MakeMKV/*
install -d /usr/share/MakeMKV
install -d /usr/bin
install -t /usr/bin bin/amd64/makemkvcon
install -t /usr/bin bin/i386/mmdtsdec
install -m 644 -t /usr/share/MakeMKV src/share/appdata.tar
install -m 644 -t /usr/share/MakeMKV src/share/blues.jar
install -m 644 -t /usr/share/MakeMKV src/share/blues.policy


$ makemkv
/usr/bin/makemkvcon: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory




$ ldd $(which makemkvcon)
    linux-vdso.so.1 =>  (0x00007ffdbf9f6000)
    libmakemkv.so.1 => /usr/lib/libmakemkv.so.1 (0x00007fa6311a7000)
    libdriveio.so.0 => /usr/lib/libdriveio.so.0 (0x00007fa630fa0000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fa630d83000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fa6309b9000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fa6307b5000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fa630433000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fa63022b000)
    libcrypto.so.1.1 => not found
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fa630011000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fa62fde8000)
    libavcodec.so.57 => not found
    libavutil.so.55 => not found
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fa62fadf000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fa62f8c9000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fa63146f000)
```

This all work using the original Xubuntu 16.04.1. It failed to after installing the newest **Xubuntu 16.04.4**.

edit: It obvious "libcryp0.so.1.1" is not installed:
> bionic
$ locate libcrypto
/usr/lib/x86_64-linux-gnu/libcrypto.a
/usr/lib/x86_64-linux-gnu/libcrypto.so
/usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1
/usr/lib/x86_64-linux-gnu/pkgconfig/libcrypto.pc

xenial
$ locate libcrypto
/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
/usr/lib/x86_64-linux-gnu/libcrypto.a
/usr/lib/x86_64-linux-gnu/libcrypto.so
/usr/lib/x86_64-linux-gnu/pkgconfig/libcrypto.pc

I tried several ways to install it, all to no avail. apt-get didn't work, and "libgcrypt11_1.5.0-5+deb7u4_amd64.deb" installed but failed. Most likely the wrong version.
google , makemkv and libcrypto revealed nothing that helped me.

---

### Post by monkeybrain20122 on 2018-03-10
On 16.04.4, I did

```
dpkg -S libcrypto.so
```

It returned

```
libssl-dev:amd64: /usr/lib/x86_64-linux-gnu/libcrypto.so
libssl1.0.0:i386: /lib/i386-linux-gnu/libcrypto.so.1.0.0
libssl1.0.0:amd64: /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
```


So libcrypto (**not libcrypt!**) comes from the package libssl1 and its version is 1.0,  to meet the requirement of makemkvcon you need 1.1 which is not in 16.04's repository. 

It is not a good idea to just grab the libssl deb from Bionic's repository because that may screw up your system's libssl even if the .deb installs. Instead you can compile a local version from source that is only used by makemkv (which is quite easy)

first of all make a directory for your compiled version to install to

```
mkdir openssl
``` this will create a directory called openssl in your $HOME, you can choose other places and other names of course, just make sure you use the path consistently below.

download the source from Bionic's repo [https://launchpad.net/ubuntu/+source/openssl](https://launchpad.net/ubuntu/+source/openssl)
click the triangle next to              1.1.0g-2ubuntu2 under Bionic Beaver and grab the tar ball openssl_1.1.0g.orig.tar.gz

extract it somewhere, say in Downloads
then
```

cd Downloads/openssl-1.1.0g
./config --prefix=$HOME/openssl --openssldir=$HOME/openssl
make
make test
make install
```

(note that it is ./config, not ./configure)

You can check that libcrypto.so.1.1 is in ~/openssl/lib. If you get errors it is probably because you are missing some dependencies, the output would tell you what they are, install them from repo (usually the -dev files)
 
Now for makemkv to find your new libcrypto, edit its .desktop file and change the EXEC line to
> EXEC = env LD_LIBRARY_PATH=/home/your-user-name/openssl/lib:$LD_LIBRARY_PATH makemkv
also comment out the Try Exec line if there is one (put a # in front or just edit it away)

To start makemkv in the terminal
```
export LD_LIBRARY_PATH=/home/your-user-name/openssl/lib:$LD_LIBRARY_PATH

makemkv

```
[B]
Edited: [/B]From mc4man's post below it looks like there is something fishy about your system. I don't have makemkv myself (I don't even have a DVD drive) I am just answering your question about how to get libcrypto 1.1 and get makemkv to find it.

---

### Post by mc4man on 2018-03-10
Don't see that problem here on 16.04, opens fine..
```
makemkv-oss-1.12.0$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking for gawk... gawk
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for -objcopy... no
checking for objcopy... objcopy
checking for -ld... /usr/bin/ld -m elf_x86_64
checking for a BSD-compatible install... /usr/bin/install -c
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for compress2 in -lz... yes
checking openssl/opensslconf.h usability... yes
checking openssl/opensslconf.h presence... yes
checking for openssl/opensslconf.h... yes
checking for AES_encrypt in -lcrypto... yes
checking expat.h usability... yes
checking expat.h presence... yes
checking for expat.h... yes
checking for XML_ParserCreate in -lexpat... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ffmpeg... yes
[COLOR="#0000FF"]checking whether LIBAVCODEC_VERSION_MAJOR is declared... yes
checking LIBAVCODEC_VERSION_MAJOR... 57[/COLOR]
checking for AVFrame.nb_samples... yes
checking whether AV_SAMPLE_FMT_U8P is declared... yes
checking for avcodec_encode_audio2... yes
checking for AVCodecContext.refcounted_frames... yes
checking whether avcodec_free_frame is declared... no
checking whether av_frame_free is declared... yes
checking for av_log_format_line... yes
checking for enum AVCodecID... yes
checking whether AV_CODEC_ID_NONE is declared... yes
checking whether av_frame_get_channels is declared... yes
checking whether av_frame_get_sample_rate is declared... yes
checking whether av_frame_set_channel_layout is declared... yes
checking for AVCodecParserContext.duration... yes
checking whether AV_CH_TOP_BACK_CENTER is declared... yes
checking for qt5... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libffabi/src/ffabicfg.h
config.status: executing libtool commands
```

```
$ ldd /usr/bin/makemkvcon
	linux-vdso.so.1 =>  (0x00007ffdeede5000)
	libmakemkv.so.1 => /usr/lib/libmakemkv.so.1 (0x00007f9d78e89000)
	libdriveio.so.0 => /usr/lib/libdriveio.so.0 (0x00007f9d78c82000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f9d78a65000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f9d7869b000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f9d78497000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f9d78115000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f9d77f0d000)
	[COLOR="#0000CD"]libcrypto.so.1.0.0 => /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 (0x00007f9d77ac9000)[/COLOR]
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f9d778af000)
	libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f9d77686000)
	[COLOR="#0000FF"]libavcodec.so.57 => /usr/lib/x86_64-linux-gnu/libavcodec.so.57 (0x00007f9d75f69000)
	libavutil.so.55 => /usr/lib/x86_64-linux-gnu/libavutil.so.55 (0x00007f9d75cdf000)[/COLOR]
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f9d759d6000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f9d757c0000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f9d79150000)
	libswresample.so.2 => /usr/lib/x86_64-linux-gnu/libswresample.so.2 (0x00007f9d755a1000)
	libwebp.so.5 => /usr/lib/x86_64-linux-gnu/libwebp.so.5 (0x00007f9d75345000)
	libcrystalhd.so.3 => /usr/lib/x86_64-linux-gnu/libcrystalhd.so.3 (0x00007f9d7512a000)
	libva.so.1 => /usr/lib/x86_64-linux-gnu/libva.so.1 (0x00007f9d74f0a000)
	libzvbi.so.0 => /usr/lib/x86_64-linux-gnu/libzvbi.so.0 (0x00007f9d74c7f000)
	libxvidcore.so.4 => /usr/lib/x86_64-linux-gnu/libxvidcore.so.4 (0x00007f9d7496b000)
	libx265.so.146 => /usr/lib/x86_64-linux-gnu/libx265.so.146 (0x00007f9d73ce3000)
	libx264.so.152 => /usr/lib/x86_64-linux-gnu/libx264.so.152 (0x00007f9d7393a000)
	libwavpack.so.1 => /usr/lib/x86_64-linux-gnu/libwavpack.so.1 (0x00007f9d73711000)
	libvpx.so.3 => /usr/lib/x86_64-linux-gnu/libvpx.so.3 (0x00007f9d732ed000)
	libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f9d73044000)
	libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f9d72e18000)
	libtwolame.so.0 => /usr/lib/x86_64-linux-gnu/libtwolame.so.0 (0x00007f9d72bf5000)
	libtheoraenc.so.1 => /usr/lib/x86_64-linux-gnu/libtheoraenc.so.1 (0x00007f9d729b6000)
	libtheoradec.so.1 => /usr/lib/x86_64-linux-gnu/libtheoradec.so.1 (0x00007f9d7279c000)
	libspeex.so.1 => /usr/lib/x86_64-linux-gnu/libspeex.so.1 (0x00007f9d72583000)
	libsnappy.so.1 => /usr/lib/x86_64-linux-gnu/libsnappy.so.1 (0x00007f9d7237b000)
	libshine.so.3 => /usr/lib/x86_64-linux-gnu/libshine.so.3 (0x00007f9d7216e000)
	libopus.so.0 => /usr/lib/x86_64-linux-gnu/libopus.so.0 (0x00007f9d71f24000)
	libopenjp2.so.7 => /usr/lib/x86_64-linux-gnu/libopenjp2.so.7 (0x00007f9d71ced000)
	libmp3lame.so.0 => /usr/lib/x86_64-linux-gnu/libmp3lame.so.0 (0x00007f9d71a78000)
	libgsm.so.1 => /usr/lib/x86_64-linux-gnu/libgsm.so.1 (0x00007f9d7186a000)
	libfdk-aac.so.1 => /usr/lib/x86_64-linux-gnu/libfdk-aac.so.1 (0x00007f9d715b1000)
	liblzma.so.5 => /lib/x86_64-linux-gnu/liblzma.so.5 (0x00007f9d7138f000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f9d71055000)
	libvdpau.so.1 => /usr/lib/x86_64-linux-gnu/libvdpau.so.1 (0x00007f9d70e51000)
	libva-x11.so.1 => /usr/lib/x86_64-linux-gnu/libva-x11.so.1 (0x00007f9d70c4b000)
	libva-drm.so.1 => /usr/lib/x86_64-linux-gnu/libva-drm.so.1 (0x00007f9d70a48000)
	libsoxr.so.0 => /usr/lib/x86_64-linux-gnu/libsoxr.so.0 (0x00007f9d707e3000)
	libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007f9d705be000)
	libnuma.so.1 => /usr/lib/x86_64-linux-gnu/libnuma.so.1 (0x00007f9d703b3000)
	libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f9d701aa000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f9d6ff88000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f9d6fd76000)
	libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007f9d6fb70000)
	libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007f9d6f95e000)
	libgomp.so.1 => /usr/lib/x86_64-linux-gnu/libgomp.so.1 (0x00007f9d6f73c000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f9d6f538000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f9d6f332000)
```

If you look in your configure it found " LIBAVCODEC_VERSION_MAJOR... 56" but your ldd shows looking for 

libavcodec.so.57 => not found
libavutil.so.55 => not found 
Did you build this all on the machine you're trying to run on?

Note that on a stock 16.04 the libavcodec ver. should be 56 & libavutil 54

---

### Post by mc4man on 2018-03-10
Also ck. 
```
ldd /usr/lib/libmakemkv.so.1
```

post if need be 
```
locate libavcodec-ffmpeg.so.56 libavcodec.so.57
```
```
apt-cache policy libavcodec-dev
```

---

### Post by VMC on 2018-03-10
mc4man, I'm on bionic right now, but yes I installed makemkv from 16.04.4. Strange that from the earlier version, I didn't have to do anything. Then again, I installed makemkv from much earlier versions and kept upgrading. 

As far as using the deb file. After it failed I backed out of it.

I'll check again on my output when I fire up 16.04.4 again.

Thanks for the replies!

PS: I see that xenial has a newer ISO:
[B]"xenial-desktop-amd64.iso 2018-03-11 01:25 1.2G"
[/B]I might install that and see if I can install makemkv from the start.

---

### Post by mc4man on 2018-03-11
Make sure you always use (extract) a fresh set of the archived makemkv files, don't re-use from another install.
If possible you may want to remove existing borked install, see end note..

It's possible makemkv may have an issue when the shared ffmpeg libs have a suffix like is used in 16.04, i.e in 16.04 it's libavcodec-ffmpeg.so.56, not libavcodec.so.56 
If still an issue after redoing from freshly extracted files you could - 
1. There are instructions on the makemkv site to build ffmpeg to /tmp & statically link
2. You could use this ppa which will provide a shared ffmpeg that provides libavcodec.so.57, ect. However then remember anything else built off of the newer  libavcodec-dev , ect. will also use the newer libs..
(- while different major version ffmpeg libs can co-exist there can only be 1 set of -dev packages installed at a time..
[https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media](https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media)

Re; how makemkv installs
Unfortunately the dev does not include a make uninstall routine. This makes removing makemkv a bit of a hassle, especially when installed to /usr (the default
You have posted logs of your install(s) so may be a bit easier to find & remove..

If doing for 1st time on an install I'd consider configuring the oss build to install to /usr/local, makes finding the files easy if wishing to remove. Just go - 
./configure --prefix=/usr/local

---

### Post by VMC on 2018-03-11
OK, I just installed the very latest xenial ISO. It also failed the same way.  
Also I have the *makemkv* 'deb' files compressed, and I use those on a fresh install. Your right about purging *makemkv*. For that reason, I first use *fsarchiver* to save xenial just before I install makemkv.

You might be onto something regarding ffmpeg. As I recall, that was compiled somehow in the beginning of the first xenial. Artful, may have been the same way. Bionic, once I realized it didn't need to compile anything, it work perfectly. Newer packages, most likely.

I'll try your ppa you listed.

Thanks!

edit: I just installed *ffmpeg* from your ppa *makemkv* still fails.

---

### Post by VMC on 2018-03-11
I just re-installed the older xenial. One which makemkv works. Interesting it uses 'libcrypto.1.0', which works. For some reason, the updated xenial with makemkv requires 'libcrypto.1.1':
```
$ ldd $(which makemkvcon)
    linux-vdso.so.1 =>  (0x00007ffd39f6f000)
    libmakemkv.so.1 => /usr/lib/libmakemkv.so.1 (0x00007fac3ec71000)
    libdriveio.so.0 => /usr/lib/libdriveio.so.0 (0x00007fac3ea6a000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fac3e84d000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fac3e483000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fac3e27f000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fac3defd000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fac3dcf5000)
    [COLOR=#0000ff]libcrypto.so.1.0.0 [/COLOR]=> /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 (0x00007fac3d8b1000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fac3d697000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fac3d46e000)
    libavcodec-ffmpeg.so.56 => /usr/lib/x86_64-linux-gnu/libavcodec-ffmpeg.so.56 (0x00007fac3c042000)
    libavutil-ffmpeg.so.54 => /usr/lib/x86_64-linux-gnu/libavutil-ffmpeg.so.54 (0x00007fac3bdd3000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fac3baca000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fac3b8b4000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fac3ef2b000)
    libswresample-ffmpeg.so.1 => /usr/lib/x86_64-linux-gnu/libswresample-ffmpeg.so.1 (0x00007fac3b697000)
    libva.so.1 => /usr/lib/x86_64-linux-gnu/libva.so.1 (0x00007fac3b47b000)
    libzvbi.so.0 => /usr/lib/x86_64-linux-gnu/libzvbi.so.0 (0x00007fac3b1f0000)
    libxvidcore.so.4 => /usr/lib/x86_64-linux-gnu/libxvidcore.so.4 (0x00007fac3aedc000)
    libx265.so.79 => /usr/lib/x86_64-linux-gnu/libx265.so.79 (0x00007fac3a2bd000)
    libx264.so.148 => /usr/lib/x86_64-linux-gnu/libx264.so.148 (0x00007fac39f19000)
    libwebp.so.5 => /usr/lib/x86_64-linux-gnu/libwebp.so.5 (0x00007fac39cbd000)
    libwavpack.so.1 => /usr/lib/x86_64-linux-gnu/libwavpack.so.1 (0x00007fac39a94000)
    libvpx.so.3 => /usr/lib/x86_64-linux-gnu/libvpx.so.3 (0x00007fac39670000)
    libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007fac393c7000)
    libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007fac3919b000)
    libtwolame.so.0 => /usr/lib/x86_64-linux-gnu/libtwolame.so.0 (0x00007fac38f78000)
    libtheoraenc.so.1 => /usr/lib/x86_64-linux-gnu/libtheoraenc.so.1 (0x00007fac38d39000)
    libtheoradec.so.1 => /usr/lib/x86_64-linux-gnu/libtheoradec.so.1 (0x00007fac38b1f000)
    libspeex.so.1 => /usr/lib/x86_64-linux-gnu/libspeex.so.1 (0x00007fac38906000)
    libsnappy.so.1 => /usr/lib/x86_64-linux-gnu/libsnappy.so.1 (0x00007fac386fe000)
    libshine.so.3 => /usr/lib/x86_64-linux-gnu/libshine.so.3 (0x00007fac384f1000)
    libschroedinger-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libschroedinger-1.0.so.0 (0x00007fac3821c000)
    libopus.so.0 => /usr/lib/x86_64-linux-gnu/libopus.so.0 (0x00007fac37fd2000)
    libopenjpeg.so.5 => /usr/lib/x86_64-linux-gnu/libopenjpeg.so.5 (0x00007fac37daf000)
    libmp3lame.so.0 => /usr/lib/x86_64-linux-gnu/libmp3lame.so.0 (0x00007fac37b3a000)
    libgsm.so.1 => /usr/lib/x86_64-linux-gnu/libgsm.so.1 (0x00007fac3792c000)
    libcrystalhd.so.3 => /usr/lib/x86_64-linux-gnu/libcrystalhd.so.3 (0x00007fac37711000)
    liblzma.so.5 => /lib/x86_64-linux-gnu/liblzma.so.5 (0x00007fac374ef000)
    libsoxr.so.0 => /usr/lib/x86_64-linux-gnu/libsoxr.so.0 (0x00007fac3728a000)
    libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007fac37065000)
    libnuma.so.1 => /usr/lib/x86_64-linux-gnu/libnuma.so.1 (0x00007fac36e5a000)
    libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007fac36c51000)
    liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007fac369d1000)
    libgomp.so.1 => /usr/lib/x86_64-linux-gnu/libgomp.so.1 (0x00007fac367af000)
```

---

### Post by mc4man on 2018-03-11
> **VMC said:**
> I just re-installed the older xenial. One which makemkv works. Interesting it uses 'libcrypto.1.0', which works. For some reason, the updated xenial with makemkv requires 'libcrypto.1.1':

makemkvcon 'inherits ldd's' from whatever libmakemkv it finds. So on your previous "updated xenial" you somehow had a libmakemkv that was configured in the presence of  libcrypto.1.1

---

### Post by VMC on 2018-03-11
Not sure now how I can get [COLOR=#000000]libcrypto.1.1  [/COLOR]  on my xenials.

[COLOR=#000000][/COLOR]I tried to install the newest makemkv 12.0 on the older xenial. It failed also. Then I upgraded that xenail to current levels. Over 500mb later, it too failed. 
Something witht the newer makemkv wont work with xenial. libcrypto is the culprit.

---

### Post by monkeybrain20122 on 2018-03-11
> **VMC said:**
> Not sure now how I can get [COLOR=#000000]libcrypto.1.1  [/COLOR]  on my xenials.

.

I wrote a long post to tell you exactly, step by step how. ;)

---

### Post by mc4man on 2018-03-11
Not sure what either of you is doing to create this but  makemkv 12.0  absolutely does not require libcrypto.so.1.1, it uses whatever version you have.
I'm sure monkeybrain20122's solution will work but it should not be needed.

If you want to explore - 
On any 16.04 install
If ever installed remove makemkv completely, assuming installed to /usr this should do
```
sudo rm /usr/lib/libdriveio.so.0 /usr/lib/libmakemkv.so.1 /usr/lib/libmmbd.so.0 /usr/bin/makemkv /usr/share/applications/makemkv.desktop /usr/share/icons/hicolor/16x16/apps/makemkv.png /usr/share/icons/hicolor/22x22/apps/makemkv.png /usr/share/icons/hicolor/32x32/apps/makemkv.png  /usr/share/icons/hicolor/128x128/apps/makemkv.png /usr/bin/makemkvcon /usr/bin/mmdtsdec /usr/share/MakeMKV/*
```
Then extract both makemkv archives.

To check that there isn't an errant libmakemkv.so.1 run a lld on  makemkv-bin-1.12.0/bin/amd64/makemkvcon 
It should return a minimal result as such
```
$ ldd   /home/doug/Desktop/mkmkv/makemkv-bin-1.12.0/bin/amd64/makemkvcon
	linux-vdso.so.1 =>  (0x00007fffdd6d8000)
	libmakemkv.so.1 => not found
	libdriveio.so.0 => not found
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007ff1ed95b000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007ff1ed591000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007ff1ed38d000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007ff1ed00b000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007ff1ece03000)
	/lib64/ld-linux-x86-64.so.2 (0x00007ff1edb78000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007ff1ecafa000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007ff1ec8e4000)
```
If it's any bigger like you see after compiling & installing makemkv-oss then there is a libmakemkv.so.1 somewhere that needs to be removed
(- don't trust locate.. should be shown in the ldd

If it is like above then go ahead & build/install makemkv-oss, then make & install makemkv-bin

---

### Post by VMC on 2018-03-11
> **mc4man said:**
> Not sure what either of you is doing to create this but  makemkv 12.0  absolutely does not require libcrypto.so.1.1, it uses whatever version you have.
...

If it is like above then go ahead & build/install makemkv-oss, then make & install makemkv-bin
On post#7, I stated that I installed a new xenial. No makemkv at all. 
I updated system first, then:

"***sudo apt-get install build-essential pkg-config libc6-dev libssl-dev libexpat1-dev libavcodec-dev libgl1-mesa-dev libqt4-dev zlib1g-dev***"

Then I created the two required folders, "*makemkv-bin-1.12.0*" and "*makemkv-oss-1.12.0*"

At that point, entering into 'oss' folder, from a terminal I did this:
***./configure***
[I][B]make
sudo make install[/B][/I]

Then entering 'bin' folder, I did this from a terminal:
***make***
[I][B]sudo make install

[/B][/I]These instructions I followed from makemkv page page.


After that it failed "ibcrypto.so.1.1", but I think your right, it uses the  libcrypto available, and I was following a 'red-herring'.

From a fresh install of xenial makemkv wouldn't even be there.

---

### Post by VMC on 2018-03-11
It works!
Here is the out put of the oss folder. Notice the compilation process. Its below "blue" make. That never happened before when it failed.

```
$ lsautoxxx    libdriveio  libmakemkv   License.txt      makemkvgui
configure  libebml     libmatroska  makefile.common  msvc
libabi     libffabi    libmmbd      Makefile.in      sstring
$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking for gawk... gawk
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for -objcopy... no
checking for objcopy... objcopy
checking for -ld... /usr/bin/ld -m elf_x86_64
checking for a BSD-compatible install... /usr/bin/install -c
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for compress2 in -lz... yes
checking openssl/opensslconf.h usability... yes
checking openssl/opensslconf.h presence... yes
checking for openssl/opensslconf.h... yes
checking for AES_encrypt in -lcrypto... yes
checking expat.h usability... yes
checking expat.h presence... yes
checking for expat.h... yes
checking for XML_ParserCreate in -lexpat... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ffmpeg... yes
checking whether LIBAVCODEC_VERSION_MAJOR is declared... yes
checking LIBAVCODEC_VERSION_MAJOR... 56
checking for AVFrame.nb_samples... yes
checking whether AV_SAMPLE_FMT_U8P is declared... yes
checking for avcodec_encode_audio2... yes
checking for AVCodecContext.refcounted_frames... yes
checking whether avcodec_free_frame is declared... yes
checking whether av_frame_free is declared... yes
checking for av_log_format_line... yes
checking for enum AVCodecID... yes
checking whether AV_CODEC_ID_NONE is declared... yes
checking whether av_frame_get_channels is declared... yes
checking whether av_frame_get_sample_rate is declared... yes
checking whether av_frame_set_channel_layout is declared... yes
checking for AVCodecParserContext.duration... yes
checking whether AV_CH_TOP_BACK_CENTER is declared... yes
checking for qt5... no
checking for qt4... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libffabi/src/ffabicfg.h
config.status: executing libtool commands
**[COLOR=#0000ff]$ make[/COLOR]**
mkdir -p out
gcc -g -O2 -D_linux_  -D_REENTRANT -shared -Wl,-z,defs -oout/libdriveio.so.0.full -I./libdriveio/inc libdriveio/src/infolist.cpp libdriveio/src/scsihlp.cpp libdriveio/src/srlist.cpp libdriveio/src/stdquery.cpp libdriveio/src/tipclient.cpp libdriveio/src/tipcommon.cpp libdriveio/src/tipserver.cpp libdriveio/src/drives/pioneer.cpp libdriveio/src/drives/xboxhddvd.cpp \
-fPIC -Xlinker -dy -Xlinker --version-script=libdriveio/src/libdriveio.vers \
-Xlinker -soname=libdriveio.so.0 -lc -lstdc++
objcopy --strip-all --strip-debug --strip-unneeded --discard-all out/libdriveio.so.0.full out/libdriveio.so.0
mkdir -p tmp
echo "#define BUILDINFO_ARCH_NAME \"x86_64-linux-gnu\"" >> tmp/gen_buildinfo.h
echo "#define BUILDINFO_BUILD_DATE \"Sun Mar 11 17:02:00 PDT 2018\"" >> tmp/gen_buildinfo.h
mkdir -p out
gcc -g -O2 -D_linux_   -D_GNU_SOURCE -D_REENTRANT -shared -Wl,-z,defs -oout/libmakemkv.so.1.full -I./libebml/inc -DEBML_NO_READ -DEBML_STRICT_API -DEBML_DEBUG \
-I./libmatroska/inc -I./libmakemkv/inc -I./sstring/inc -I./makemkvgui/inc -I./libabi/inc \
-I./libffabi/inc -DDCA_LOG -DDCA_FFMALLOC libebml/src/EbmlBinary.cpp libebml/src/EbmlContexts.cpp libebml/src/EbmlCrc32.cpp libebml/src/EbmlDate.cpp libebml/src/EbmlDummy.cpp libebml/src/EbmlElement.cpp libebml/src/EbmlFloat.cpp libebml/src/EbmlHead.cpp libebml/src/EbmlMaster.cpp libebml/src/EbmlSInteger.cpp libebml/src/EbmlString.cpp libebml/src/EbmlSubHead.cpp libebml/src/EbmlUInteger.cpp libebml/src/EbmlUnicodeString.cpp libebml/src/EbmlVersion.cpp libebml/src/EbmlVoid.cpp libebml/src/IOCallback.cpp libebml/src/MemIOCallback.cpp  libmatroska/src/FileKax.cpp libmatroska/src/KaxAttached.cpp libmatroska/src/KaxAttachments.cpp libmatroska/src/KaxBlock.cpp libmatroska/src/KaxBlockData.cpp libmatroska/src/KaxCluster.cpp libmatroska/src/KaxContexts.cpp libmatroska/src/KaxCues.cpp libmatroska/src/KaxCuesData.cpp libmatroska/src/KaxInfoData.cpp libmatroska/src/KaxSeekHead.cpp libmatroska/src/KaxSegment.cpp libmatroska/src/KaxTracks.cpp libmatroska/src/KaxVersion.cpp libmatroska/src/KaxSemantic.cpp libmakemkv/src/ebmlwrite.cpp libmakemkv/src/libmkv.cpp libmakemkv/src/version.cpp libmakemkv/src/world.cpp libmakemkv/src/stdstring.cpp  sstring/src/sstring.cpp \
libabi/src/ossl_aes.c libabi/src/ossl_sha.c libabi/src/ossl_ec.c libabi/src/zlib.c libabi/src/xpat.c libabi/src/libm.c libabi/src/httplinux.cpp makemkvgui/src/api_linux.cpp libabi/src/sys_linux.c makemkvgui/src/spawn_posix.cpp libffabi/src/ffabi.c libffabi/src/mlp.c libffabi/src/log.c libffabi/src/audio_convert.c libffabi/src/audio_mix.c libffabi/src/audio_mix_matrix.c libffabi/src/dcadec/bitstream.cpp libffabi/src/dcadec/core_decoder.cpp libffabi/src/dcadec/dca_context.cpp libffabi/src/dcadec/dmix_tables.cpp libffabi/src/dcadec/exss_parser.cpp libffabi/src/dcadec/idct_fixed.cpp libffabi/src/dcadec/interpolator.cpp libffabi/src/dcadec/interpolator_fixed.cpp libffabi/src/dcadec/interpolator_float.cpp libffabi/src/dcadec/ta.cpp libffabi/src/dcadec/xll_decoder.cpp libffabi/src/dcadec/idct_float.cpp \
-DHAVE_BUILDINFO_H -Itmp -I/usr/include/x86_64-linux-gnu \
-fPIC -Xlinker -dy -Xlinker --version-script=libmakemkv/src/libmakemkv.vers \
-Xlinker -soname=libmakemkv.so.1 -lc -lstdc++ -lcrypto -lz -lexpat -lavcodec-ffmpeg -lavutil-ffmpeg -lrt -lm -lrt
objcopy --strip-all --strip-debug --strip-unneeded --discard-all out/libmakemkv.so.1.full out/libmakemkv.so.1
mkdir -p tmp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -o tmp/moc_mainwnd.cpp makemkvgui/src/mainwnd.h
mkdir -p tmp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -o tmp/moc_logtext.cpp makemkvgui/src/logtext.h
mkdir -p tmp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -o tmp/moc_dirselectbox.cpp makemkvgui/src/dirselectbox.h
mkdir -p tmp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -o tmp/moc_aboutbox.cpp makemkvgui/src/aboutbox.h
mkdir -p tmp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -o tmp/moc_settingdlg.cpp makemkvgui/src/settingdlg.h
mkdir -p tmp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -o tmp/moc_backupdlg.cpp makemkvgui/src/backupdlg.h
mkdir -p tmp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -o tmp/moc_lineeditk.cpp makemkvgui/src/lineeditk.h
mkdir -p tmp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -o tmp/moc_dvdbox.cpp makemkvgui/src/dvdbox.h
mkdir -p tmp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -o tmp/moc_drivebox.cpp makemkvgui/src/drivebox.h
mkdir -p tmp
/usr/bin/ld -m elf_x86_64 -r -b binary -z noexecstack -o tmp/image_data.o makemkvgui/bin/image_data.bin
mkdir -p out
g++ -std=c++11 -g -O2 -D_linux_   -oout/makemkv.full -I./makemkvgui/inc -I./libmakemkv/inc -I./sstring/inc \
-I./libdriveio/inc -I./libabi/inc makemkvgui/src/aboutbox.cpp makemkvgui/src/client.cpp makemkvgui/src/dirselectbox.cpp makemkvgui/src/logic.cpp makemkvgui/src/logtext.cpp makemkvgui/src/main.cpp makemkvgui/src/nativefiledialog.cpp makemkvgui/src/mainwnd.cpp makemkvgui/src/marshall.cpp makemkvgui/src/progress.cpp makemkvgui/src/scsiinfo.cpp makemkvgui/src/settingdlg.cpp makemkvgui/src/uisync.cpp makemkvgui/src/viteminfo.cpp makemkvgui/src/margui.cpp makemkvgui/src/backupdlg.cpp makemkvgui/src/lstring.cpp makemkvgui/src/notify.cpp makemkvgui/src/str/en_utf16.cpp makemkvgui/src/image.cpp makemkvgui/src/abutton.cpp makemkvgui/src/lineeditk.cpp makemkvgui/src/dvdbox.cpp makemkvgui/src/drivebox.cpp makemkvgui/src/api_posix.cpp makemkvgui/src/api_linux.cpp makemkvgui/src/sem_posix.cpp makemkvgui/src/spawn_posix.cpp makemkvgui/src/logic_posix.cpp makemkvgui/src/notify_linux.cpp makemkvgui/src/image_linux.cpp tmp/image_data.o tmp/moc_mainwnd.cpp tmp/moc_logtext.cpp tmp/moc_dirselectbox.cpp tmp/moc_aboutbox.cpp tmp/moc_settingdlg.cpp tmp/moc_backupdlg.cpp tmp/moc_lineeditk.cpp tmp/moc_dvdbox.cpp tmp/moc_drivebox.cpp \
sstring/src/sstring.cpp libdriveio/src/srlist.cpp \
-DHAVE_BUILDINFO_H -Itmp \
-DQT_SHARED -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I/usr/include/qt4/QtDBus -I/usr/include/qt4 -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I/usr/include/qt4/QtCore -lc -lstdc++ \
-lQtGui -lQtDBus -lQtXml -lQtCore -lpthread -lz -lrt
objcopy --strip-all --strip-debug --strip-unneeded --discard-all out/makemkv.full out/makemkv
mkdir -p out
gcc -g -O2 -D_linux_  -D_REENTRANT -shared -Wl,-z,defs -oout/libmmbd.so.0.full -I./makemkvgui/inc -I./libmmbd/inc \
-I./libmakemkv/inc -I./sstring/inc -I./libabi/inc makemkvgui/src/client.cpp makemkvgui/src/marshall.cpp libmmbd/src/marmmbd.cpp libmmbd/src/nstring.cpp libmmbd/src/mmbd.cpp libmmbd/src/mmconn.cpp libmmbd/src/mmbdipc.cpp libmmbd/src/utf8.cpp libmmbd/src/aacs.cpp libmmbd/src/bdplus.cpp libmmbd/src/crypto_ossl.cpp makemkvgui/src/api_posix.cpp makemkvgui/src/api_linux.cpp makemkvgui/src/sem_posix.cpp makemkvgui/src/spawn_posix.cpp sstring/src/sstring.cpp \
-fPIC -Xlinker -dy -Xlinker --version-script=libmmbd/src/libmmbd.vers \
-Xlinker -soname=libmmbd.so.0 -lc -lstdc++ -lrt -lpthread -lcrypto
objcopy --strip-all --strip-debug --strip-unneeded --discard-all out/libmmbd.so.0.full out/libmmbd.so.0
type "sudo make install" to install
$ sudo make install
[sudo] password for vmc: 
/usr/bin/install -c -D -m 644 out/libdriveio.so.0 /usr/lib/libdriveio.so.0
/usr/bin/install -c -D -m 644 out/libmakemkv.so.1 /usr/lib/libmakemkv.so.1
/usr/bin/install -c -D -m 644 out/libmmbd.so.0 /usr/lib/libmmbd.so.0
ldconfig
/usr/bin/install -c -D -m 755 out/makemkv /usr/bin/makemkv
/usr/bin/install -c -D -m 644 makemkvgui/share/makemkv.desktop /usr/share/applications/makemkv.desktop
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/16x16/makemkv.png /usr/share/icons/hicolor/16x16/apps/makemkv.png
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/22x22/makemkv.png /usr/share/icons/hicolor/22x22/apps/makemkv.png
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/32x32/makemkv.png /usr/share/icons/hicolor/32x32/apps/makemkv.png
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/64x64/makemkv.png /usr/share/icons/hicolor/64x64/apps/makemkv.png
/usr/bin/install -c -D -m 644 makemkvgui/share/icons/128x128/makemkv.png /usr/share/icons/hicolor/128x128/apps/makemkv.png
$ 
```

---

### Post by VMC on 2018-03-11
OMG! I think I may have found the problem. the X??? folder was the ones I have been using. I decided to re-download again. Here's the results of a compare:
> $ diff --brief -r makemkv-oss-1.12.0 Xmakemkv-oss-1.12.0Files makemkv-oss-1.12.0/config.log and Xmakemkv-oss-1.12.0/config.log differ
Files makemkv-oss-1.12.0/config.status and Xmakemkv-oss-1.12.0/config.status differ
Files makemkv-oss-1.12.0/libffabi/src/ffabicfg.h and Xmakemkv-oss-1.12.0/libffabi/src/ffabicfg.h differ
Files makemkv-oss-1.12.0/libtool and Xmakemkv-oss-1.12.0/libtool differ
Files makemkv-oss-1.12.0/Makefile and Xmakemkv-oss-1.12.0/Makefile differ
Files makemkv-oss-1.12.0/out/libdriveio.so.0 and Xmakemkv-oss-1.12.0/out/libdriveio.so.0 differ
Files makemkv-oss-1.12.0/out/libdriveio.so.0.full and Xmakemkv-oss-1.12.0/out/libdriveio.so.0.full differ
Files makemkv-oss-1.12.0/out/libmakemkv.so.1 and Xmakemkv-oss-1.12.0/out/libmakemkv.so.1 differ
Files makemkv-oss-1.12.0/out/libmakemkv.so.1.full and Xmakemkv-oss-1.12.0/out/libmakemkv.so.1.full differ
Files makemkv-oss-1.12.0/out/libmmbd.so.0 and Xmakemkv-oss-1.12.0/out/libmmbd.so.0 differ
Files makemkv-oss-1.12.0/out/libmmbd.so.0.full and Xmakemkv-oss-1.12.0/out/libmmbd.so.0.full differ
Files makemkv-oss-1.12.0/out/makemkv and Xmakemkv-oss-1.12.0/out/makemkv differ
Files makemkv-oss-1.12.0/out/makemkv.full and Xmakemkv-oss-1.12.0/out/makemkv.full differ
Files makemkv-oss-1.12.0/tmp/gen_buildinfo.h and Xmakemkv-oss-1.12.0/tmp/gen_buildinfo.h differ
Files makemkv-oss-1.12.0/tmp/image_data.o and Xmakemkv-oss-1.12.0/tmp/image_data.o differ
Do you think that was the issue all along?

This has been a **Exercise in futility!**

---

### Post by mc4man on 2018-03-11
> **VMC said:**
> OMG! I think I may have found the problem. the X??? folder was the ones I have been using. I decided to re-download again. Here's the results of a compare:

Do you think that was the issue all along?

This has been a **Exercise in futility!**
Yes - as I mentioned you should get _new archives_ from the site or archived, never re-use. The oss one never gets cleaned after configure/build so if done elsewhere it keeps previous linker info
(- maybe I wasn't exactly clear with "from freshly extracted files" ..

For curiosity installed xubuntu 16.04.4, there was no issue...

---

### Post by mc4man on 2018-03-11
After doing the configure, make, make install & make,  make install  the best thing to do is delete the 2 extracted folders you installed from.
They are useless for an uninstall & obviously could cause issue if  re-used in a changed env or with newer libs.
You can keep the orig. downloaded  .tar.gz's as they are untouched..

---

### Post by VMC on 2018-03-11
I thought the compressed files were in fact "clean". But at some point I must have compressed them again after an install, not realizing 'oss' was already used.

Thanks for all the replies. It help me a lot.

---

