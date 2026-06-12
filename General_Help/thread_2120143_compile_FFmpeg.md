---
title: "compile FFmpeg"
date: 2013-02-25
forum: General Help
---

### Post by MRxSNIPES2 on 2013-02-25
I am trying to compile FFmpeg and I get a error. 
this is what it said and i dont know why i am getting this. thanks for any help you may give and if you need more info that i did not add just let me know.

Installing with make install...

========================= Installation results ===========================
Makefile:2: config.mak: No such file or directory
Makefile:49: /common.mak: No such file or directory
Makefile:92: /libavutil/Makefile: No such file or directory
Makefile:92: /library.mak: No such file or directory
Makefile:178: /doc/Makefile: No such file or directory
Makefile:179: /tests/Makefile: No such file or directory
make: *** No rule to make target `/tests/Makefile'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by mc4man on 2013-02-25
Well you have to configure it first, (& actually configure what you want.

Probably better to start over & follow this guide, at least for now.
(believe it's still good for 12.04, read & follow carefully

[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---

### Post by MRxSNIPES2 on 2013-02-26
> **mc4man said:**
> Well you have to configure it first, (& actually configure what you want.

Probably better to start over & follow this guide, at least for now.
(believe it's still good for 12.04, read & follow carefully

[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

that is what i used same site and and it worked now I may have been missing something cos I compiled wine when this did not work. I think it was something called XFIXES was not installed. thanks for the help.

---

