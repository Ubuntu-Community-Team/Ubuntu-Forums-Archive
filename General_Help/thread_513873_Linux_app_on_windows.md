---
title: "Linux app on windows?"
date: 2007-07-31
forum: General Help
---

### Post by funnyguyfunnyguy on 2007-07-31
Hi all~

I've been using Ubuntu for a little over a year, and love it; however, I have a windows box and would like to run Alexandria Book Collection Manager on it. I know that I could dual boot, or use VMware, but I was wondering if it is possible to (1) compile the source so I could run it on windows. or (2) maybe there is a program for windows which works similarly to WINE, letting me run a linux app under windows.

Any ideas?

Steve

---

### Post by kroiz on 2007-07-31
colinux

---

### Post by aquavitae on 2007-07-31
Have a look at [http://www.cygwin.com]("http://www.cygwin.com/").  It'll let you install certain linux apps onto windows.  Failing that, you should be able to compile it from source through cygwin.

---

### Post by kroiz on 2007-07-31
> **aquavitae said:**
> Have a look at [http://www.cygwin.com]("http://www.cygwin.com/").  It'll let you install certain linux apps onto windows.  Failing that, you should be able to compile it from source through cygwin.

Unless he is a member of the development team of that application he will not be able to  build it for windows. doing a port is not just a matter of building the source on different platform, it requires code changes.

---

### Post by aquavitae on 2007-07-31
> **kroiz said:**
> Unless he is a member of the development team of that application he will not be able to  build it for windows. doing a port is not just a matter of building the source on different platform, it requires code changes.
I am not a member of the development team, but I have successfully built apps on cygwin before.  It doesn't work for everything, but the whole point of it is that it is to avoid having to change the code, as cygwin is basically a port of linux for windows.

---

### Post by kroiz on 2007-07-31
> **aquavitae said:**
> I am not a member of the development team, but I have successfully built apps on cygwin before.  It doesn't work for everything, but the whole point of it is that it is to avoid having to change the code, as cygwin is basically a port of linux for windows.

Ok so let us be more specific, for this application Alexandria Book Collection Manager it is not practical. also if it was, there would probably already be a port.

---

### Post by aquavitae on 2007-07-31
Ok, I agree in this case.  I didn't realise ABCM was a gnome app.  Kde apps compile easily, but it would take quite a bit of work to get gnome apps working.  Not impossible though cos there is a port of gtk, but certainly not straightforward.

---

### Post by funnyguyfunnyguy on 2007-07-31
Thanks for the advice. I think I will just run VMware Server, because I am by no means capable of altering code to compile this app for windows.

---

### Post by kroiz on 2007-08-01
What about colinux? I used it awhile ago and it works very good. and it is not that hard to set up.

---

