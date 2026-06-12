---
title: "gnome-panel won't compile"
date: 2008-04-23
forum: General Help
---

### Post by vector_prime on 2008-04-23
I've been experiencing a bug where gnome-panel crashes every time I click on the clock applet.  I know it's related to the zimbra connector, and I found an upstream bug report [here]("http://bugzilla.gnome.org/show_bug.cgi?id=520111") with a workaround.

So I pulled the source code and the build deps out of the repos, patched the code, and tried to compile, and it errored out:
```
libtool: link: cannot find the library `/usr/lib/libstartup-notification-1.la' or unhandled argument `/usr/lib/libstartup-notification-1.la'
```

I didn't think anything I'd done could've caused that error, so just to be on the safe side, I redownloaded it and tried to compile the unmodified code.  No dice, same error.

I have libstartup-notification0-dev installed and ls /usr/lib/libstartup-notification* gives me
```
ben@ben-laptop:~$ ls -a /usr/lib/libstartup-notification*
/usr/lib/libstartup-notification-1.a
/usr/lib/libstartup-notification-1.so
/usr/lib/libstartup-notification-1.so.0
/usr/lib/libstartup-notification-1.so.0.0.0
```
but no libstartup-notification-1.la

Any ideas?

---

### Post by mc4man on 2008-04-23
> but no libstartup-notification-1.la Thats in libstartup-notification0-dev , just did a quick compile using dpkg-buildpackage ...., no problems encountered. I'm always adding libs and -dev's so for no great reason I'll run sudo ldconfig every once and awhile. Are you trying to build a package or doing make, make-install ?

---

### Post by vector_prime on 2008-04-24
> **mc4man said:**
> Thats in libstartup-notification0-dev , just did a quick compile using dpkg-buildpackage ...., no problems encountered.
That's odd, I've reinstalled libstartup-notification0-dev 0.9-1 from the Hardy repos and there's no .la file to be found.

> **mc4man said:**
> Are you trying to build a package or doing make, make-install ?
was trying to build a package for myself with
```
./configure --prefix=/usr && make && sudo checkinstall
```
but it won't compile either way without the library.

---

### Post by mc4man on 2008-04-24
sorry I misread that - there is no libstartup-notification-1.la in the hardy (or gutsy) packages. In any event it  compiled fine, where did you get the source ?

---

### Post by vector_prime on 2008-04-24
```
apt-get source gnome-panel
```

---

### Post by mc4man on 2008-04-24
try using either to build
fakeroot debian/rules binary 
dpkg-buildpackage -rfakeroot -uc -b
look at debian/ rules if you need to mod configure

---

### Post by natrixgli on 2008-04-24
This is completely useless with regards to your issue but I just wanted to say hello to a fellow Zimbra user!

When you say Zimbra connector, are we talking Evolution, or just the notifier app (toaster)?

-n8

---

