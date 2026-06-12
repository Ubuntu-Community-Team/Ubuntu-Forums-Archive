---
title: "Ripping DVDs with MakeMKV"
date: 2023-03-12
forum: General Help
---

### Post by lwalper on 2023-03-12
[FONT=arial]I'd like to begin archiving some of my DVD library to storage. It sounds like MakeMKV is the tool to use, but with my limited knowledge of the command line I'm bumfuzzled with the instructions on the [MakeMKV]("https://forum.makemkv.com/forum/viewtopic.php?f=3&t=224") site. I have (made a backup of my OS) and downloaded and unpacked the two .tar files, but then I come to the command line
```
./
configure
make
sudo make install
```
and am stuck. In that command shouldn't there be a reference to the files that are being installed? -- or do I just navigate to the appropriate folder and enter the given command?[/FONT]

---

### Post by MAFoElffen on 2023-03-12
The instructions are on the same page of the download: [https://forum.makemkv.com/forum/viewtopic.php?f=3&t=224](https://forum.makemkv.com/forum/viewtopic.php?f=3&t=224)

---

### Post by lwalper on 2023-03-12
So, just navigate to the appropriate folder and enter the commands ... I'll give it a try.

EDIT: -- That seemed to work. Great! Thanks.

---

### Post by MAFoElffen on 2023-03-12
???
> 
The application will be installed as "/usr/bin/makemkv".

That is in the default PATH...

You know you have to also have '*libavcodec*' for it to work, right?

---

### Post by lwalper on 2023-03-12
[FONT=arial]> **MAFoElffen said:**
> ???

That is in the default PATH...
[COLOR=#000000]*The application will be installed as "/usr/bin/makemkv". (that's the end result, right?)*[/COLOR]

> You know you have to also have 'libavcodec' for it to work, right?
[/FONT]Yep, that was in the installation instructions. It seems to run OK.

---

### Post by VMC on 2023-03-13
Here's a docker script to use:
[https://hub.docker.com/r/jlesage/makemkv](https://hub.docker.com/r/jlesage/makemkv)

---

