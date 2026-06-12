---
title: "Installing stuff into home dir"
date: 2006-08-09
forum: General Help
---

### Post by tawsi on 2006-08-09
Often at times I'd like to be able to test new versions of software without interfering with other users' ability to use the computer. Currently to do this I'm having to set environment variables depending on the particular language the program is written e.g library search paths for c,c++ and pythonpath for python. 

Is there any way of simplifying this other than setting each variable via the login script or some particular place in my home dir I can install to that will be searched by configure and the like?

---

### Post by llamakc on 2006-08-09
You could use vmware to run an Ubuntu install where you test out anything you want and it would have no effect on other users.

---

### Post by tawsi on 2006-08-10
Thanks, but I was more looking for a way to run them for an extended period of time on the normal before installing them for others. For the most part I've been able to do this but the makefiles for kde applications often want to install stuff all over the place even when certain prefixs are specified.

I guess I could get around it using something like unionfs but I was hoping I was just missing something simple. Such as a default search path for includes and libs in home directories, or an environment variable specifying an alternative root to be searched before the normal root so that I don't need to duplicate everything.

---

### Post by llamakc on 2006-08-10
Build a chroot.

---

### Post by tawsi on 2006-08-10
Thats the current plan, to try and use UnionFS (via fuse if possible) and an overlay I can write to. I was just hoping there was a more straight forward method that I was missing.

In general how do people who are working on the applications and libs test new versions without overwriting the default ones?

---

