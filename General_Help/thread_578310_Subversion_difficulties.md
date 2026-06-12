---
title: "Subversion difficulties"
date: 2007-10-17
forum: General Help
---

### Post by Jolly.Tall on 2007-10-17
I finally have v1.4 working fine on a 6.06 server. Apt-get installed v1.3 OK, but I could not get Apache integration working so installed 1.4 from source and it was fine, providing I removed the apt-get package using --purge, otherwise I got a lot of instances of 'expecting 1.4x, found 1.3x' when running svn.

But now I would like to install ViewVC, which requires python bindings, and I'm getting a lot of errors trying to run 'make swig-py'. There seems to be an issue here with Debian?

So  I try to install python-subversion via apt-get, but it lists subversion as a dependency (naturally), but I'm worried it will break my existing installation, as the Dapper version is 1.3. What will happen to my existing installation of /usr/local/bin/svn if I run 'apt-get install python-subversion'?

---

