---
title: "Command Line Question"
date: 2007-11-19
forum: General Help
---

### Post by piznimpo on 2007-11-19
I'm trying to search for all instances of a file and then delete them all. I think I know what I'm supposed to type, but I'm not sure if it will delete EVERYTHING in the directory or not. Really i just need someone to tell me if this command would work or not:

find . -name "desktop.ini" | rm *

I know the find command will find all the files I want to remove, but the command after the pipe symbol is what has me worried. Will the command after the pipe only apply to the results of the find command, or would it remove everything in my directory?

---

### Post by nick_h on 2007-11-19
You command will remove everything in the current directory.

What you need is:
```
find . -name "desktop.ini" -exec rm '{}' \;
```

---

### Post by erginemr on 2007-11-19
Be careful!
find . -name "desktop.ini" | rm *

will delete all files!

Another alternative to the above elegant method is:
rm `find -name "desktop.ini" `

Buy using the formula:
command 2 `command 1` 

you can send the result of "command 1" as argument to "command 2".

---

### Post by mali2297 on 2007-11-19
A general advice is to use **rm -i**, then you will be asked for confirmation before  the removal of any file.

---

### Post by Nameless_one on 2007-11-19
Even better, you should add it to your .bash_aliases.

---

### Post by bodhi.zazen on 2007-11-19
> **Nameless_one said:**
> Even better, you should add it to your .bash_aliases.

AND, almost more important, /root/.bashrc

---

### Post by piznimpo on 2007-11-19
Thanks for all the replies! I figured I should ask before using the command 'rm *'. Now I can get rid of all the crap Windows put into my USB drive!

---

### Post by nick_h on 2007-11-19
> **Nameless_one said:**
> Even better, you should add it to your .bash_aliases.

The only problem with adding it as an alias is that you might use another machine and forget that rm doesn't ask for confirmation by default.

Not a bad idea though.

---

