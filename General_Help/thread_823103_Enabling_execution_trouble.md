---
title: "Enabling execution trouble"
date: 2008-06-08
forum: General Help
---

### Post by symbol86651 on 2008-06-08
Hi, I am trying to enable execution of airoscript....
the instructions say to make the file executible, type in the terminal
"chmod -x airoscript.sh"
When I do, it comes back with the message 
"chmod: cannot access `airoscript.sh': No such file or directory"
I currently have the file "airoscript.sh" on my desktop
                           Any help would be greatly appreciated.....

---

### Post by HalPomeranz on 2008-06-09
A couple of things:

1) The command to make your program executable is "chmod +x airoscript.sh" (notice that's "+x" not "-x")

2) Your executable path probably doesn't include your Desktop directory when it's looking for programs that can be run.  Instead give an explicit pathname when running your program:  "~/Desktop/airoscript.sh" (or just "./airoscript.sh" if you're already in your Desktop directory)

---

