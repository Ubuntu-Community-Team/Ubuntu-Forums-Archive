---
title: "unable to burn audio cd from mp3"
date: 2008-04-23
forum: General Help
---

### Post by DarkDancer on 2008-04-23
In Hardy. K3b tells me I have to convert them to .wav files first. Brassero says that it does not have the plug-in required.

---

### Post by logos34 on 2008-04-23
Sounds like you need k3b mp3 decoder or the extracodecs pkg

sudo apt-get install libk3b2-mp3 ubuntu-restricted-extras

---

### Post by DarkDancer on 2008-04-23
I get:

> Package libk3b2-mp3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libk3b2-extracodecs
E: Package libk3b2-mp3 has no installation candidate


---

### Post by DarkDancer on 2008-04-23
ok, got it, I did a search for libk3b2-mp3 in synaptec and found something, installed it and off she goes.... ;)

Thanks logos....

---

### Post by logos34 on 2008-04-24
I just double checked the ubuntu pkg archive and it seems that libk3b2-extracodecs has indeed replaced libk3b2-mp3, like the message says.  So that's the one you want for K3b on Hardy Heron. And hopefully buntu-restricted-extras will get Brasero and ther gnome apps working.

---

### Post by jespdj on 2008-04-24
Please *read* the error message, it says:

[I]However the following packages replace it:
**libk3b2-extracodecs**[/I]

Do what it suggests: install libk3b2-extracodecs instead of libk3b2-mp3.

---

### Post by DarkDancer on 2008-04-25
Actually I have those installed (libk3b2-extracodecs) Brassero still won't burn a music cd, though k3b will. What the search for libk3b2 brught up was the extracodecs.

---

