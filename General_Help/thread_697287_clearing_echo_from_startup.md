---
title: "clearing echo from startup"
date: 2008-02-15
forum: General Help
---

### Post by jaikat on 2008-02-15
hello all

I've used the echo command to make sound work on my built in sound card when playing games that won't recognize it "the sound card", in the following manner

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss (the file et.x86 is for enemy territory)

but now i have another sound card and i want to remove the previous "echo" command from executing at startup.. but unfortunately i don't know how to do that..

i appreciate the help..

---

### Post by Sudz on 2008-02-16
You need to edit that line out of whichever startup file you added it to.

You can check files with a quick ```
grep /proc/asound/card0/pcm0p/oss *
``` in the directory where you made the change.

There might also be output telling you what file is being run, but I'm not sure where you would have added that command.

---

