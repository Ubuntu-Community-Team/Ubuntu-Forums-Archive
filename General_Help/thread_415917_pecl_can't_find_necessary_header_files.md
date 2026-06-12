---
title: "pecl can't find necessary header files"
date: 2007-04-20
forum: General Help
---

### Post by letheology on 2007-04-20
I'm trying to install the pecl svn package, which provides subversion commands to the PHP runtime.

When I run $ sudo pecl install channel://pecl.php.net/svn-0.2, it starts configuring, and breaks with:

checking for svn includes... configure: error: failed to find svn_client.h
ERROR: `/tmp/pear/cache/svn-0.2/configure' failed


So it can't find the svn client header file on my system.  I've checked, it is indeed not there.  I do have subversion installed.

I'm kind of new to Ubuntu, so I'm not sure if there's something special I have to do to get the header files which go with my software.  So is there some way?  

I also tried downloading the tarball from subversion's website and manually dropped it into my /usr/includes.  It was a long show which didn't work.  Can Ubuntu this for me, the right way?

TIA

---

### Post by letheology on 2007-04-20
OK, so I apt-got libsvn1 and libsvn-dev, which I guess weren't already there even though I had the subversion client and server.  Now pecl no longer complains about missing svn_client.h.  Now it's complaining about a missing header file apr.h.  The apache portable runtime, or something.  I've tried apt-getting libapr0, libaprutil1, libaprutil1-dev, libapr1, and libapr1-dev.  So far, nothing seems to get pecl to finish.

Is there some way of finding out what apt-get package can provide a given file?

Thanks

---

### Post by letheology on 2007-04-23
I've read the configure script of the pecl svn package.  It's looking for apr.h in /usr/include/apr-0/apr.h, whereas I only have the file installed at /usr/include/apr-1/apr.h.  I gather that is because this package expects apr 0.x whereas I have a newer apr 1.x installed.  So I downloaded old version and installed manually (does Ubuntu provide a method for having old versions of software installed alongside the latest versions?)

So then the pecl package managed to find the apr library.  Yay!  

Didn't get much further though..  Now I have this error:

In file included from /tmp/pear/cache/svn-0.2/svn.c:39:
/usr/include/subversion-1/svn_utf.h:27:23: error: apr_xlate.h: No such file or directory


I guess I'm going to give up now.  I had this software working on our gentoo box, I think I might try to get the boss to switch.

---

