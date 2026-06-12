---
title: "Server OS change: is it possible?"
date: 2014-06-20
forum: General Help
---

### Post by john205 on 2014-06-20
I have an HP mediasmart server that has outlived its usefulness since all my machines now run ubuntu. I plan on hosting a website with it, but I want  to check a few things so I don't hose the thing. Is it remotely possible to install Ubuntu server onto it? And if it is, will the server boot to the new server OS? I mean, does HP make their mainboards accept only their software?

Before replying: Yes, I know there's no "real" way of doing it, but I am able to disassemble the sever. That way, I can take the hard drive and install ubuntu on there.

Didn't really know where to stick this one. Mods, move as you wish.

---

### Post by nerdtron on 2014-06-20
Is this your server? [http://en.wikipedia.org/wiki/HP_MediaSmart_Server](http://en.wikipedia.org/wiki/HP_MediaSmart_Server)

If it can boot from a USB or CD drive, then I don't see anything special on it that would stop you from installing Ubuntu server.
If the server comes with its own RAID controller, you might need to configure that first before installing Ubuntu.

---

### Post by john205 on 2014-06-20
Different model, and no CD drive. I am able to pull the HDD. May I install it that way?? I've done similar things before. will check thread in morning.

---

### Post by nerdtron on 2014-06-21
Why not use USB to install Ubuntu? But taking out the hard drive and installing the OS on another computer should also work too (unless there would be RAID controllers on the HP, it might cause a problem).

---

### Post by john205 on 2014-06-21
There's 0 display outputs, and it's a single drive. So I'll just rip the drive out and go from there.

---

### Post by john205 on 2014-06-21
Yes, it worked! A few issues but those are aesthetic things like diagnostic lights that only worked wit the original OS.

---

