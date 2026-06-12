---
title: "Error about missing libSDL file..."
date: 2007-09-29
forum: General Help
---

### Post by phatty420 on 2007-09-29
Hello everyone.

I am having a problem running OpenBOR for linux.  I have everything I need to run it but when I run the command I get this error:

```

error while loading shared libraries: libSDL_gfx.so.0: cannot open shared object file: No such file or directory
 
```

I looked in my usr/lib directory and I have a few libSDL_gfx.so files but none of them are libSDL_gfx.so.0 .... I have:

libSDL_gfx.so
libSDL_gfx.so.4
libSDL_gfx.so.4.9.0

Does anyone know what my problem is, or how to fix it?

Thanks in advance for any help.

---

### Post by jordanmthomas on 2007-10-01
```
sudo ln -s /usr/lib/libSDL_gfx.so /usr/lib/libSDL_gfx.so.0
```
should do the trick.

---

### Post by phatty420 on 2007-10-01
Ok man that worked for that error, thanks alot!!  Now I'm getting this error when it runs:

```
Segmentation fault (core dumped)
```

Any ideas???

---

### Post by jordanmthomas on 2007-10-02
I'm not sure why it would dump its core.  Did it leave a dump in your home directory?  Maybe you should send it to the people who make OpenBOR.

**edit** I suppose it could conceivably be an incompatibility with your version of libsdl_gfx that you symlinked.

---

### Post by phatty420 on 2007-10-02
Is there any way to reverse this to back to the way it was before?  To undo the symlink?

---

### Post by jordanmthomas on 2007-10-02
yeah
```
sudo rm /usr/lib/libSDL_gfx.so.0
```

---

