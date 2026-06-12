---
title: "how to exit from command &quot;source&quot; ?"
date: 2019-04-10
forum: General Help
---

### Post by creatxr on 2019-04-10
how to exit from command "source" ?

if i use "exit" , it will close my shell window.

what's the command exit from "source" and keep my shell window?

thanks.

---

### Post by oldrocker99 on 2019-04-10
CTRL-C will exit a shell-started program.

---

### Post by Holger_Gehrke on 2019-04-10
The behaviour of 'exit' is just as expected, since 'source' executes a script in the **current** shell. There's no specific command to exit from a file executed with '.' or 'source'. You can of course use 'return' if you want to return a specific value from the script, but just running past the end of the file is fine, too.

Holger

---

### Post by creatxr on 2019-04-10
use command "deactivate"

---

