---
title: "Dependancy problem"
date: 2017-07-21
forum: General Help
---

### Post by Evil Wayz on 2017-07-21
I'm trying to update to a later version of Handbrake that is in the repo, but this dependency is holding me back.  What I don't understand is I appear to have a later or ewual to version of said dependency, but its giving me the error anyways.  Its Libmp3lame0 

[IMG]http://i68.tinypic.com/kexeeg.jpg[/IMG]

---

### Post by vocx on 2017-07-21
> **Evil Wayz said:**
> I'm trying to update to a later version of Handbrake that is in the repo, but this dependency is holding me back.  What I don't understand is I appear to have a later or ewual to version of said dependency, but its giving me the error anyways.  Its Libmp3lame0 


How did you install Handbrake? If it is a self-contained ".tar.gz" it may be searching for the "libmp3lame0" library inside its own directory, and not in the system-wide directory. That is, maybe if you installed Handbrake in "/opt/handbrake", it could be looking for plugins in "/opt/handbrake/libs" or so.

Did you compile this new version of Handbrake? Maybe you need to modify the Makefile so that during compilation the executable is linked against "libmp3lame0", or directed to the system-wide directories where "libmp3lame0" is found, for example, "/usr/lib", or so.

There is also an environmental variable that instructs the programs to look for libraries if not in the standard directories, maybe LD_LIBRARY_PATH. So, you could try setting this value and then running your version of Handbrake.

There could be other reasons why it doesn't find the library, this is just one idea.

---

### Post by Evil Wayz on 2017-07-21
I installed it thru the Handbrake ppa.  But it's stuck back in 1.0.3, and there are some features I need that are in 1.0.7.  I initially had four depencies that were bad, I solved the others with a combination of removing and reinstalling, and forced installs.  This one, I have no idea.  I suppose i could remove the PPA and handbrake-gtk and try to build it from source but I kind of suck at it, sometimes they work and sometimes they don't.

---

### Post by Evil Wayz on 2017-07-21
This is what happened when I tried removing the package that is currently installed:

[IMG]http://i63.tinypic.com/f4qpfd.jpg[/IMG]

Don't want to mess with all that.

---

### Post by vocx on 2017-07-21
> **Evil Wayz said:**
> I installed it thru the Handbrake ppa.  But it's stuck back in 1.0.3, and there are some features I need that are in 1.0.7.  I initially had four depencies that were bad, I solved the others with a combination of removing and reinstalling, and forced installs.  This one, I have no idea.  I suppose i could remove the PPA and handbrake-gtk and try to build it from source but I kind of suck at it, sometimes they work and sometimes they don't.
Nobody "sucks" at compiling. Compilation is an exact science. You either have the correct dependencies, with the correct linker options, or not.

Edit: please do not put images of text. It's extremely annoying because it cannot be selected or searched online. All output generated in a terminal should be in "```
" tags in this forum.

[CODE]
#This is inside CODE tags, wow!
The following packages have unmet dependencies:
 libavdevice57 : Depends: libavcodec57

It keeps          the spaces                in the   code
         dfsd          sdfsdf     fjslfjas;ldf

