---
title: "libssh2"
date: 2005-07-31
forum: General Help
---

### Post by j0e on 2005-07-31
Is libssh2 available as a debian/ubuntu package? Or even better, available over apt-get?

I've searched for it, but haven't had any luck so far.

The project homepage [1] suggests downloading and installing from source - just wondering if there is a debain package to make my life a lot easier!  :) 

I'm trying to get the secure shell2 functions [2] working in PHP - anyone achieved this? My understanding is that I need to install the necessary PECL extension - but it requires libssh2.

Thanks for any help! R, Joe.

[1] [http://libssh2.sourceforge.net/](http://libssh2.sourceforge.net/)
[2] [http://php.net/manual/en/ref.ssh2.php](http://php.net/manual/en/ref.ssh2.php)

---

### Post by amccausl on 2006-07-17
The same package is required for the Perl ssh2 package to work (Net::SSH2).  I couldn't find a debian package for it, but I did find rpm's ([http://dag.wieers.com/packages/libssh2/)](http://dag.wieers.com/packages/libssh2/)).  If you really don't want to do a source install you can import them to debian with a utility called "alien".  I haven't tested that it works with this package, I'm going to attempt a source install instead.  Best of luck in whatever you decide to do :)

---

