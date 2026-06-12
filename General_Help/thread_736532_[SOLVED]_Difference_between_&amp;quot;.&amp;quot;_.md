---
title: "[SOLVED] Difference between &amp;quot;.&amp;quot; and &amp;quot;./&amp;quot;"
date: 2008-03-26
forum: General Help
---

### Post by spupy on 2008-03-26
Normally, when i want to run a script in bash from the current directory, i do:
```
./script.sh
```

I noticed however that I can do
```
. script.sh
```

The result is almost the same - the script is executed.
**Almost** the same. Lets see this script:
```
#!/bin/bash
df /home/uibxn | grep -o -e '[0-9]\{1,2\}%'

```
It just prints the % of used space on my home partition. If I run this script with "./", it says something like "32%". If I run the script with "." only, the output is the same, but it is colored, as grep colors it if I run the grep command manually.

What is the difference here? Anyone care to explain?

---

### Post by monraaf on 2008-03-26
In the second case you are using the . as the 'source' command.

It basically means  to read the script in the current shell. This also
means that it doesn't work with python scripts or any other non-shell
script or executable.

See also bash(1)

---

### Post by keratos on 2008-03-26
"." runs it within your shell and environment which means current shell environment variables and settings are available and can be updated.

"./" is just a full path qualifier to an executable (beit script or ELF) which potentially runs in the current process and the "#!" line (if there is one) tell the shell how to execute the script.

The key is "potentially". the first form will ALWAYS run in the current shell, the second...may not

```

# man sh

```

---

### Post by nick_h on 2008-03-26
Typing the path and name of a shell script will run it in a new shell environment.  If the path is listed in the PATH environment variable then the specifying the path is not necessary.  In this case the "." refers to the current directory.

In your second example the "." is equivalent to the builtin shell command, *source*.  This command runs the contents of the file in the current shell environment.

The difference is between running the script in a batch or an interactive shell environment.

---

### Post by spupy on 2008-03-26
Thank you! Your explanations were very helpful!

---