```

---

### Post by Evil Wayz on 2017-07-22
You can in fact suck at compiling, when you do the exact same things with two builds and one works and the other doesn't.

---

### Post by Evil Wayz on 2017-07-22
So I get this far building from source.  Also, autogen.sh returned with command not found. 

```
touch contrib/ffmpeg/.stamp.patch
set -e; cd ./contrib/ffmpeg/libav-12/; CC=/usr/bin/gcc CFLAGS="-I/usr/local/src/HandBrake-1.0.7/build/contrib/include -std=gnu99 -mfpmath=sse -msse2" CXX=/usr/bin/g++ CXXFLAGS="-I/usr/local/src/HandBrake-1.0.7/build/contrib/include -mfpmath=sse -msse2" CPPFLAGS="-I/usr/local/src/HandBrake-1.0.7/build/contrib/include -mfpmath=sse -msse2" LDFLAGS="-L/usr/local/src/HandBrake-1.0.7/build/contrib/lib " PKG_CONFIG_PATH="/usr/local/src/HandBrake-1.0.7/build/contrib/lib/pkgconfig" PATH="/usr/local/src/HandBrake-1.0.7/build/contrib/bin:/usr/local/src/HandBrake-1.0.7/build/contrib/bin:/home/wolf/bin:/home/wolf/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/jvm/java-9-oracle/bin:/usr/lib/jvm/java-9-oracle/db/bin" ./configure --prefix=/usr/local/src/HandBrake-1.0.7/build/contrib/ --disable-shared --enable-static --enable-gpl --disable-doc --disable-bsfs --enable-bsf=aac_adtstoasc --disable-avconv --disable-avplay --disable-avprobe --disable-avdevice --disable-muxers --disable-network --disable-hwaccels --disable-vaapi --disable-vdpau --disable-encoders --enable-libmp3lame --enable-encoder=aac --enable-encoder=ac3 --enable-encoder=eac3 --enable-encoder=flac --enable-encoder=mpeg2video --enable-encoder=mpeg4 --enable-encoder=libmp3lame --enable-libopus --enable-encoder=libopus --enable-libvpx --enable-encoder=libvpx_vp8 --disable-decoder=libvpx_vp8 --enable-encoder=libvpx_vp9 --disable-decoder=libvpx_vp9 --enable-zlib --enable-bzlib --enable-pthreads --cc="/usr/bin/gcc" --extra-ldflags="-mfpmath=sse -msse2 -L/usr/local/src/HandBrake-1.0.7/build/contrib/lib" --enable-muxer=matroska --enable-muxer=webm --enable-muxer=mov --enable-muxer=mp4 --enable-muxer=psp --enable-muxer=ipod --disable-debug --extra-cflags="-mfpmath=sse -msse2 -I/usr/local/src/HandBrake-1.0.7/build/contrib/include -DNDEBUG"
ERROR: libmp3lame >= 3.98.3 not found

If you think configure made a mistake, make sure you are using the latest
version from Git.  If the latest version fails, report the problem to the
libav-tools@libav.org mailing list or IRC #libav on irc.freenode.net.
Include the log file "config.log" produced by configure as this will help
solving the problem.
../contrib/ffmpeg/module.rules:2: recipe for target 'contrib/ffmpeg/.stamp.configure' failed
make: *** [contrib/ffmpeg/.stamp.configure] Error 1

```

---

### Post by oldos2er on 2017-07-22
Did you try running ```
sudo apt build-dep handbrake
``` Or try installing it from github.

---

### Post by Evil Wayz on 2017-07-22
```
wolf@wolf-desktopbubba:~$ sudo apt build-dep handbrake
[sudo] password for wolf: 
Reading package lists... Done
E: Unable to find a source package for handbrake

```

Do I need to tell it what folder the tarball is in?
I tried installing from github and i got the same error as before.  I have the dependency, a higher version than called for but I don't know how to tell the program where it is.

---

### Post by oldos2er on 2017-07-22
> **Evil Wayz said:**
> ```
wolf@wolf-desktopbubba:~$ sudo apt build-dep handbrake
[sudo] password for wolf: 
Reading package lists... Done
E: Unable to find a source package for handbrake

