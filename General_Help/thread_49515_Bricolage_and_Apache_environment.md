---
title: "Bricolage and Apache environment"
date: 2005-07-16
forum: General Help
---

### Post by jimcooncat on 2005-07-16
I installed Bricolage, and apache/perl/postgres content management package using these instructions from their wiki:

> There is also an experimental Debian package for Bricolage 1.8. To install it, add these lines to your /etc/apt/sources.list file:

# bricolage

deb [http://tetsuo.geekhive.net/mark/debian/unstable](http://tetsuo.geekhive.net/mark/debian/unstable) /

deb-src [http://tetsuo.geekhive.net/mark/debian/unstable](http://tetsuo.geekhive.net/mark/debian/unstable) /

Then do this (as root):

apt-get install bricolage-db

apt-get install bricolage

BUT you need to export LD_LIBRARY_PATH so apache-perl can find some required libraries. export LD_LIBRARY_PATH=/usr/lib/perl5/auto/libapreq/

/etc/init.d/bricolage_cms start  So that works great, but I have to set the environment manually when I start it up using bric_apachectl.

Any clues where I can set this environment variable so this will work with init.d?

---

### Post by jimcooncat on 2005-07-20
Guess I won't be using this after all, so please disregard. Switching to Drupal.

Oh yeah, Ubuntu Rocks!

---

