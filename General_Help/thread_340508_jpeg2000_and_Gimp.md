---
title: "jpeg2000 and Gimp"
date: 2007-01-17
forum: General Help
---

### Post by scott_b on 2007-01-17
I found a jpeg2000 plugin for Gimp:  [http://registry.gimp.org/list?name=jp2](http://registry.gimp.org/list?name=jp2)

But I can't seem to get it installed.  The problem seems to be that it doesn't know where to look for the programs I have.  At first it said I didn't have gcc. So, I did the following: 

sudo ln /usr/bin/gcc-4.0 /usr/bin/gcc 

Maybe that was a huge mistake, but it got me further along in the "make."
Now it fails because it doesn't think I have Gimp.  I have Gimp 2.2.  The output from the command "make" is:

checking for GIMP... configure: error: Package requirements (gimp-2.0 >= 2.2.0 gimpui-2.0 >= 2.2.0) were not met:

No package 'gimp-2.0' found
No package 'gimpui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GIMP_CFLAGS
and GIMP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** [config.status] Error 1

I don't know what the instructions mean, much less how to implement them.  I would appreciate any help.

Or maybe there is an easier way to do this.

NOTE - I have done Imagemagic, but it can't open the jp2 I'm after.

---

### Post by Roobert on 2007-01-19
I'm having the same problem; another post on the forums mentioned that imagemagick was the way to go, but it "can't decode file stream".

I *really * don't want to have to use Windows for this! Are there any other ways to convert this file format?

---

