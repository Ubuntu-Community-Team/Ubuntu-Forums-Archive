---
title: "Temporary files misbehaving"
date: 2008-06-29
forum: General Help
---

### Post by Thesuperchang on 2008-06-29
I recently dual booted Vista with Hardy Heron to use as a programming rig. My specs are as the signature states.

My problem is that when I open or create files, Ubuntu naturally creates a temporary file. Obviously this should be expected, however the problem is that it is not using the temporary files correctly. It's rather annoying. One example is that when I edit some code in gedit and hit save, half the time it will not flush the edited code to the disk. So when I compile my code, I'm really compiling old code! When this occurs, I must close gedit. Not very helpful at all.:sad: Furthermore, these temporary files just seem to linger around and clog up my system, even after I delete the actual files! Surely this isn't the behavior to be expected from Hardy. I do not recall Gutsy ever acting in such an inappropriate manner.

Regards,
C. Anderson

---

### Post by ibuclaw on 2008-06-29
I think that the backup files are actually rather useful.

It means that if I made an error with a script or sourcefile, and I can't find where; or I accidentally delete a portion of the file and knowingly saved it when I shouldn't have (a series of unfortunate events. I know), then I can easily recover it.
```
mv examplefile~ examplefile
```
I'm not sure what you mean when you say that it compiles the tempfiles. Because it shouldn't, and I have absolutely no problem with it here.

But, if you wish to remove them easily, you could always setup an alias inside your .bashrc file.
```
gedit ~/.bashrc
```
And put at the bottom
```
alias clean='find $PWD -name "*~" -exec rm "{}" \;'
```
Then close and reopen a terminal, and type in
```
clean
```
and most temp files will be removed. (emacs uses #name# style temp filenames).

Regards
Iain

---

