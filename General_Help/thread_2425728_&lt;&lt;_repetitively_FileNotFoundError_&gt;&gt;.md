---
title: "&lt;&lt; repetitively FileNotFoundError &gt;&gt;"
date: 2019-08-29
forum: General Help
---

### Post by icamps on 2019-08-29
Dear all,

I am using a suite of programs and scripts to do computational simulations in the area of chemistry/structural biology (Schrodinger Suite).

I am facing, repetitively, the error that a given program is not found.

The setup of the suite is just to add to the path the installation directory, as I did.

The problem is:
- When I run the graphical interface (called Maestro), it complains about not finding the scripts.
- When I run the scripts that calls a program, I got the error ```
 FileNotFoundError: [Errno 2] No such program: 
``` (the script is found in the system!)
- When I run the program called by the script, it runs without any issue (the program is found by the system!).

Of course, you can be thinking "then run the program manually". The problem is that there are a lot of input files to prepare that are not well documented in the suite documentations (as it is expected to be used via GUI).

I own the installation folder and it has all the permissions (read, write and execute) active.

Any ideas?

Thanks in advance.

---

### Post by dragonfly41 on 2019-08-29
> 
The setup of the suite is just to add to the path the installation directory, as I did.


This begs the question did you add to $PATH correctly?

Do you see the app path (to executable) in **echo $PATH** command?

On occasions I install apps in /opt/ directory.

---

### Post by icamps on 2019-08-29
Hi @dragonfly41.

Answering your questions: Yes and Yes. 
As I can run the script and programs manually from any directory I am, the PATH is correctly define.

I installed in the directory suggested by the install script.

Camps

---

### Post by TheFu on 2019-08-29
Where you enter helper programs, use the full path to that program. Don't trust the PATH.

---

