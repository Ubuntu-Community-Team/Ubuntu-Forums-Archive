---
title: "MPlayer-1.0pre7 Woes"
date: 2005-05-11
forum: General Help
---

### Post by Mr Frosti on 2005-05-11
I recently loaded Ubuntu and had issues with MPlayer version 1.0pre7. In case anyone is having a similar problem, let me walk through what did to bypass the issue:

I downloaded the following on (5/11/2005):

MPlayer-1.0pre7.tar.bz2
font-arial-iso-8859-1.tar.bz2
essential-20050412.tar.bz2
Blue-1.4.tar.bz2

My intentions were to compile with a GUI. I setup everything according to [this](http://simpson.mine.nu/debian.html#mplayer)  guide only to have the "make" execution error out with the last lines reading:

"mencoder.c: In function `main':
mencoder.c:1914: Internal compiler error in print_rtl_and_abort, at flow.c:6458
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://www.gnu.org/software/gcc/bugs.html> for instructions.
make: *** [mencoder.o] Error 1"

I am still not able to install 1.0 pre7, however MPlayer-1.0pre6a works wonderfully. I hope this is an isolated event, but this post is here if anyone is having a similar problem.

---

### Post by Mr Frosti on 2005-05-11
Just an update:

"gcc-3.0" causes errors when compiling, so I upgraded to "gcc-3.4" and this seems to resolve the make issue described above.

---

### Post by wwwolf on 2005-05-11
The best walkthru is here: [http://ubuntuforums.org/showthread.php?t=31061](http://ubuntuforums.org/showthread.php?t=31061)

If you follow all the instructions you will get the latest versions of everything that is needed. It works everytime, all the time.

---

