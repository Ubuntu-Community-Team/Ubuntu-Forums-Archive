---
title: "How to boot directly into a specific program?"
date: 2013-02-22
forum: General Help
---

### Post by jamesbeat on 2013-02-22
I have an old laptop that I wish to make into a dedicated Atari ST emulation machine.

I have an emulator lined up, but I'm having trouble figuring out how to get the machine to boot directly into it.
I don't want a window manager at all, the emulator runs without one.

The emulator that I want to use is Hatari, which works with SDL.

Ideally, I would like the machine to boot directly into Hatari, and shut down when I select 'quit' in the hatari menu..

I would have thought that this would be ridiculously simple, but I don't seem to be able to find a way to do it simply and without running a windowing environment?

---

### Post by ersatzsplatt on 2013-02-22
I think ...

you would want to manage your runlevel:
apt-get install rcconf
rcconf

and initiate running a program via changes to /etc/rc* files.

That's where I would start anyhow.

---

