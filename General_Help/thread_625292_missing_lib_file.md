---
title: "missing lib file"
date: 2007-11-27
forum: General Help
---

### Post by Duroon on 2007-11-27
I am trying to get google earth running on my gutsy install. The error I am getting is this
> /usr/lib32/googleearth/googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

I am a bit new to all of this so not sure what I have to do to get that fixed, any suggestions would be greatly appreciated.

---

### Post by PeterJS on 2007-11-27
Well it looks like you are missing 3d drivers for your system, what graphics card does your system have?

---

### Post by Duroon on 2007-11-28
> **PeterJS said:**
> Well it looks like you are missing 3d drivers for your system, what graphics card does your system have?

I have an ATI mobility radeon x600, I have compiz up and running just fine too. I just double checked and I do have a file named libGL.so.1 but it is a link to libGL.so.1.2. Could that be the problem? Or is googleearth just looking in the wrong spot for libGL.so.1?

---

### Post by PeterJS on 2007-11-28
> **Duroon said:**
> I have an ATI mobility radeon x600, I have compiz up and running just fine too. I just double checked and I do have a file named libGL.so.1 but it is a link to libGL.so.1.2. Could that be the problem? Or is googleearth just looking in the wrong spot for libGL.so.1?


:-| That's no good, that looks like it should work. libGL should be in /usr/lib, but I'm betting that's where it is so that's not really helpful. Are you running 64bit ubuntu by chance?

---

### Post by Duroon on 2007-11-28
Yes I am running 64bit. Think maybe Google Earth just doesn't like 64 bit?

---

### Post by PeterJS on 2007-11-28
That'll do it. Google earth is built for 32 bit systems and is expecting a 32bit GL library, which you don't have, because you have a 64bit GL library.

---

### Post by Duroon on 2007-11-30
I switched over to 32 bit Gutsy and googleearth works fine now, as long as compiz isn't running of course. With the compiz running it flashes between black screen and the google earth image. Of course movies do that too unless you set visual output correctly on the program in use. I can't find anywhere to set the visual overlay to use on google earth though.

---

