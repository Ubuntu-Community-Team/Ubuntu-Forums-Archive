---
title: "Trouble compiling libpng"
date: 2007-01-03
forum: General Help
---

### Post by ionophore on 2007-01-03
Hey everyone,

I am having trouble ./configuring libpng (version 1.2.14, the latest at the time of this writing).  The configure script claims that it can't find zlib.  I have downloaded and compiled zlib (latest version, configure, make, make install) with no errors.  

The error given by the configure script is:
"configure: error: zlib not installed"

Here is how my directories look:

/home/ben/local/zlib
                         zlib files...
                       /include
                         a directory that zlib made upon make install
                       /libpng-1.2.14
                        libpng files...

There is a readme that comes with libpng that says to put the zlib directory at the same level as the libpng directory (this is what I have done - see above).  

Last thing:  I configured both packages like this:
./configure --prefix=/home/ben/local

(I know that these packages are available through the repos but for reasons that I do not want to go into I would rather not do it this way.)

Any help is greatly appreciated.  Thank you,

-Ben

---

