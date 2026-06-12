---
title: "CinePaint 1.3 in Ubuntu 10.04"
date: 2012-12-16
forum: General Help
---

### Post by shelbyvision on 2012-12-16
I managed to get CinePaint installed on my computer, but there are problems that I need help with. It won't open any existing image files. If I go to file/preferences/folders, most of the lines are blank (see screenshot). I don't know where those folders are located. I tried doing a search and it looks like nearly all the cinepaint folders are still in my Downloads folder. The installation apparently left them all there. It seems to me that they should be somewhere else, but I don't know where. Can anyone shed some light on this for me? I'm afraid if I mess with it to much I'll just make matters worse.

---

### Post by ajgreeny on 2012-12-16
How did  you install it?

---

### Post by shelbyvision on 2012-12-16
> **ajgreeny said:**
> How did  you install it?

The .tgz has a file called INSTALL that has these instructions:

CINEPAINT INSTALLATION
[email]Robin.Rowe@cinepaint.org[/email]
2012/03/31 VERSION 1.1

Build and Install from source tarball

tar xvfz cinepaint.1.3.tgz
cd cinepaint
./configure
make
sudo make install
cinepaint

I just noticed in that same file, further down:

ldconfig

CinePaint by default installs its libraries in /usr/local/lib. If CinePaint
fails on launch because it can't find its libraries, you must specify 
where to look using LD_LIBRARY_PATH or ldconfig. With ldconfig, create a
file named /etc/ld.so.conf.d/cinepaint.conf that contains the lib path
/usr/local/lib then sudo ldconfig -v. Alternately, you may set it with
the evironment variable LD_LIBRARY_PATH that may be written in your
profile file.

I can't quite figure out what to do with that.

---

