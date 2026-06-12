---
title: "&quot;Type or namespace name `Gtk' could not be found.&quot; Missing Assembly Reference Issue"
date: 2015-01-26
forum: General Help
---

### Post by bigcfk on 2015-01-26
Hey! I'm trying to install an addin for Tomboy, [Tomboy-Todo]("http://romain.blogreen.org/projects/tomboy-todo/"), and it requires that I compile it but I'm having some issues there.

The instructions say to *cd* into the folder, run *./configure*, then *make*, optionally *make check*, then *make install*, and *make clean* afterwards.

*./configure* and *make check* don't have any trouble, but *make* and *make install* both give me this missing assembly reference error. All of suggestions I've gotten through searching have not helped. Here's the output from the *make command*:

```

kieran@dell:~/Inbox/tomboy-todo-1.0.0$ make
Making all in src
make[1]: Entering directory `/home/kieran/Inbox/tomboy-todo-1.0.0/src'
/usr/bin/gmcs -out:tomboy-todo.dll -target:library -r:/usr/lib/tomboy/Tomboy.exe   -resource:./Todo.addin.xml Todo.cs
Todo.cs(26,7): error CS0246: The type or namespace name `Gtk' could not be found. Are you missing an assembly reference?
Todo.cs(69,44): error CS0246: The type or namespace name `Gtk' could not be found. Are you missing an assembly reference?
Todo.cs(74,46): error CS0246: The type or namespace name `Gtk' could not be found. Are you missing an assembly reference?
Todo.cs(84,32): error CS0246: The type or namespace name `Gtk' could not be found. Are you missing an assembly reference?
Todo.cs(84,52): error CS0246: The type or namespace name `Gtk' could not be found. Are you missing an assembly reference?
Todo.cs(96,48): error CS0246: The type or namespace name `Gtk' could not be found. Are you missing an assembly reference?
Todo.cs(96,68): error CS0246: The type or namespace name `Gtk' could not be found. Are you missing an assembly reference?
Compilation failed: 7 error(s), 0 warnings
make[1]: *** [tomboy-todo.dll] Error 1
make[1]: Leaving directory `/home/kieran/Inbox/tomboy-todo-1.0.0/src'
make: *** [all-recursive] Error 1
kieran@dell:~/Inbox/tomboy-todo-1.0.0$ 

```

Thanks for any help!

---

