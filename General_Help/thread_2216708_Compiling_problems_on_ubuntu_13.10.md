---
title: "Compiling problems on ubuntu 13.10"
date: 2014-04-13
forum: General Help
---

### Post by Chelidze on 2014-04-13
So I am trying to compile Ffmpeg with using this guide
[https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)


every thing up to actually compiling ffmpeg works 


so this is what I get


```
levan@SMS:~/ffmpeg_sources/ffmpeg/ffmpeg$ PKG_CONFIG_PATH="$HOME/ffmpeg_build/lib/pkgconfig"
levan@SMS:~/ffmpeg_sources/ffmpeg/ffmpeg$ export PKG_CONFIG_PATH
levan@SMS:~/ffmpeg_sources/ffmpeg/ffmpeg$ ./configure --prefix="$HOME/ffmpeg_build" --extra-cflags="-I$HOME/ffmpeg_build/include" \
>    --extra-ldflags="-L$HOME/ffmpeg_build/lib" --bindir="$HOME/bin" --extra-libs="-ldl" --enable-gpl \
>    --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus \
>    --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
ERROR: libfdk_aac not found


If you think configure made a mistake, make sure you are using the latest
version from Git.  If the latest version fails, report the problem to the
ffmpeg-user@ffmpeg.org mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.log" produced by configure as this will help
solving the problem.
levan@SMS:~/ffmpeg_sources/ffmpeg/ffmpeg$ make
Makefile:2: config.mak: No such file or directory
Makefile:54: /common.mak: No such file or directory
Makefile:94: /libavutil/Makefile: No such file or directory
Makefile:94: /library.mak: No such file or directory
Makefile:96: /doc/Makefile: No such file or directory
Makefile:179: /tests/Makefile: No such file or directory
make: *** No rule to make target `/tests/Makefile'.  Stop.
levan@SMS:~/ffmpeg_sources/ffmpeg/ffmpeg$ make install
Makefile:2: config.mak: No such file or directory
Makefile:54: /common.mak: No such file or directory
Makefile:94: /libavutil/Makefile: No such file or directory
Makefile:94: /library.mak: No such file or directory
Makefile:96: /doc/Makefile: No such file or directory
Makefile:179: /tests/Makefile: No such file or directory
make: *** No rule to make target `/tests/Makefile'.  Stop.
levan@SMS:~/ffmpeg_sources/ffmpeg/ffmpeg$ make distclean
Makefile:2: config.mak: No such file or directory
Makefile:54: /common.mak: No such file or directory
Makefile:94: /libavutil/Makefile: No such file or directory
Makefile:94: /library.mak: No such file or directory
Makefile:96: /doc/Makefile: No such file or directory
Makefile:179: /tests/Makefile: No such file or directory
make: *** No rule to make target `/tests/Makefile'.  Stop.
levan@SMS:~/ffmpeg_sources/ffmpeg/ffmpeg$ hash -r

```


Thank you for your time

---

### Post by mc4man on 2014-04-13
> levan@SMS:~/ffmpeg_sources/ffmpeg/ffmpeg$ ./configure --prefix="$HOME/ffmpeg_build" --extra-cflags="-I$HOME/ffmpeg_build/include" \
>    --extra-ldflags="-L$HOME/ffmpeg_build/lib" --bindir="$HOME/bin" --extra-libs="-ldl" --enable-gpl \
>    --enable-libass [COLOR="#FF0000"]--enable-libfdk-aac[/COLOR] --enable-libfreetype --enable-libmp3lame --enable-libopus \
>    --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
[COLOR="#FF0000"]ERROR: libfdk_aac not found[/COLOR]

You have --enable-libfdk-aac in the configure but either didn't install libfdk-aac-dev from saucy repos or do the "**libfdk-aac**" section from linked guide
(the repo version is ok, the guide gets you the latest version of  fdk-aac which would be better way to go.

---

### Post by Chelidze on 2014-04-13
> **mc4man said:**
> You have --enable-libfdk-aac in the configure but either didn't install libfdk-aac-dev from saucy repos or do the "**libfdk-aac**" section from linked guide
(the repo version is ok, the guide gets you the latest version of  fdk-aac which would be better way to go.

Thank You very much, I used repository version and everything works now 
thank you

---

