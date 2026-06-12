---
title: "Can't run from  menu"
date: 2007-02-14
forum: General Help
---

### Post by jrd on 2007-02-14
I installed Kompozer yesterday and I can run it from the run box but not the  menu. I manually put it n the  menu. When I clik the shortcut it don't do anything. I used the exact same command when I put in the shortcut as when I use the run box. Any ideas?

---

### Post by meng on 2007-02-14
What command is that?

---

### Post by jrd on 2007-02-14
I just type "kompozer" and it works.

---

### Post by Maestro23 on 2007-02-14
> **jrd said:**
> I just type "kompozer" and it works.

You need to input the complete path to the .bin file. Probably /usr/bin.

Open terminal:

whereis kompozer (tell you the paths)

Good link to get your feet wet with commands/file structure: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by jrd on 2007-02-14
Thanks for the help. I figured it out. when I typed in "locate kompozer" (nice thing to know about by the way.) It gave my a big list of stuff. I still didn't see anything that looked like a bin file and was related to kompozer. Come to find out the command is "/usr/bin/nvu". I guess that's because it's really the bug free version of nvu. One more question though... If it's under nvu then how did the "Kompozer" command ever work?

---

