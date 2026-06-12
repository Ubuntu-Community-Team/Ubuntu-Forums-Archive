---
title: "GLib-CRITICAL **: PCRE library is compiled without UTF8 support"
date: 2013-10-31
forum: General Help
---

### Post by ahowe42 on 2013-10-31
Hello all from a "*more than noobie, but far far from expert*"

I recently started getting this error message in Octave 3.62 calling a function from the Java 1.2.9 package: *GLib-CRITICAL **: PCRE library is compiled without UTF8 support*.  I found, via pcretest, that my libpcre was still on 8.21 with no UTF8 support. I then followed these instructions [http://www.linuxfromscratch.org/blfs/view/svn/general/pcre.html](http://www.linuxfromscratch.org/blfs/view/svn/general/pcre.html) to compile and install PCRE 8.33. This didn't work entirely as advertised, as I ended up with two sets of pcretest/pcregrep (/usr/bin and /usr/local/bin), and two sets of libpcre*.* (/usr/lib and /lib). Running pcretest from the console got me to the 8.21 version, but if I used the full path /usr/bin/pcretest, I got the expected 8.33. I solved this by overwriting /usr/local/bin/pcretest (and pcregrep) with links to the /usr/bin version. Now, when I run pcretest with no path from the console, it picks up the correct version with UTF8 support.

However, I still get the same GLib critical error; it seems that GLib is still referencing the old version of libpcre.  I would just totally uninstall libpcre then compile and reinstall 8.33, but I'm guessing that's not possible, due to dependencies.

How can I fix this?

Thanks.

---

