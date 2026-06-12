---
title: "Re-Install of libvpx.so.4?"
date: 2019-02-07
forum: General Help
---

### Post by sdsurfer on 2019-02-07
Ubuntu 18.04

Not an expert by any means and have done due diligence in searching for a solution before asking.

I have a particular program that has run for two years and it ran only last week, yesterday I attempted to run it and get

*error while loading shared libraries: libvpx.so.4: cannot open shared object file: No such file or directory*

Obviously something has changed and attempts to re-install have failed. I can find little on this library other than it is an mmpeg encoding library and can find all other versions EXCEPT 4. Any ideas how I can re-install it?

Output of dpgk gives me

ii  libvpx-dev:amd64     1.7.0-3    amd64        VP8 and VP9 video codec (development files)
ii  libvpx-doc    1.7.0-3     all          VP8 and VP9 video codec (API documentation)
ii  libvpx5:amd64     1.7.0-3    amd64        VP8 and VP9 video codec (shared library)

apt list shows nada

$ apt list libvpx
Listing... Done

Attempted apt-get install, only thing that "seemed to" work without error was wildcard apt-get-install libvpx* (installing libvpx1, libvpx4, etc = "Unable to locate package.") No error, just didn't seem to work.

The forum of the programmer's site for this app is broken, it requires email verification and am not receiving the verify (one of those. :-) ) or I would inquire there.

Can anyone point me in the right direction as to how to get this re-installed?

---

### Post by sdsurfer on 2019-02-07
Not marking as solved but found a "sort of" solution. It may turn out that it breaks other things.

Per the docs here
[https://packages.ubuntu.com/bionic/amd64/libvpx-dev/filelist](https://packages.ubuntu.com/bionic/amd64/libvpx-dev/filelist)

I see the location of /usr/lib/x86_64-linux-gnu/libvpx.so, I copied and added it as  /usr/lib/x86_64-linux-gnu/libvpx.so.4 (so now there are both files.)

The original problem is solved, the program runs, but it's obviously not the original libvpx.so.4 which it very likely removed for a reason (hence may break other stuff.) This program is dependent on it though.

I found lots of other sources for libvpx 3 and 5, but 4 is suspiciously missing, probably for good reason.

---

