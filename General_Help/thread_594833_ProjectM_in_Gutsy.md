---
title: "ProjectM in Gutsy?"
date: 2007-10-28
forum: General Help
---

### Post by IndieRockSteve on 2007-10-28
anyone get ProjectM to compile in Gutsy? I'm trying to compile libprojectm 1.01 but i get this error even with ftgl-dev installed,

> # make
[  2%] Building CXX object CMakeFiles/projectM.dir/projectM.o
In file included from /usr/include/FTGL/FTFont.h:4,
                 from /usr/include/FTGL/FTGLPixmapFont.h:5,
                 from /Storage/local/Tarballz/libprojectM-1.01/Renderer.hpp:25,
                 from /Storage/local/Tarballz/libprojectM-1.01/projectM.cpp:59:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from /usr/include/FTGL/FTGLPixmapFont.h:5,
                 from /Storage/local/Tarballz/libprojectM-1.01/Renderer.hpp:25,
                 from /Storage/local/Tarballz/libprojectM-1.01/projectM.cpp:59:
/usr/include/FTGL/FTFont.h:5:10: error: #include expects "FILENAME" or <FILENAME>
In file included from /usr/include/FTGL/FTFont.h:7,
                 from /usr/include/FTGL/FTGLPixmapFont.h:5,
                 from /Storage/local/Tarballz/libprojectM-1.01/Renderer.hpp:25,
                 from /Storage/local/Tarballz/libprojectM-1.01/projectM.cpp:59:
/usr/include/FTGL/FTFace.h:5:10: error: #include expects "FILENAME" or <FILENAME>
/usr/include/FTGL/FTFace.h:6:10: error: #include expects "FILENAME" or <FILENAME>
In file included from /usr/include/FTGL/FTFace.h:9,
                 from /usr/include/FTGL/FTFont.h:7,
                 from /usr/include/FTGL/FTGLPixmapFont.h:5,
                 from /Storage/local/Tarballz/libprojectM-1.01/Renderer.hpp:25,
                 from /Storage/local/Tarballz/libprojectM-1.01/projectM.cpp:59:
/usr/include/FTGL/FTPoint.h:5:10: error: #include expects "FILENAME" or <FILENAME>
/usr/include/FTGL/FTPoint.h:6:10: error: #include expects "FILENAME" or <FILENAME>
In file included from /usr/include/FTGL/FTFace.h:10,
                 from /usr/include/FTGL/FTFont.h:7,
                 from /usr/include/FTGL/FTGLPixmapFont.h:5,
                 from /Storage/local/Tarballz/libprojectM-1.01/Renderer.hpp:25,
                 from /Storage/local/Tarballz/libprojectM-1.01/projectM.cpp:59:
/usr/include/FTGL/FTSize.h:6:10: error: #include expects "FILENAME" or <FILENAME>
/usr/include/FTGL/FTPoint.h:45: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/FTGL/FTPoint.h: In constructor ‘FTPoint::FTPoint(int)’:
/usr/include/FTGL/FTPoint.h:47: error: ‘ft_vector’ was not declared in this scope
/usr/include/FTGL/FTSize.h: At global scope:
/usr/include/FTGL/FTSize.h:43: error: ‘FT_Face’ has not been declared
/usr/include/FTGL/FTSize.h:102: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTSize.h:108: error: expected ‘;’ before ‘*’ token
/usr/include/FTGL/FTSize.h:113: error: ‘FT_Size’ does not name a type
/usr/include/FTGL/FTSize.h:133: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTFace.h:67: error: expected ‘;’ before ‘*’ token
/usr/include/FTGL/FTFace.h:79: error: expected `;' before ‘const’
/usr/include/FTGL/FTFace.h:93: error: expected ‘;’ before ‘*’ token
/usr/include/FTGL/FTFace.h:103: error: ‘FT_GlyphSlot’ does not name a type
/usr/include/FTGL/FTFace.h:115: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTFace.h:121: error: expected ‘;’ before ‘*’ token
/usr/include/FTGL/FTFace.h:133: error: expected ‘;’ before ‘*’ token
/usr/include/FTGL/FTFace.h:143: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTFont.h:87: error: ‘FT_Encoding’ has not been declared
/usr/include/FTGL/FTFont.h:101: error: expected ‘;’ before ‘*’ token
/usr/include/FTGL/FTFont.h:217: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTFont.h:251: error: ‘FT_Error’ does not name a type
make[2]: *** [CMakeFiles/projectM.dir/projectM.o] Error 1
make[1]: *** [CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2


---

### Post by anparks on 2007-10-29
im absolutely wondering the same thing. i really wish there were .deb packages for projectM...

im getting the following error in gutsy:

```

