---
title: "help with console command"
date: 2017-02-28
forum: General Help
---

### Post by bogy on 2017-02-28
could someone please explain me what this command does?

find /bin -type f -perm /a+x -exec ldd {} \; \

it's got a pipe with sort to sort out the contents, and i see what it does, but i don't understand what it's actually doing, how it's getting it's results ...
i understand it this far:

find files in the directory /bin from the regular type (no dirs, sockets, ...) the permissions should be "all can execute" and the file itself should be an executable and then i come to the ldd {} \; \ part which i fail to understand

i hope you guys can help me out

---

### Post by &amp;KyT$0P# on 2017-02-28
> **bogy said:**
>  then i come to the ldd {} \; \ part which i fail to understand
By default, [FONT=Courier New]find[/FONT] will print out the paths to matching files.  The [FONT=Courier New]-exec ldd {} \;[/FONT] part instructs [FONT=Courier New]find[/FONT] to, instead of printing filenames, run [FONT=Courier New]ldd[/FONT] on every matching file.

For more information, run [FONT=Courier New]man find[/FONT] in your Terminal.

The extra \ on the end is not part of the command.  That just tells the shell that the command continues on the next line.

---

