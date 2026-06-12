---
title: "Problems caused by nvidia drivers (seemingly)"
date: 2006-10-29
forum: General Help
---

### Post by sharperguy on 2006-10-29
Ok, when Edgy was still in beta I upgraded my dapper installation and everything worked really well.

I installed nvidia-glx, and flash 9, and everything worked amazingly.

To begin with a couple of things were buggy, but that went away closer to release time.

Then I suffered a stupid hardware problem where I put a floppy in the drive, the system crashed and some files in my installation became corrupt.

I then reinstalled Edgy with a clean dapper install then upgrade

I then began configuring, inluding installing flash 9b (although from Seveas' repo instead of the .so file), and nvidea-glx , and now I have the following problems:

Flash 9b, is very unstable, at least when playing videos from youtube. It starts playing, but then it gets stuck like a broken cd, sometimes refershing the page stops it, other times i need to close FireFox to stop the noise.

Since i restarted x after running nvidia-xconfig, GDM try's to look up a the human background (a png), and it cant reciognise the file type :S, so it defaults to a no-themed greeter.

Also since i enabled nvidia-glx, HAL refuses to initialise.

This has cased many problems all round.....

](*,)

edit: one more i remembered is that when i click the shutdown button, a window pops up a couple of times and dissapears, and then the shutdown dialogue appears, but without the hibernate option.

---

### Post by sharperguy on 2006-10-29
Can anyone help?

This is really annoying

I removed seveas' package, and installed from the adobe .so file, and flash works a bit better, but still gets stuck often

---

### Post by sharperguy on 2006-10-30
just another update, it was not caused by nvidia-glx becasue i went back to NV and still not working.

---