```

Do I need to tell it what folder the tarball is in?

No, you need to enable your source repositories in software sources.

---

### Post by Evil Wayz on 2017-07-22
Ok did that (enabled the source repo for Handrbake and updated), got the same output, it doesn't know that i have libmp3lame0 ver 3.99.5

```
wolf@wolf-desktopbubba:/usr/local/src/HandBrake-1.0.7/build$ make
set -e; cd ./contrib/ffmpeg/libav-12/; CC=/usr/bin/gcc CFLAGS="-I/usr/local/src/HandBrake-1.0.7/build/contrib/include -std=gnu99 -mfpmath=sse -msse2" CXX=/usr/bin/g++ CXXFLAGS="-I/usr/local/src/HandBrake-1.0.7/build/contrib/include -mfpmath=sse -msse2" CPPFLAGS="-I/usr/local/src/HandBrake-1.0.7/build/contrib/include -mfpmath=sse -msse2" LDFLAGS="-L/usr/local/src/HandBrake-1.0.7/build/contrib/lib " PKG_CONFIG_PATH="/usr/local/src/HandBrake-1.0.7/build/contrib/lib/pkgconfig" PATH="/usr/local/src/HandBrake-1.0.7/build/contrib/bin:/home/wolf/bin:/home/wolf/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/jvm/java-9-oracle/bin:/usr/lib/jvm/java-9-oracle/db/bin" ./configure --prefix=/usr/local/src/HandBrake-1.0.7/build/contrib/ --disable-shared --enable-static --enable-gpl --disable-doc --disable-bsfs --enable-bsf=aac_adtstoasc --disable-avconv --disable-avplay --disable-avprobe --disable-avdevice --disable-muxers --disable-network --disable-hwaccels --disable-vaapi --disable-vdpau --disable-encoders --enable-libmp3lame --enable-encoder=aac --enable-encoder=ac3 --enable-encoder=eac3 --enable-encoder=flac --enable-encoder=mpeg2video --enable-encoder=mpeg4 --enable-encoder=libmp3lame --enable-libopus --enable-encoder=libopus --enable-libvpx --enable-encoder=libvpx_vp8 --disable-decoder=libvpx_vp8 --enable-encoder=libvpx_vp9 --disable-decoder=libvpx_vp9 --enable-zlib --enable-bzlib --enable-pthreads --cc="/usr/bin/gcc" --extra-ldflags="-mfpmath=sse -msse2 -L/usr/local/src/HandBrake-1.0.7/build/contrib/lib" --enable-muxer=matroska --enable-muxer=webm --enable-muxer=mov --enable-muxer=mp4 --enable-muxer=psp --enable-muxer=ipod --disable-debug --extra-cflags="-mfpmath=sse -msse2 -I/usr/local/src/HandBrake-1.0.7/build/contrib/include -DNDEBUG"
ERROR: opus not found

If you think configure made a mistake, make sure you are using the latest
version from Git.  If the latest version fails, report the problem to the
libav-tools@libav.org mailing list or IRC #libav on irc.freenode.net.
Include the log file "config.log" produced by configure as this will help
solving the problem.
../contrib/ffmpeg/module.rules:2: recipe for target 'contrib/ffmpeg/.stamp.configure' failed
make: *** [contrib/ffmpeg/.stamp.configure] Error 1

