---
title: "aliases and completion"
date: 2008-06-21
forum: General Help
---

### Post by manfer on 2008-06-21
I explain it with an example. If I type:

prompt:~$ **sudo apt-get install pdf**

and now press TAB TAB, bash gives me the possible completions:

pdfcrack    pdfcube     pdfedit     pdfjam      pdf-reader  pdftk       pdftohtml   pdftoipe    pdfviewer   pdf-viewer

Now I create an alias for that particular command:

alias aptInst='sudo apt-get install'

And if I type:

prompt:~$ **aptInst pdf**

then TAB TAB and completion doesn't work.

I know for most commands and most aliases all works fine, completion still works on aliases, but in this particular case, and I suppose there are more cases out there, completion is not working on the alias.

Is there a way to make completion work in this particular cases?

---

### Post by twbks on 2008-06-21
There is a way, but as I understand it differs depending on which shell you are using.  

For example using *bash*, you will need to define the completion using the *complete* builtin.  I have not done this, so the only help I can give is to read the man page for bash focusing on the *complete* builtin and the **Programmable Completion** section.

---

### Post by sdennie on 2008-06-21
These alias come from /etc/bash_completions.  I believe completions are keyed off the command as written on the command line so its not possible for it to know that your alias is "apt-get install".  However, this might help you: [http://ubuntuforums.org/showthread.php?t=733397](http://ubuntuforums.org/showthread.php?t=733397)

---

### Post by manfer on 2008-06-21
Thanks for pointing me to the solution. I will try to understand all that.

---

