---
title: "Saving Shell Script and/or equivilant to applescript?"
date: 2008-04-20
forum: General Help
---

### Post by Condip on 2008-04-20
Okay two questions...
1. How do i make a shell script (at least i think there called that) and save it to some place like the desktop, so i can double click it and run it when i please.
2. Also is there any Linux equivalents to applescript? For example,could i tell my system to run something, or open something at a cretin time, at cretin intervals? (and do other applescript like stuff?) All help is greatly appreciated!

---

### Post by scragar on 2008-04-20
shell scripts are easy to set up, make an empty text document, and make the first like:
```
#!/bin/bash
```after that make it executable from the properties box and your all done.

I have no idea what applescript is...

---

### Post by mpchlets on 2008-04-20
a shell script is much like applescript, and do run them at an interval you will setup cronjobs in your crontab.

you probably will want to get used to using the terminal, Applications->Accessories->Terminal

There you can type man crontab and learn all about the crontab

to edit your crontab, type crontab -e

and to create a script try vi script.sh.

vi is a good editor, but hard to get used too, and easier one is pico.

you can use any language you want in there, python, perl, php, bash, etc.  The first line gives the interpreter name, #!/bin/bash is for bash scripts, #!/usr/bin/php would run php in most environments.

so you will create your script, save it in your home directory and then add it to your crontab to run whenever.

Good Luck.

---

### Post by Condip on 2008-04-20
I have no idea what you just said but i will give it a try. Can't i just make a plain text document and save it with an extension like .sh or something? And applescript is a mac programming language, that does simple system tasks, but can get mush more complex, and is almost a fully functional language.

---

### Post by scragar on 2008-04-20
the .sh extention doesn't always work(some configs etc don't support it properly), which is the reasoning behind the first line(tells ubuntu what to run the text file in).

---

