---
title: "Auto Clear terminal on startup"
date: 2007-09-20
forum: General Help
---

### Post by xrdguy on 2007-09-20
Hello People. 

I have a problem with terminal. whenever I open the terminal it gives me this list of message. 

bash: export: `CHANGELOG~': not a valid identifier
bash: export: `configure~': not a valid identifier
bash: export: `DEVELOPERS~': not a valid identifier
bash: export: `ejourn.kateproject': not a valid identifier
bash: export: `empty.bmp': not a valid identifier
bash: export: `ex.xml~': not a valid identifier
bash: export: `gui_io.c': not a valid identifier
bash: export: `ID~': not a valid identifier
bash: export: `imagetmp.c': not a valid identifier
bash: export: `journal.conf': not a valid identifier
bash: export: `Makefile~': not a valid identifier
bash: export: `Makefile.old': not a valid identifier
bash: export: `Makefile.win': not a valid identifier
bash: export: `Makefile.win~': not a valid identifier
bash: export: `oldcode.bak': not a valid identifier
bash: export: `oldcode.bak~': not a valid identifier
bash: export: `prefDialogue.h.bak': not a valid identifier
bash: export: `prefix.c': not a valid identifier
bash: export: `prefix.h': not a valid identifier
bash: export: `pref.tmp': not a valid identifier
bash: export: `README~': not a valid identifier
bash: export: `test.c': not a valid identifier
bash: export: `test.c~': not a valid identifier
bash: export: `test.xml': not a valid identifier
bash: export: `test.xml~': not a valid identifier
bash: export: `threads.c': not a valid identifier
bash: export: `threads.h': not a valid identifier
bash: export: `CHANGELOG~': not a valid identifier
bash: export: `configure~': not a valid identifier
bash: export: `DEVELOPERS~': not a valid identifier
bash: export: `ejourn.kateproject': not a valid identifier
bash: export: `empty.bmp': not a valid identifier
bash: export: `ex.xml~': not a valid identifier
bash: export: `gui_io.c': not a valid identifier
bash: export: `ID~': not a valid identifier
bash: export: `imagetmp.c': not a valid identifier
bash: export: `journal.conf': not a valid identifier
bash: export: `Makefile~': not a valid identifier
bash: export: `Makefile.old': not a valid identifier
bash: export: `Makefile.win': not a valid identifier
bash: export: `Makefile.win~': not a valid identifier
bash: export: `oldcode.bak': not a valid identifier
bash: export: `oldcode.bak~': not a valid identifier
bash: export: `prefDialogue.h.bak': not a valid identifier
bash: export: `prefix.c': not a valid identifier
bash: export: `prefix.h': not a valid identifier
bash: export: `pref.tmp': not a valid identifier
bash: export: `README~': not a valid identifier
bash: export: `test.c': not a valid identifier
bash: export: `test.c~': not a valid identifier
bash: export: `test.xml': not a valid identifier
bash: export: `test.xml~': not a valid identifier
bash: export: `threads.c': not a valid identifier
bash: export: `threads.h': not a valid identifier

I tried clearing it and it did. i removed previous command history but still invain. I can use command clear in terminal and it clear up but when i close terminal and again open it then it still shows these crap at start. I have recently installed ejourn and problem started after that, however, ejourn is working fine. any suggestion.

---

### Post by jamvegan on 2007-09-20
I would suggest checking your ~/.bashrc, ~/.bash_profile and/or ~/.profile files to see if there is anything in them that appears to be related to the messages you're getting.  I have no idea what ejourn is, but perhaps its setup changed one of these files (which is where I would expect to find export commands).

---

### Post by Wolki on 2007-09-20
> **xrdguy said:**
> 
I tried clearing it and it did. i removed previous command history but still invain. I can use command clear in terminal and it clear up but when i close terminal and again open it then it still shows these crap at start. I have recently installed ejourn and problem started after that, however, ejourn is working fine. any suggestion.

Either that install or one of your manual changes messed up your bash settings (I'll just assume your shell is bash, if you changed that tell me). The error is very likely in one of the directories jamvegan mentioned, looking at the error messages it's probably an "export *" or something similar. If you can't find the error yourself, feel free to post these files here so we can take a look at them.

---

