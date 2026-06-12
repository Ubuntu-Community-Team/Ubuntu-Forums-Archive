---
title: "can batch code be writen as a .sh file?"
date: 2008-04-08
forum: General Help
---

### Post by DSdragondude on 2008-04-08
I've got a batch file that i need to compile a .java file (not at the terminal) and I can't run it.

Is there anyway to use the same code but save it as a .sh file?

---

### Post by asbjorne08 on 2008-04-08
You could explain  little bit more around the problem, since it is not that clear what you mean.

If you mean like a batch file from windows/dos (.bat), then you will need to convert the commands a little bit, but usually it is not that difficult.

To make a shell script just put #!/bin/bash on the first line and then the some commands. 

To run it chmod +x shellscript.sh, and then try to start it. (sh shellscript.sh works too)


Hope this helpls.
-- 
a

---

