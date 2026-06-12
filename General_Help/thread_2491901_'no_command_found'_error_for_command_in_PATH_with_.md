---
title: "'no command found' error for command in PATH with proper permissions 22.04 LTS"
date: 2023-10-25
forum: General Help
---

### Post by lmpeiris on 2023-10-25
I have created a shell-script based command called 'fc' at /usr/bin/fc, which is in user PATH. Requirement is for the command to work 'fc<arg>' form without giving full path, but it doesn't work. Is this apparmour at work?

Script is not calling any sudo required commands / files from inside

I have given the outputs below.

> uname -a
Linux VM-jhags 6.2.0-1011-azure #11~22.04.1-Ubuntu SMP Wed Aug 23 19:26:19 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

> fc list
-bash: fc: no command found

> ps -p $$
PID TTY TIME CMD
1461288 pts/0 00:00:00 bash

> which fc
/usr/bin/fc

> ls -lht /usr/bin/fc
-rwxr-xr-x 1 root root 5.9K Oct 25 06:31 /usr/bin/fc

> bash fc list
(works as expected)

> sudo fc list
(works as expected)

> /usr/bin/fc list
(works as expected)

> sudo apparmor_status
apparmor module is loaded.
32 profiles are loaded.
32 profiles are in enforce mode.
.....
.....

---

### Post by Holger_Gehrke on 2023-10-25
Try 'type fc' in a shell. There is a shell built-in named 'fc' that is a way to access the command history. If a command contains no '/' the shell first looks for a shell function, then for a built-in, and then it looks for external commands. So when you call 'fc list' the shell runs its built-in 'fc' to search history for a command starting with list and then tells you that it hasn't found anything.

Holger

---

### Post by lmpeiris on 2023-10-25
thanks. this worked. i changed name of the command :P

---

