---
title: "libcurl"
date: 2005-08-10
forum: General Help
---

### Post by michellembrodeur on 2005-08-10
Not sure if this is the right place to post this.

I just ./configure make and make install the new version of libcurl needed for tmw.

But typing curl-config --version still gives the old version. But it all compiled perfectly.

So what do I do to make the kernel or whatever see it. Synaptic still see's the old version.

thanks

---

### Post by baustiech on 2005-08-12
you probably need
./configure --prefix=/usr
make
make install

which would put the files under
/usr/bin/
/usr/lib/
etc

instead of (where they probably went, by default):
/usr/local/bin
/usr/local/lib
etc

as far as shared libs go, i found it convenient to keep on installing to /usr/local/ but then also add /usr/local/lib into /etc/ld.so.conf (followed by running ldconfig); that way, i can keep the distro-installed libs (/lib, /usr/lib) the same while also inserting the new ones.  i've not yet taken the next step, tho, and inserted /usr/local/bin and /usr/local/sbin in my PATH env var prior to the /usr/bin and /usr/sbin...

hih

---