anparks@anparks-laptop:~/InstallProjectM/libprojectM-1.01$ make
Linking CXX shared library libprojectM.so
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libprojectM.so] Error 1
make[1]: *** [CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2

```

when i try:

make -fPIC

it returns that it doesnt know of a PIC file

---

### Post by IndieRockSteve on 2007-10-29
well, i had to delete the folder and untar the download again and then it worked. weird, but oh well, it's installed now.

I agree though, it would be great to have a package for projectM.

---

### Post by punkrockguy318 on 2007-11-14
yeah a projectm deb would be very nice.  is there anyone out there that would be willing to do that? it would be really appreciated by so many people

---

### Post by puterboy on 2007-11-18
Found a solution. Seems to work only in Amarok...and I have no idea what packages are needed. I just installed every package anyone told me to install lol

Download libprojectm-1.01 and projectM-libvisual-1.0 from the ProjectM site. Google it to find it.

Install the following packages: build-essential, xmms-dev, ftgl-dev, cmake

Find and install the latest versions of: libglibX.X-dev, libgtkX.X-dev, libsdlX.X-dev, liblewX.X-dev, libvisualX.X-dev, and libvisualX.X-plugins (X.X being the latest versions. Don't worry about any earlier version, xmms-dev needs them)

After everything's installed, go into the libproject-1.01 folder, and type:

cmake . -DCMAKE_BUILD_TYPE=RELEASE
make
sudo make install

then go into the projectM-libvisual-1.0 folder, and type the EXACT SAME INSTRUCTIONS

Like I said, I probably installed a lot more packages than I should have, but it's working for me in amarok. there's an mp3 problem, but i don't think it's related. Also, I installed the xmms-projectM before, so I'm not sure if that has any bearing on the solution at all

---

### Post by aganima on 2007-12-25
Thanks Puterboy and EVERYONE else helping me out to get here!
so all day i've been trying to get this working on my AMD 64x2 with nvidia card, and all threads i've found so far have had only partial info mostly addressing x86 issues; however this thread seems to have the main 2 errors.


I found the 2 links below VERY helpful:

[http://ubuntuforums.org/showthread.php?t=249818](http://ubuntuforums.org/showthread.php?t=249818)
[http://ubuntuforums.org/showthread.php?t=623919](http://ubuntuforums.org/showthread.php?t=623919)

-------------------------
my suggestions: 
Follow "puterboy's" instructions regarding the packages that you need installed and use his install instructions, however after doing so, you may still end up with a small error after running make (as "anparks" has mentioned:
************
anparks@anparks-laptop:~/InstallProjectM/libprojectM-1.01$ make
Linking CXX shared library libprojectM.so
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libprojectM.so] Error 1
make[1]: *** [CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2
*************

at this point, visit: [http://ubuntuforums.org/showthread.php?t=249818](http://ubuntuforums.org/showthread.php?t=249818)
and download the "pre-compiled" "ftgl-dev" package because there seems to be an error with the one that you can install from APT! so IF YOU HAVE A x64 machine, you'll have to uninstall your "ftgl-dev" from apt, and use/install the one listed in the link above, and after you've done so, just go ahead and run make, then sudo make install and you're all set! :)))

---

### Post by tremby on 2007-12-30
any chance to see a package? even after the instructions above i'm still having problems. i'd imagine in most cases the potential users of projectM wouldn't have a clue how to begin compiling something, so it'd be really nice to see a package for this.

---

### Post by jordoex on 2008-01-17
It's being put into hardy.

---

### Post by disturbedite on 2008-01-17
its been in hardy for quite a while.  i don't know if its in the repos for the other versions, but why compile it if it is?

---

### Post by lateralchaos on 2008-02-12
I want 1.x!!! not .99!!! I have tried compiling it on gutsy but no luck. I upgraded to hardy, and it was in the repos, but then it broke my wireless!! Either gotta figure out the compile thingy, or wait till.. April?

---

