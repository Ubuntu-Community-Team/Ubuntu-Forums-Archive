---
title: "text editor"
date: 2018-06-21
forum: General Help
---

### Post by idkwhatimdoing1.0 on 2018-06-21
Hello, I seem to have a problem with text editor. For some reason whenever I open a text file that is big it starts to load it, so far no problem however at a certain point usually near the end it stops completely and then my computer crashes... And I have to forcefull shut down my computer... I don't really think its my hardware that is an issue as I have 16gb of RAM and i7 7thgen intel processor and some pretty decent graphics... My computer is always fast and doesnt have a problem when I open a large text file in widnows, however in Ubuntu 18 it seems to not work. For example just a text file that is 666.5 MB will make the computer crash... can anyone help?

---

### Post by dragonfly41 on 2018-06-21
I have never opened a text file that size.
But digging around found some advice here.

[https://askubuntu.com/questions/28847/text-editor-to-edit-large-4-3-gb-plain-text-file](https://askubuntu.com/questions/28847/text-editor-to-edit-large-4-3-gb-plain-text-file)

Perhaps joe editor?

---

### Post by vanadium on 2018-06-23
You probably use gnome and it is indeed the standard gedit editor that does not cut it. I tested a bit with a 1.5 GB text file. Vi does it without problems. Editing does not show any slowdown. Takes three seconds to load, a few seconds to save (an SSD drive). Leafpad loads the file in about 15 seconds, file can be navigated and edited easily, saving takes about 20 seconds and the OS thinks it is frozen. After that: all fine. Search-replace is a different matter - still going on for several minutes and memory usage increasing - at 11.4 already (probably the"undo") [edit]Had to abort as also the swap was getting close to 100% [/edit]. Nano also loads the file in a reasonable amount of time. Inserting a line shows a tiny (less than half a second) delay. Gedit takes ages to load - after more than a minute and loading not at 50%, I aborted.

I also have 16 GB Ram. It all happens in RAM. Nano for example uses 4.5 GB RAM. With limited RAM, the system will use swap, and it will also become unworkable with these editors that do cut it with these large files.

---

