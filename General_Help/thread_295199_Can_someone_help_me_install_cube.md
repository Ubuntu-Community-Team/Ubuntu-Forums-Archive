---
title: "Can someone help me install cube?"
date: 2006-11-07
forum: General Help
---

### Post by thecynicality on 2006-11-07
I am trying to install cube on my system but i can't get it working, when i run the script it says it can't find some directory, i'm not sure what to do, im brand new to linux and i have no idea how to install games and apps. Thanks.

---

### Post by taurus on 2006-11-07
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by thecynicality on 2006-11-07
Ok i read every part of those articles that might help me but i still can't figure this out ive tried several methods and none work. argh this is frustrating.

---

### Post by taurus on 2006-11-07
Okay, tell me where you've downloaded that and I will see how to install it!!!  :rolleyes: 

Also, if you need somebody to help you, you need to include the command that you ran and the exact error message that you got from running that command.  Otherwise, nobody's sure what you are talking about.  It's like taking your car to a mechanic and say "Hey, how come my car doesn't run?"

---

### Post by thecynicality on 2006-11-07
I'm trying to install Cube, its the game at the bottom of this page: [http://www.cubeengine.com/](http://www.cubeengine.com/)

---

### Post by taurus on 2006-11-07
So, you downloaded the cube_2005_08_29_unix.tar.gz to ~/Desktop!  Open a terminal and do

```

cd Desktop
tar xvzf cube_2005_08_29_unix.tar.gz
cd cube

```
You have a couple of options.  You can run it right now by doing

```

cd bin_unix
./linux_client

```
**[COLOR="Red"]Or[/COLOR]** you can install it on system while by modifying cube_unix!!!

```
gedit cube_unix
```
Here is what I would change to install it...

```

#!/bin/bash
# CUBE_DIR should refer to the directory in which Cube is placed.
#CUBE_DIR=~/cube
#CUBE_DIR=/usr/local/lib/cube
CUBE_DIR=/opt/cube

# SYSTEM_NAME should be set to the name of your operating system.
#SYSTEM_NAME=Linux
SYSTEM_NAME=`uname -s`

# MACHINE_NAME should be set to the name of your processor.
#MACHINE_NAME=i686
MACHINE_NAME=`uname -m`

case ${SYSTEM_NAME} in
Linux)
  SYSTEM_PREFIX=linux_
  ;;
FreeBSD)
  SYSTEM_PREFIX=freebsd_
  ;;
*)
  echo "Your operating system does not have a supported Cube client."
  exit 1
  ;;
esac

case ${MACHINE_NAME} in
i486|i586|i686)
  MACHINE_PREFIX=
  ;;
#ppc)
#  MACHINE_PREFIX=ppc_
#  ;;
*)
  echo "Your processor does not have a supported Cube client."
  exit 1
  ;;
esac

cd ${CUBE_DIR}
exec ${CUBE_DIR}/bin_unix/${MACHINE_PREFIX}${SYSTEM_PREFIX}client $*

```
Then, you just have to run it with sudo to install it to /opt/cube...

```
sudo ./cube_unix
```
Have fun.

---

### Post by thecynicality on 2006-11-08
I get this error when i try and launch it:

./linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by thecynicality on 2006-11-08
When i try the second method i get this error:

cd: 41: can't cd to /opt/cube
exec: 42: /opt/cube/bin_unix/linux_client: not found

---

### Post by jocko on 2006-11-08
> **thecynicality said:**
> I get this error when i try and launch it:

./linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

Try running this before you try again:
```
sudo aptitude install libsdl-image1.2
```

---

### Post by thecynicality on 2006-11-08
Ok i tried that and it installed, and i tried to run it again now it gives me this error:

couldn't load texture data/newchars.png
could not find core textures (hint: run cube from the parent of the bin directory) (Couldn't open data/newchars.png)

I found this in one of the readmes

Clients will need the following dynamic link libraries present:
opengl, glu, sdl, sdl_image, sdl_mixer, png, jpeg, zlib (1.2.1 for
all SDL libs, do a ldd for details).

I don't think i have all those libraries, how would i get those?

---

### Post by thecynicality on 2006-11-08
Yeah still can't figure out how to get the libraries, any help would be great.

---

### Post by taurus on 2006-11-08
> **thecynicality said:**
> Ok i tried that and it installed, and i tried to run it again now it gives me this error:

couldn't load texture data/newchars.png
could not find core textures (hint: run cube from the parent of the bin directory) (Couldn't open data/newchars.png)

I found this in one of the readmes

Clients will need the following dynamic link libraries present:
opengl, glu, sdl, sdl_image, sdl_mixer, png, jpeg, zlib (1.2.1 for
all SDL libs, do a ldd for details).

I don't think i have all those libraries, how would i get those?

Use synaptic to search for those files!

---

### Post by thecynicality on 2006-11-08
I get several files when i search in synaptic how do i know which to download

---

### Post by thecynicality on 2006-11-08
Ok i think i got the libraries installed i don't think thats the problem, the readme also says something about using chmod +x on the files before using them. What does that mean?

---

### Post by taurus on 2006-11-08
It means you make the files to be an executable so you can run them!  In the bin_unix directory, what is the output of this command then?

```
ldd linux_client
```

---

### Post by thecynicality on 2006-11-08
It output this:

        linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7ea4000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e91000)
        libSDL_image-1.2.so.0 => /usr/lib/libSDL_image-1.2.so.0 (0xb7e75000)
        libSDL_mixer-1.2.so.0 => /usr/lib/libSDL_mixer-1.2.so.0 (0xb7e07000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7df3000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7d53000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7cd9000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7c1f000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7bf9000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7bed000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ab9000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb79f0000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb7938000)
        libdirectfb-0.9.so.24 => /usr/lib/libdirectfb-0.9.so.24 (0xb78ea000)
        libfusion-0.9.so.24 => /usr/lib/libfusion-0.9.so.24 (0xb78e5000)
        libdirect-0.9.so.24 => /usr/lib/libdirect-0.9.so.24 (0xb78d7000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb78d3000)
        /lib/ld-linux.so.2 (0xb7f45000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb78b0000)
        libvorbisfile.so.3 => /usr/lib/libvorbisfile.so.3 (0xb78a9000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb7882000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb787d000)
        libsmpeg-0.4.so.0 => /usr/lib/libsmpeg-0.4.so.0 (0xb7825000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7818000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7739000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7736000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7731000)

---

### Post by taurus on 2006-11-08
Looks like you have all the library for that binary!  See if you can run it from where it is right now.

```
./linux_client
```

---

### Post by thecynicality on 2006-11-08
It still gives me this when i run it:

init: sdl
init: net
init: world
game mode is ffa/default
init: video: sdl
init: video: mode
init: video: misc
init: gl
init: basetex
couldn't load texture data/newchars.png
could not find core textures (hint: run cube from the parent of the bin directory) (Couldn't open data/newchars.png)

---

### Post by thecynicality on 2006-11-08
Any ideas what i have to do to fix this error?

---

### Post by maxpower on 2006-11-08
The program uses a relative path so you have to be in the directory above where you install the data directory when you run linux_client. So, open a terminal, then:
```

cd /opt/cube
bin/linux_client

```

---

