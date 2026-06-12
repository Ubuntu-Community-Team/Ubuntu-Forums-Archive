---
title: "shell problems"
date: 2007-08-24
forum: General Help
---

### Post by xGutsAndGloryx on 2007-08-24
I am having a tough time understanding certain aspects of the shell. I was wondering if anyone knows some websites that could assist me?

---

### Post by bernied on 2007-08-24
Which aspects?

Any of these help?

Commands:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

Scripting:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by xGutsAndGloryx on 2007-08-25
i have downloaded some programs that i think work only in the shell prompt... how do i find the command to pull them up?

---

### Post by bernied on 2007-08-25
Usually you would just type the name of the program.
But this only works if it has been installed in a place where the shell will be looking for programs. This is defined by the PATH environment variable. To find out the value of PATH, try:
```
echo $PATH
```
If the program is not in one of the locations in PATH, you need to specify its location to start it. So, if the program was called runme and it was in /home/user, then you could do:
```
/home/user/runme
```
Or, if your current working directory was /home/user, then you would just need to do:
```
./runme
```
The '.' refers to the current directory. (As an aside '..' refers to the parent directory, /home in this case.)

If this still doesn't work, there may be a problem with permissions. To find out the permissions on a file, use 'ls -l'. And [read this](http://www.hostingmanual.net/other/permissions.shtml), because it explains it better than I could.

I hope this helps.

---