```

---

### Post by oldos2er on 2017-07-22
I don't see anything about  libmp3lame0 in the output? ```
ERROR: opus not found
``` You may need to enable source in the default Ubuntu repos too, since libmp3lame-dev is in the universe source repo.

Did you rerun ./configure or ./autogen.sh ? Need to do that after installing dependencies.

---

### Post by Evil Wayz on 2017-07-22
I actually did enable Ubuntu source.  Autogen.sh produces command not found.  .configure --force tells me successful and to go to ./build and run make.  And that'[s where the hiccup is, ffmpeg doesn't want to act right.

---

### Post by Evil Wayz on 2017-07-22
I just noticed that the errors are similar but not exact.  So apparently libmp3lame0 isn't the problem anymore.  I have libopus0.

---

### Post by oldos2er on 2017-07-22
When you're compiling you need the development files, most of which end with -dev; this is also why you need to enable any and all source repos. So install libopus-dev if you haven't already (and apologies if you knew this already!) Then rerun ./configure or ./autogen.sh

Edit: Why are you forcing configure? Try it without.

---

### Post by Evil Wayz on 2017-07-22
It insists i have to use that to create the build directory.

```
wolf@wolf-desktopbubba:/usr/local/src/HandBrake-1.0.7$ ./configure
probe: host tuple...(pass) x86_64-unknown-linux-gnu
compute: available architectures...(pass) x86_64
find: ar...(pass) /usr/bin/ar
find: cp...(pass) /bin/cp
find: gcc...(pass) /usr/bin/gcc
find: gmake...(pass) /usr/bin/make
find: gm4...(pass) /usr/bin/m4
find: mkdir...(pass) /bin/mkdir
find: gpatch...(pass) /usr/bin/patch
find: rm...(pass) /bin/rm
find: ranlib...(pass) /usr/bin/ranlib
find: strip...(pass) /usr/bin/strip
find: gtar...(pass) /bin/tar
find: yasm...(pass) /usr/bin/yasm
find: autoconf...(pass) /usr/bin/autoconf
find: automake...(pass) /usr/bin/automake
find: cmake...(pass) /usr/bin/cmake
find: libtool...(pass) /usr/bin/libtool
find: pkg-config...(pass) /usr/bin/pkg-config
find: xcodebuild...(fail) not found
find: lipo...(fail) not found
compute: build tuple...(pass) x86_64-unknown-linux-gnu
probe: number of CPU cores...(pass) 4
probe: repo info...(fail) code 128
probe: version.txt...(fail)
compute: project data...(pass) HandBrake (release)
version probe: yasm...(pass) 1.3.0
probe: strerror_r...(pass) end
compute: makevar SRC/    = ..
compute: makevar BUILD/  = .
compute: makevar PREFIX/ = /usr/local
ERROR: build directory already exists: ./build (use --force to overwrite); configure stop.
wolf@wolf-desktopbubba:/usr/local/src/HandBrake-1.0.7$ ./configure --forceprobe: host tuple...(pass) x86_64-unknown-linux-gnu
compute: available architectures...(pass) x86_64
find: ar...(pass) /usr/bin/ar
find: cp...(pass) /bin/cp
find: gcc...(pass) /usr/bin/gcc
find: gmake...(pass) /usr/bin/make
find: gm4...(pass) /usr/bin/m4
find: mkdir...(pass) /bin/mkdir
find: gpatch...(pass) /usr/bin/patch
find: rm...(pass) /bin/rm
find: ranlib...(pass) /usr/bin/ranlib
find: strip...(pass) /usr/bin/strip
find: gtar...(pass) /bin/tar
find: yasm...(pass) /usr/bin/yasm
find: autoconf...(pass) /usr/bin/autoconf
find: automake...(pass) /usr/bin/automake
find: cmake...(pass) /usr/bin/cmake
find: libtool...(pass) /usr/bin/libtool
find: pkg-config...(pass) /usr/bin/pkg-config
find: xcodebuild...(fail) not found
find: lipo...(fail) not found
compute: build tuple...(pass) x86_64-unknown-linux-gnu
probe: number of CPU cores...(pass) 4
probe: repo info...(fail) code 128
probe: version.txt...(fail)
compute: project data...(pass) HandBrake (release)
version probe: yasm...(pass) 1.3.0
probe: strerror_r...(pass) end
compute: makevar SRC/    = ..
compute: makevar BUILD/  = .
compute: makevar PREFIX/ = /usr/local
chdir: ./build
write: GNUmakefile
write: project/handbrake.m4
write: distfile.cfg
-------------------------------------------------------------------------------
Build is configured!
You may now cd into ./build and run make (/usr/bin/make).
wolf@wolf-desktopbubba:/usr/local/src/HandBrake-1.0.7$ cd build
wolf@wolf-desktopbubba:/usr/local/src/HandBrake-1.0.7/build$ make
/usr/bin/m4 -Iproject ../libhb/project.h.m4 > libhb/project.h
set -e; cd ./contrib/ffmpeg/libav-12/; CC=/usr/bin/gcc CFLAGS="-I/usr/local/src/HandBrake-1.0.7/build/contrib/include -std=gnu99 -mfpmath=sse -msse2" CXX=/usr/bin/g++ CXXFLAGS="-I/usr/local/src/HandBrake-1.0.7/build/contrib/include -mfpmath=sse -msse2" CPPFLAGS="-I/usr/local/src/HandBrake-1.0.7/build/contrib/include -mfpmath=sse -msse2" LDFLAGS="-L/usr/local/src/HandBrake-1.0.7/build/contrib/lib " PKG_CONFIG_PATH="/usr/local/src/HandBrake-1.0.7/build/contrib/lib/pkgconfig" PATH="/usr/local/src/HandBrake-1.0.7/build/contrib/bin:/home/wolf/bin:/home/wolf/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/jvm/java-9-oracle/bin:/usr/lib/jvm/java-9-oracle/db/bin" ./configure --prefix=/usr/local/src/HandBrake-1.0.7/build/contrib/ --disable-shared --enable-static --enable-gpl --disable-doc --disable-bsfs --enable-bsf=aac_adtstoasc --disable-avconv --disable-avplay --disable-avprobe --disable-avdevice --disable-muxers --disable-network --disable-hwaccels --disable-vaapi --disable-vdpau --disable-encoders --enable-libmp3lame --enable-encoder=aac --enable-encoder=ac3 --enable-encoder=eac3 --enable-encoder=flac --enable-encoder=mpeg2video --enable-encoder=mpeg4 --enable-encoder=libmp3lame --enable-libopus --enable-encoder=libopus --enable-libvpx --enable-encoder=libvpx_vp8 --disable-decoder=libvpx_vp8 --enable-encoder=libvpx_vp9 --disable-decoder=libvpx_vp9 --enable-zlib --enable-bzlib --enable-pthreads --cc="/usr/bin/gcc" --extra-ldflags="-mfpmath=sse -msse2 -L/usr/local/src/HandBrake-1.0.7/build/contrib/lib" --enable-muxer=matroska --enable-muxer=webm --enable-muxer=mov --enable-muxer=mp4 --enable-muxer=psp --enable-muxer=ipod --disable-debug --extra-cflags="-mfpmath=sse -msse2 -I/usr/local/src/HandBrake-1.0.7/build/contrib/include -DNDEBUG"
ERROR: opus not found

