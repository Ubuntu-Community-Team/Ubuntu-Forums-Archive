---
title: "Search for string in directory"
date: 2006-12-11
forum: General Help
---

### Post by Burgresso on 2006-12-11
Is there a way to search for a string in every file (either txt, html, whatever) in a directory on the commandline, or  other way?

thanks

burgresso

---

### Post by jeff777 on 2006-12-11
The command you need is called grep.  Type ```
grep --help
``` or ```
man grep
```at the command line to figure out the syntax.

Basically,  
```
grep "penguin" * -n
``` will search all files in the current directory for the word penguin and output the filename and line number.

---

### Post by Burgresso on 2006-12-11
thanks jeff777! I'll try this when I get moment too.

UPDATE:

Thanks! Worked great!

---

