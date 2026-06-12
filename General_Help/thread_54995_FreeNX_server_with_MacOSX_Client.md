---
title: "FreeNX server with MacOSX Client"
date: 2005-08-07
forum: General Help
---

### Post by ltmon on 2005-08-07
Hi all,

I am trying to get FreeNX up on my Ubuntu box and have a Mac OSX box login to it.  I have set up FreeNX and can connect to it locally (i.e. running the NX client on Ubuntu).  When I try log in from my Mac I get the following error on connection:

Error: Unable to set TCP_NODELAY (Operation not supported on socket)

If I turn off TCP_NODELAY in the client I get as far as creating a new session, but then it bombs out with the same error.

I have tried enabling and disabling TCP_NODELAY in the nxserver configuration also, with no results.

Any clues?

Cheers,

L.

---

### Post by crashtest on 2005-08-12
There is an open bug report regarding the OS X client:
[http://www.nomachine.com/tr/view.php?id=TR08C00940](http://www.nomachine.com/tr/view.php?id=TR08C00940)

It looks like the OS X client software is "broken" at the moment - at least for 10.4.

---

