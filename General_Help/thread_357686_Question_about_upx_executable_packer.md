---
title: "Question about upx executable packer"
date: 2007-02-09
forum: General Help
---

### Post by Ptero-4 on 2007-02-09
Hi. I heard about an app called upx (a binary packer app) and I wanted to know this.
Can this app be used to pack the entire directory that contains an app (f.e: if I compile firefox in side it`s own directory) so that clicking the compressed binary runs the app and the compressed binary gets a custom icon which shows up in Nautilus and the ¨Applications¨ menu?

---

### Post by nereid on 2007-02-10
As far as I know the only file that will be changed is the firefox executable. I do think that you can also compress libraries.

Following your example, you could install Firefox in your home folder and compress the binary with upx. Then you could add a link in the application menu to your own compressed Firefox installation and start it.

---

