---
title: "Would some one be willing to package this small program?"
date: 2008-01-27
forum: General Help
---

### Post by onesojourner on 2008-01-27
I would like to get this small program installed but it is way over my skill level. Would some one on here be willing to package it for me? 

The program allows you to use a wii classic controller with your emulators.

---

### Post by sub2007 on 2008-01-27
We just built this and it went really quite easily bar one or two dependency issues. Unfortunately it's not an easy one (for me anyway) to just package into a .deb file for you and so I'll talk you through how to compile it. If you'd rather not than fine but, as I said, this one isn't difficult at all to compile. If you get any error messages along the way STOP and post them here - they'll be dependency issues that need resolving (and I should be able to work them out from the error messages).

So first things first, extract the archive to a folder where you can easily find it (I would extract it to /home/*your username*/ which is convenient because that's where Terminal opens in).

Now we'll satisfy the dependencies. These are the dependencies that I needed, you may need more - as I said please post back any error messages here.

In Terminal **sudo apt-get install build-essential libbluetooth-dev libxtst-dev **

Hopefully that'll satisfy the dependencies.

Now we DON'T need to run ./configure as there is no configure file, in fact there is a makefile already so our next step is (in Terminal):

[b]cd **whatever the XWii folder is called**/

make[/b]

Hopefully it will just run through and make the entire thing with no errors.

Now our next stage is NOT *sudo make install* because there is no install file. Instead please check inside the XWii folder (the extracted one) - there should be an executable called XWii there. If so then fantastic - the program compiled correctly! To run it you just need to (in Terminal) enter:

./XWii

When I tried to run it, it told me that I needed to specify a profile - check the packages website for more instructions about creating profiles.

Making a launcher is slightly harder but let's get it working first and then do that step next :)

---

### Post by onesojourner on 2008-01-27
fixed
network cable fell out...


I found the documentation for the profiles. your code in the terminal should look something like this

ex: classic controller
./xwii Profiles/classic.xwii

---

### Post by bodhi.zazen on 2008-01-27
try 

```
sudo apt-get update
```

Then try re-installing those packages

---

### Post by onesojourner on 2008-01-27
ok I got 3 errors with make. I am posting it all, I don't know if you need all this or not.

```

peter@peter-laptop:~$ cd xwii
peter@peter-laptop:~/xwii$ make
g++ main.cpp -c -I ./include
make[1]: Entering directory `/home/peter/xwii/wiiuse-0.9'
make[2]: Entering directory `/home/peter/xwii/wiiuse-0.9/src'

------
- Building wiiuse ...
------
make wiiuse.so
make[3]: Entering directory `/home/peter/xwii/wiiuse-0.9/src'
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c classic.c
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c dynamics.c
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c events.c
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c io.c
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c io_nix.c
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c io_win.c
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c ir.c
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c main.c
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c nunchuk.c
gcc -Wall -pipe -fPIC -funroll-loops -I. -I../include/ -c wiiuse.c
g++ -Wall -pipe -fPIC -funroll-loops -shared -lbluetooth classic.o dynamics.o events.o io.o io_nix.o io_win.o ir.o main.o nunchuk.o wiiuse.o  -o wiiuse.so
make[3]: Leaving directory `/home/peter/xwii/wiiuse-0.9/src'

--
-- Build complete.
--

make[2]: Leaving directory `/home/peter/xwii/wiiuse-0.9/src'
make[2]: Entering directory `/home/peter/xwii/wiiuse-0.9/api'

------
- Building wiiuse example ...
------
make wiiuse-example
make[3]: Entering directory `/home/peter/xwii/wiiuse-0.9/api'
gcc -Wall -pipe -I. -I../include/ -c example.c
gcc -Wall -pipe -I. -I../include/ -c wiiuse.c
g++ -Wall -pipe -ldl example.o wiiuse.o  -o wiiuse-example
make[3]: Leaving directory `/home/peter/xwii/wiiuse-0.9/api'

--
-- Build complete.
--

make[2]: Leaving directory `/home/peter/xwii/wiiuse-0.9/api'
make[2]: Entering directory `/home/peter/xwii/wiiuse-0.9/gfx'

------
- Building wiiuse example ...
------
make wiiuse-gfx
make[3]: Entering directory `/home/peter/xwii/wiiuse-0.9/gfx'
gcc -Wall -pipe -I. -I../include/ -c gfx.c
gfx.c:41:19: error: GL/gl.h: No such file or directory
gfx.c:42:20: error: GL/glu.h: No such file or directory
gfx.c:43:21: error: SDL/SDL.h: No such file or directory
gfx.c:54: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;width&#8217;
gfx.c:55: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;backColor&#8217;
gfx.c:65: error: expected &#8216;)&#8217; before &#8216;new_width&#8217;
gfx.c: In function &#8216;display&#8217;:
gfx.c:98: warning: implicit declaration of function &#8216;glClear&#8217;
gfx.c:98: error: &#8216;GL_COLOR_BUFFER_BIT&#8217; undeclared (first use in this function)
gfx.c:98: error: (Each undeclared identifier is reported only once
gfx.c:98: error: for each function it appears in.)
gfx.c:98: error: &#8216;GL_DEPTH_BUFFER_BIT&#8217; undeclared (first use in this function)
gfx.c:99: warning: implicit declaration of function &#8216;glMatrixMode&#8217;
gfx.c:99: error: &#8216;GL_MODELVIEW&#8217; undeclared (first use in this function)
gfx.c:100: warning: implicit declaration of function &#8216;glLoadIdentity&#8217;
gfx.c:102: warning: implicit declaration of function &#8216;glBegin&#8217;
gfx.c:102: error: &#8216;GL_TRIANGLES&#8217; undeclared (first use in this function)
gfx.c:104: warning: implicit declaration of function &#8216;glColor3f&#8217;
gfx.c:105: warning: implicit declaration of function &#8216;glVertex3f&#8217;
gfx.c:105: error: &#8216;width&#8217; undeclared (first use in this function)
gfx.c:105: error: &#8216;height&#8217; undeclared (first use in this function)
gfx.c:124: warning: implicit declaration of function &#8216;glEnd&#8217;
gfx.c:126: warning: implicit declaration of function &#8216;SDL_GL_SwapBuffers&#8217;
gfx.c: At top level:
gfx.c:129: error: expected &#8216;)&#8217; before &#8216;new_width&#8217;
gfx.c: In function &#8216;main&#8217;:
gfx.c:192: warning: implicit declaration of function &#8216;SDL_Init&#8217;
gfx.c:192: error: &#8216;SDL_INIT_VIDEO&#8217; undeclared (first use in this function)
gfx.c:193: warning: implicit declaration of function &#8216;SDL_GetError&#8217;
gfx.c:193: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;int&#8217;
gfx.c:197: warning: implicit declaration of function &#8216;SDL_GL_SetAttribute&#8217;
gfx.c:197: error: &#8216;SDL_GL_DOUBLEBUFFER&#8217; undeclared (first use in this function)
gfx.c:198: error: &#8216;SDL_GL_DEPTH_SIZE&#8217; undeclared (first use in this function)
gfx.c:201: error: &#8216;width&#8217; undeclared (first use in this function)
gfx.c:202: error: &#8216;height&#8217; undeclared (first use in this function)
gfx.c:203: warning: implicit declaration of function &#8216;SDL_SetVideoMode&#8217;
gfx.c:203: error: &#8216;SDL_RESIZABLE&#8217; undeclared (first use in this function)
gfx.c:203: error: &#8216;SDL_OPENGL&#8217; undeclared (first use in this function)
gfx.c:207: warning: implicit declaration of function &#8216;glEnable&#8217;
gfx.c:207: error: &#8216;GL_DEPTH_TEST&#8217; undeclared (first use in this function)
gfx.c:208: warning: implicit declaration of function &#8216;glDepthFunc&#8217;
gfx.c:208: error: &#8216;GL_LEQUAL&#8217; undeclared (first use in this function)
gfx.c:209: warning: implicit declaration of function &#8216;glClearColor&#8217;
gfx.c:212: warning: implicit declaration of function &#8216;resize_window&#8217;
gfx.c:215: error: &#8216;SDL_Event&#8217; undeclared (first use in this function)
gfx.c:215: error: expected &#8216;;&#8217; before &#8216;event&#8217;
gfx.c:218: warning: implicit declaration of function &#8216;SDL_PollEvent&#8217;
gfx.c:218: error: &#8216;event&#8217; undeclared (first use in this function)
gfx.c:220: error: &#8216;SDL_VIDEORESIZE&#8217; undeclared (first use in this function)
gfx.c:226: error: &#8216;SDL_QUIT&#8217; undeclared (first use in this function)
gfx.c:229: warning: implicit declaration of function &#8216;SDL_Quit&#8217;
make[3]: *** [gfx.o] Error 1
make[3]: Leaving directory `/home/peter/xwii/wiiuse-0.9/gfx'
make[2]: *** [Release] Error 2
make[2]: Leaving directory `/home/peter/xwii/wiiuse-0.9/gfx'
make[1]: *** [Release] Error 2
make[1]: Leaving directory `/home/peter/xwii/wiiuse-0.9'
make: *** [wiiuse-0.9/api/wiiuse.o] Error 2

```

---

### Post by onesojourner on 2008-01-27
can any one help me out with these errors?

---

### Post by fatalGlory on 2008-01-28
You appear to be missing the SDL and openGL libs.  

I'm not sure which packages exactly need to be installed but I'd say start with:

```
sudo apt-get install libsdl1.2-dev
```

and see if that enables you to make the program.  That will at least take care of SDL/SDL.h.  Do that and post any errors that come up after that.

P.S.  I created XWii, I don't have any experience creating .deb packages.  If someone could point me in the right direction to learn how I'd appreciate it.

---

### Post by RawMustard on 2008-01-28
sudo apt-get install checkinstall and read this page.

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by onesojourner on 2008-01-28
That did it.

---

### Post by onesojourner on 2008-01-31
I wrote a how to here [http://ubuntuforums.org/showthread.php?p=4243141#post4243141](http://ubuntuforums.org/showthread.php?p=4243141#post4243141)

hopefully that will help some one else out.

---

