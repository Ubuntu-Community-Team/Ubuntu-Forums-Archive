---
title: "Matlab compiler on Ubuntu Edgy Eft"
date: 2006-11-22
forum: General Help
---

### Post by garton on 2006-11-22
Anyone here who runs Matlab and specifically the matlab compiler on Edgy Eft? I have problems getting this thing to run, this is I've created a shared lib
with the matlab and subsequently written a small app that uses my lib.
When I compile the app I get this error message:

/usr/bin/ld: warning: libstdc++.so.5, needed by
/usr/local/matlab/bin/glnx86/libmwmclmcrrt.so, may conflict with
libstdc++.so.6

And then, when I try to run my small test program (whose main() only
does return 0;) I get this error:

./libmysmalltestapp:
/usr/local/matlab//bin/glnx86/../../sys/os/glnx86/libgcc_s.so.1:
version `GCC_3.3' not found (required by /usr/lib/libstdc++.so.6)
./libmysmalltestapp:
/usr/local/matlab//bin/glnx86/../../sys/os/glnx86/libgcc_s.so.1:
version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

I've looked around for solutions to this for a few hours, but I don't
get any wiser... any ideas?

This is Matlab 7.0.0.19901 (R14). (Old, I know, but it's what I've got.)

---

### Post by taurus on 2006-11-22
Looks like it wants to use an older library!  I think I have seen this kind of error message before from Wolfram's forums!  May want to check out there then...  Otherwise, you can e-mail them and I am sure they will either tell you how to fix it or redirect you to where to look up for help.

In the meantime, you need a gcc compiler for your machine...

```
sudo aptitude install build-essential
```

---

