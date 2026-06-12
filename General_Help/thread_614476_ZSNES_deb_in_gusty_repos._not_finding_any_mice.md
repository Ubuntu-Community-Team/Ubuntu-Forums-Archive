---
title: "ZSNES deb in gusty repos. not finding any mice"
date: 2007-11-16
forum: General Help
---

### Post by kd7swh on 2007-11-16
The ZSNES binary in the repos. doesn't find any of my mice and thus wont start. Not the Alps pad on my notebook and none of the USB mice I have around work. 

Any ideas why this is the case?

I compiled from source and it finds all of them no problem. The source-build runs like a champ!

Was the deb in the ropos. not built with mouse support?

---

### Post by K.Mandla on 2007-11-16
It's possible that the version in the repos contains some sort of proprietary or licensed software that can't be included. The VICE packages (the Commodore emulator) are the same way; because the Commodore kernel ROMs are still copyrighted, they can't be packaged with the emulator. Compiling it works fine, but the version in the repos is effectively crippled.

I don't know if that's the case for the ZSNES package, but that would be my first guess.

---

### Post by kd7swh on 2007-11-16
I know the game roms are under copyright, (in the case of SNES) but its my understanding that the kernel and or operating system isn't any longer. 

I might be mistaken. Thanks for your response.

---