If you think configure made a mistake, make sure you are using the latest
version from Git.  If the latest version fails, report the problem to the
libav-tools@libav.org mailing list or IRC #libav on irc.freenode.net.
Include the log file "config.log" produced by configure as this will help
solving the problem.
../contrib/ffmpeg/module.rules:2: recipe for target 'contrib/ffmpeg/.stamp.configure' failed
make: *** [contrib/ffmpeg/.stamp.configure] Error 1

```

---

### Post by oldos2er on 2017-07-22
I assumed you were working in your home folder, not /usr/local/src

Try deleting the build folder, install libopus-dev, and rerun ./configure without force.

---

### Post by mc4man on 2017-07-22
install libopus-dev  There may be more, according to the ppa's control file this is what they use.
```
sudo apt install libbz2-dev zlib1g-dev libgtk-3-dev libwebkitgtk-3.0-dev libnotify-dev \
libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev python libappindicator3-dev \
libfribidi-dev libxml2-dev libogg-dev libtheora-dev libvorbis-dev libopus-dev \
libsamplerate0-dev libfreetype6-dev libfontconfig1-dev libass-dev libmp3lame-dev \
libx264-dev libjansson-dev
```

There's no good reason you couldn't use the current ppa build, may be related to severe  issues as seen in post 4, you could ignore that, fix, or just do a fresh install where all would be well, at least for a bit..

---

### Post by vasa1 on 2017-07-22
> **vocx said:**
> ...
Edit: please do not put images of text. It's extremely annoying because it cannot be selected or searched online. All output generated in a terminal should be in [noparse][CODE][/noparse] tags in this forum.
...
A big +1 to that. And if images are to be included, use the forum's attachment facility rather than some ad- and tracker-full third party site.

---

