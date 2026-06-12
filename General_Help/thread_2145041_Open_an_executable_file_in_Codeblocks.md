---
title: "Open an executable file in Codeblocks"
date: 2013-05-14
forum: General Help
---

### Post by dali1985 on 2013-05-14
I just installed Codeblocks in my Raspberry. I built and run the hello world application and it works. But when I try to open the executable file(with double click) it does not do anything. Or better it does something in stdout but not in a terminal window. I want to open it in a new window. Maybe with the usage of GUI?? I can open it with the command cd and after that ./myfile but how can I do to open it in a window?

---

### Post by TheFu on 2013-05-14
If you want a window around the running of the program, then you need to code that up.  Another option would be to create a tiny shell script that opens a new terminal and launches your program inside it.  The man page for whatever terminal program you use should explain how.

I use xterms - yes, I'm old - according to the man page for xterm, if I run **xterm -e /full/path/to/program**, then it will do what I think you want.

I have no idea what "codeblocks" is and I've never touched a Raspberry except to eat it, so this may not be helpful, but if you are running a version of UNIX or Linux, this should work provided X/Windows is actually available and running. X/Windows is usual the GUI for UNIX systems, though the system may not be running X (that is the shorter, common, name for X/Windows).

---

