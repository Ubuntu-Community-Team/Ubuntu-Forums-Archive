---
title: "Installing VMD"
date: 2015-01-28
forum: General Help
---

### Post by matas3 on 2015-01-28
Hello! I've been using ubuntu for, like, 15 minutes (one year ago I made a VERY short course, but remember almost nothing). I need to use a program (VMD), wich I can´t install. The instructions in the pdf are:
.........................................................................................................................................................
To install the pre-compiled Unix version of VMD, then only three steps remain to be done after
you uncompress and untar the distribution.

&#8226; Edit the configure script. If necessary, change the following values:

$install_bin_dir

This is the location of the startup script &#8217;vmd&#8217;. It should
be located in the path of users interested in running VMD.

$install_library_dir

This is the location of all other VMD files. This includes
the binary and helper scripts. It should not be in the path.

&#8226; Next generate the Makefile based on these configuration variables. This is done by running
./configure .

&#8226; After configuration is complete, cd to the src directory and type make install. This will
put the code in the two directories listed above. After this, you just type vmd to begin,
provided that vmd is in your path.
.........................................................................................................................................................
So, I skipped step 1 since i'm OK with the default settings. In step 2, I was able to move to the directory of the "configure" in the terminal. But when I type "./configure", what I get is the following:

LINUXAMD64 OPENGL OPENGLPBUFFER FLTK TK ACTC CUDA IMD LIBSBALL XINERAMA XINPUT LIBTACHYON VRPN NETCDF COLVARS TCL PYTHON PTHREADS NUMPY SILENT ICC

I wouldn´t know wether that's OK or not, but then I type "make install", it says the following:
make: *** No rule to make target `install'.  Stop.

Ah... does anyone have any clue? Thanks in advanced!

---

