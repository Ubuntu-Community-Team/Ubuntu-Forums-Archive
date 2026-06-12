---
title: "Installing Source Package"
date: 2007-01-14
forum: General Help
---

### Post by wersdaluv on 2007-01-14
I am trying to install [OrbitView]("http://freshmeat.net/projects/orbitview/") from freshmeat but I'm having a hard time with the installation. 

I have extracted the tar.gz file and went to the folder which is the product of the extraction via the terminal. I tried to execute a configure script, but I guess the package didn't include one. This is what happened:

```
user@Laptop:~$ cd '/home/user/Extracted Files/Orbit View/OrbitView-1.0.1'
user@Laptop:~/Extracted Files/Orbit View/OrbitView-1.0.1$ /home/user/Extracted Files/Orbit View/OrbitView-1.0.1/configure
bash: /home/user/Extracted: No such file or directory

```

Then, I tried "make"
```
user@Laptop:~/Extracted Files/Orbit View/OrbitView-1.0.1$ make "/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/"
make: Nothing to be done for `/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/'.

``` Please correct me if I did it the wrong way.

Finally, I tried "make install"
```
user@Laptop:~/Extracted Files/Orbit View/OrbitView-1.0.1$ sudo make install "/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/"
Password:
make: *** No rule to make target `install'.  Stop.
```

I also attached a screenshot of the extracted folder.

Please let me know about what I can do.

Thank you very much. :)

---

### Post by happy-and-lost on 2007-01-14
Try running that OrbitView script from terminal by...

```
cd /home/user/Extracted Files/Orbit View/OrbitView-1.0.1
./OrbitView
```

---

### Post by wersdaluv on 2007-01-14
I ran the OrbitView file under the folder I got into after using the code above.

```
user@Laptop:~/Extracted Files/Orbit View/OrbitView-1.0.1$ "/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/OrbitView"
OrbitView Parameters

-i     XWindows interactive mode

-p x    set pan position (-7000..7000)
-t x    set tilt position (-3000..2500)
-x x    set x resolution (320,640)
-y x    set y resolution (240,480)
-f x    set framerate (0...63)

-?      dump current settings

-c x    set compression preference (0-3)
-g x    set automatic gain control (0...65535)
-s x    set shutter speed (1...65535)
-w x    set white balance (auto/manual/indoor/outdoor/fl)
-a x    speed of automatic white balance (1...65535)
-j x    delay for automatic white balance (1...65535)
-k x    set led on-time (0...25500ms
-l x    set led off-time
-m x    set electronic sharpness (0...65535)
-n x    set backlight compensation (0=0ff, other=on)
-o x    set antiflicker mode (0=0ff, other=on)
-r x    set noise reduction mode (0=none...3=high)
-e x    reset pan(bit 0) and/or tilt(bit 1)
-q      query pan/tilt status
-z      set zoom
-h      this help


Exmaple:
OrbitView -x 320 -y 240 -f 30 -i

```

Did I run the right file?

What do I do after this? I'm sorry. I'm new with Linux. I don't get what those things mean.

---

### Post by wersdaluv on 2007-01-14
I just ran the Makefile inside the extracted folder. I don't know if I had to run that but what happened was it deleted some files inside the folder. Here's what happened:

```
user@Laptop:~/Extracted Files/Orbit View/OrbitView-1.0.1$ "/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile"
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 4: -L/usr/X11R6/lib: No such file or directory
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 6: -lXt: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 8: -O2: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 14: LIBRARYDIR: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 15: LIBRARYDIR: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 16: LIBRARYDIR: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 18: XTSELIBDIR: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 19: MEMALLOCLIBDIR: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 20: PHILIPSWEBCAMLIBDIR: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 22: XTSELIB: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 22: MEMALLOCLIB: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 22: PHILIPSWEBCAMLIB: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 23: XTSELIBDIR: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 23: MEMALLOCLIBDIR: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 23: PHILIPSWEBCAMLIBDIR: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 23: -I: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 25: orbitview.c: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 27: COMPILER: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 28: DEFINES: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 30: all: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 32: auxlibs: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 33: MAKE: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 33: -C: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 34: MAKE: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 34: -C: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 35: MAKE: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 35: -C: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 37: update: command not found
cp: cannot stat `../../LIBRARIES/XTSE/Xtse-1.0.0': No such file or directory
cp: cannot stat `../../LIBRARIES/MEMALLOC/MemAllocLib-1.0.0': No such file or directory
cp: cannot stat `../../LIBRARIES/PHILIPSWEBCAM/PhilipsWebCamLib-1.2.1': No such file or directory
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 45: OrbitView:: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 46: COMPILER: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 46: DEFINES: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 46: SOURCES: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 46: STATICLIBS: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 46: LIBDIRS: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 46: LIBS: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 46: STATICINCLUDES: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 46: -o: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 48: clean:: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 50: MAKE: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 50: clean: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 51: MAKE: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 51: clean: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 52: MAKE: command not found
/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/Makefile: line 52: clean: command not found
user@Laptop:~/Extracted Files/Orbit View/OrbitView-1.0.1$       
```

---

### Post by Sef on 2007-01-14
> ser@Laptop:~/Extracted Files/Orbit View/OrbitView-1.0.1$ "/home/user/Extracted Files/Orbit View/OrbitView-1.0.1/OrbitView"

You should just enter ./file_name

example: ```
ser@Laptop:~/Extracted Files/Orbit View/OrbitView-1.0.1$ Orbit View/OrbitView-1.0.1/OrbitView
```

Or whatever it is.

---

### Post by wersdaluv on 2007-01-14
After running the Makefile, the contents of the extracted folder changed. I have included with this post the screenshot which shows the contents of the folder.

Which file should I run?

---

### Post by wersdaluv on 2007-01-14
> **Sef said:**
> You should just enter ./file_name

example: ```
ser@Laptop:~/Extracted Files/Orbit View/OrbitView-1.0.1$ Orbit View/OrbitView-1.0.1/OrbitView
```

Or whatever it is.

Thanks. It made my life easier. :)

---

### Post by wersdaluv on 2007-01-16
I ran the MakeFile inside the extracted folder but I think the software still is not installed. Inside the folder, the files are, "COPYING", "MakeFile," MemAllocLib," "orbitview.c," "PhilipsWebCamLib," README," and "Xtse."

How can I install this?

---

