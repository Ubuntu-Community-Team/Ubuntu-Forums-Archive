---
title: "Use nedit 5.5 on Ubuntu"
date: 2006-10-22
forum: General Help
---

### Post by orel_11 on 2006-10-22
Hi,

I try to run the nedit 5.5 ([www.nedit.org](www.nedit.org)) on Ubuntu 6.0.6.
I copied the nedit file to the homedirectory and type nedit to launch the editor, but got error that the command is not recognized.

I'm new in linux and don't understand why its not work.
I would appreciate if somebody an help me.

Thanks

---

### Post by bettlebrox on 2006-10-22
The command needs to be in your PATH.

PATH is a list of directorys that is searched for commands to run.

If your running nedit from a shell, cd to the directory where U put nedit then put ./ in front of the command.

Have a look at this which explains more about PATH:

[http://www.debian.org/doc/manuals/debian-tutorial/ch-shell.html]("http://www.debian.org/doc/manuals/debian-tutorial/ch-shell.html")

Look for the section titled "6.2 Where commands live: the PATH variable".

---

