---
title: "wine"
date: 2007-01-07
forum: General Help
---

### Post by hostage on 2007-01-07
Hello i just installed WINE

when i was in the terminal an wrote "wine run" then this camed up

[B]anders@anders:~/Desktop$ wine run
wine: creating configuration directory '/home/anders/.wine'...
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
Failed to open the service control manager.
wine: '/home/anders/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\run.exe": Module not found[/B]

dunno what that mean?!

---

### Post by meng on 2007-01-07
It's looking for a file called run on your Desktop. Does such a file exist?

---

### Post by hostage on 2007-01-07
no that does not exist. should it exist on the desktop?

---

### Post by meng on 2007-01-07
No, but why would you pass an argument of "run" to the command "wine" unless you wanted to execute the file "run"?
Syntax:
wine {name of thing you want to execute}

---

### Post by hostage on 2007-01-07
When i installed the WINE deb package and tried to get to the wine folder i could'nt find it at /home/anders/.wine

so after i wroted this in the terminal " wine run" then the WINE hidden folder appeared.

---

### Post by meng on 2007-01-07
You have to invoke the wine command once for the directory to be created (even if you invoke it with the wrong syntax). Thereafter, the directory already exists.

---

### Post by hostage on 2007-01-07
im not so good at english.. okey.. i was just little confused that wine would not work after this message. well im going to try install Warcraft to se if wine is successful installed.

wine: creating configuration directory '/home/anders/.wine'...
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
Failed to open the service control manager.
wine: '/home/anders/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\run.exe": Module not found

---

