---
title: "Compiling woes, please help!"
date: 2007-05-06
forum: General Help
---

### Post by McSnuffy on 2007-05-06
Hi. I'm on Dapper 6.06 right now, attempting to compile a patched version of the most recent [ONscripter source code]("htthttp://nscripter.insani.org/onscripter.html") and running into some problems. I realize that many of you probably haven't used ONscripter, but I hope that my problem is general enough that somebody with enough knowledge of compiling can help me out. 

Anyway, after un-tarring and patching the ONscripter source code, I navigate to the directory where I attempt to compile and install everything through the included Linux makefile:
```
navi@wired:~/Games/Onscripter/onscripter-20060724-insani$ make -f Makefile.Linux.insani
```
I get the following output:
```
g++ -o onscripter onscripter.o DirectReader.o SarReader.o NsaReader.o ScriptHandler.o ScriptParser.o ScriptParser_command.o ONScripterLabel.o ONScripterLabel_command.o ONScripterLabel_text.o ONScripterLabel_effect.o ONScripterLabel_event.o ONScripterLabel_rmenu.o ONScripterLabel_animation.o ONScripterLabel_sound.o ONScripterLabel_file.o ONScripterLabel_file2.o ONScripterLabel_image.o AnimationInfo.o FontInfo.o DirtyRect.o resize_image.o sjis2utf16.o  -static -z muldefs -Wl,--start-group `sdl-config --static-libs` `smpeg-config --libs` -lSDL_ttf -lfreetype -lSDL_image -ltiff -lpng -lSDL_mixer -lbz2 -lz -ljpeg -lm -lvorbis -lvorbisenc -lvorbisfile -logg -lgpm -lncurses -lslang -ldirectfb -lfusion -ldirect -lvga -ldl -lesd -lartsc -lasound -lX11 -laa -Wl,--end-group
/usr/lib/libSDL.a(SDL_x11gl.o): In function `X11_GL_LoadLibrary': warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libSDL_mixer.a(mdriver.o): In function `MD_DropPrivileges': warning: Using 'getpwnam' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libesd.a(libesd_la-esdlib.o): In function `esd_connect_tcpip': warning: Using 'getaddrinfo' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libesd.a(libesd_la-esdlib.o): In function `esd_connect_tcpip': warning: Using 'gethostbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libX11.a(x11_trans.o): In function `_X11TransSocketINETConnect': warning: Using 'getservbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/libaudio.a(ConnSvr.o): In function `GetAuthorization':/build/buildd/nas-1.7/lib/audio/ConnSvr.c:1990: undefined reference to `XauDisposeAuth'
/usr/lib/libaudio.a(ConnSvr.o): In function `_AuConnectServer':/build/buildd/nas-1.7/lib/audio/ConnSvr.c:1841: undefined reference to `XauGetBestAuthByAddr'
/usr/lib/libX11.a(ConnDis.o): In function `_X11TransConnectDisplay': undefined reference to `XauDisposeAuth'
/usr/lib/libX11.a(ConnDis.o): In function `_X11TransConnectDisplay': undefined reference to `XauGetBestAuthByAddr'
collect2: ld returned 1 exit status
make: *** [onscripter] Error 1
```
I've done some Googling but I have no idea what to make of this output and the errors. Does anybody with compiling knowledge know how I might be able to fix this? Even if you don't have an exact answer but have an idea or two about what is going on, please respond as it may still help to point me in the right direction.

Thanks for your time.

---

### Post by rai4shu2 on 2007-05-06
You realize onscripter is available in the universe repo?

---

### Post by ramjet_1953 on 2007-05-06
Have you got build-essential installed?

If not, copy and paste this into a terminal:

[COLOR="Red"]sudo apt-get build-essential[/COLOR]

Are you running [COLOR="Red"]./config[/COLOR] first?

The three steps are:

[COLOR="Blue"]./configure
make
sudo make install[/COLOR]

I usually use [COLOR="Blue"]checkinstall [/COLOR], instead of sudo make install, as it produces a .deb package, which makes it much easier to un-install the application at a later date, if you need to.

[COLOR="Red"]sudo apt-get install checkinstall[/COLOR]

Of course, dependencies have to be met, also.

Regards,
Roger :cool:

---

### Post by McSnuffy on 2007-05-06
> **rai4shu2 said:**
> You realize onscripter is available in the universe repo?
It is, but in order to use the English patch for Tsukihime, you need to compile a newer build.

> **ramjet_1953 said:**
> Have you got build-essential installed?

If not, copy and paste this into a terminal:

[COLOR="Red"]sudo apt-get build-essential[/COLOR]

Are you running [COLOR="Red"]./config[/COLOR] first?

The three steps are:

[COLOR="Blue"]./configure
make
sudo make install[/COLOR]

I usually use [COLOR="Blue"]checkinstall [/COLOR], instead of sudo make install, as it produces a .deb package, which makes it much easier to un-install the application at a later date, if you need to.

[COLOR="Red"]sudo apt-get install checkinstall[/COLOR]

Of course, dependencies have to be met, also.

Regards,
Roger :cool:

This may sound odd, but there is no "./configure" in the folder. I looked this up on other forums, and the answer was simple to skip straight to "make -f". Concerning dependencies, I believe that I have everything. I spent a good two hours downloading all sorts of dev packages just to get to the point that I am at now. I could be wrong though. Does anybody have an idea as to what my output means?

---

### Post by mrThefter on 2008-01-03
Lucky you, I was compiling this myself just now because I'm using linux as primary on my new laptop (I run windows primary on desktop...DX9 and gaming =/ )

Anyway, the problem is that the makefile doesn't define Xauth to be linked (among a few other libraries)
So, on the LIB line under the comment about having oggvorbis, english, and insani, add, somewhere before --end-group, -lXau.
That should do the trick. Let me know how it works out.

Just for clarification, the Tsukihime english patch actually requires a patched build, so using the universe repo package isn't such a great idea. I haven't tried it yet, but it MIGHT be compatible. As far as I know though, the build in the repo is from another programmer/maintainer. So I don't think it's likely to be so.

---

