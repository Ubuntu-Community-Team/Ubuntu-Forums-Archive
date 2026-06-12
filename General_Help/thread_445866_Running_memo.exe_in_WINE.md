---
title: "Running memo.exe in WINE"
date: 2007-05-16
forum: General Help
---

### Post by jsladek on 2007-05-16
Memo.exe is a simple date reminder program (I have tried Linux flavors, but all are cumbersome) that I am trying to startup in Sessions.

In terminal (and Sessions start at bootup), if I try the command wine /home/jim/.wine/drive_c/Program\ Files/Memo/MEMO.EXE ..... it does not work.  If I go to terminal and drill down to /Memo, I can execute the program.

It appears to be a path problem, but I have other programs successfully starting via Sessions in wine using the command line that I am try to use for Memo.exe.

Any ideas why it won't work?

---

### Post by taurus on 2007-05-16
When you say it does not work, what is the error message on a terminal when you run that command?

---

### Post by jsladek on 2007-05-16
There is no error message in Terminal.  The prompt comes up for the next line just as if the program had executed, but the Memo GUI does not come up as it does when you drill down and execute from the subdirectory.

Jim

---

### Post by jsladek on 2007-05-17
Case closed ......

The answer to the problem was too obvious and I missed it.  It doesn't run in Windows that way either.  When it runs from StartUp, the link is set to start the program in the subdirectory.  I realized it late last night and wrote a quick and dirty script this morning that changes to the Memo subdirectory and then runs the program.  It works fine.

Jim

---

