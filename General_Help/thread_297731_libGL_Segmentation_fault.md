---
title: "libGL Segmentation fault"
date: 2006-11-11
forum: General Help
---

### Post by guano on 2006-11-11
Hello, I am using Edgy and trying to run a proprietary :( app, called ENVI, for satellite image processing. In Dapper, it used to run fine, but now when I try to run it I get:

```
guano@grohmann:~$ envi
IDL Version 6.2 (linux x86 m32). (c) 2005, Research Systems, Inc.


% Restored file: ENVI.
% Loaded DLM: TIFF.
libGL warning: 3D driver claims to not support visual 0x5b
Segmentation fault (core dumped)
```

any hints? workarounds?

---

### Post by Architeuthis on 2006-11-11
> libGL warning: 3D driver claims to not support visual 0x5b
You are not alone this is a mesa issue, you will unfortunately have to wait untill the version fixing this bug arrives.

---

### Post by girishv on 2007-04-11
Hi,

I too had similar problem and found this solution from a post by dr_death in fedora forums. It worked for me.

before running IDL, reset the libGL to render indirect only

export LIBGL_ALWAYS_INDIRECT=true
idl


# if you want, you can test with a simple plot
IDL> t = randomu(sss,100)
IDL> plot,t


Girish

---

### Post by nhmc on 2007-04-21
Thanks for posting that tip Girish - I can now run IDL in Feisty :)

---

### Post by Nikos.Alexandris on 2007-04-29
I have the same problem... since I upraded to Feisty from Edgy (a few days ago!).

The "export LIBGL_ALWAYS_INDIRECT=true" does not work for me!

Any other hints?

---

### Post by Nikos.Alexandris on 2007-04-29
This is the answer... : [http://www.ittvis.com/services/techtip.asp?ttid=4177](http://www.ittvis.com/services/techtip.asp?ttid=4177)

Have fun!

---

### Post by seyfarth on 2007-06-20
I have envi on Ubuntu 7.04 64 bit.  I can successfully run envizoom and then use "Launch ENVI" from the "file" menu.  This seems like a good solution since I have not reverted to software GL nor older X11 libraries.  It's a little clumsy, but it is quite successful.  It should also be a good clue to the right person about the reason for the segfaults.

Ray

---

### Post by cleardays on 2007-07-18
> **Nikos.Alexandris said:**
> This is the answer... : [http://www.ittvis.com/services/techtip.asp?ttid=4177](http://www.ittvis.com/services/techtip.asp?ttid=4177)

Have fun!

Thanks! !!

---

