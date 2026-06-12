---
title: "Command 'sudo' is available in '/usr/bin/sudo'"
date: 2018-10-07
forum: General Help
---

### Post by ibrahim.khan on 2018-10-07
Hello respected members
Recently I have frustrated situations. Suddenly something happened to my Ubuntu operating system. Whenever I type any kind of command it says that specific command is available in '/usr/bin/' 
For example when I type ```
sudo apt-get 
``` it says that 
```
Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
```
I cant use any command.
So I searched for the solution, someone mentioned that type ```
export PATH=/usr/bin:/bin
``` in terminal, this solves the problem but not permanently, because when i open terminal again, so the same situation occurs, I dont know what to do. Please someone help me to solve the problem.
Thanks

---

### Post by &amp;KyT$0P# on 2018-10-07
Normally in Ubuntu, that part of [FONT=Courier New]PATH[/FONT] is set by this line in [FONT=Courier New]/etc/environment[/FONT] -
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```
Does your [FONT=Courier New]/etc/environment[/FONT] have this line?

If yes please post the contents of your [FONT=Courier New]~/.bashrc[/FONT] and your [FONT=Courier New]~/.profile[/FONT]

---

### Post by Impavidus on 2018-10-07
There's something wrong with your PATH. You should still be able to run commands, provided you use the full path to the command.

Let's see what your PATH currently is:```
echo $PATH
```(That command should run, as echo is a shell build-in, although available as separate program too.)

And let's see if you have some wrong redefinition of your PATH somewhere in .bashrc, or something wrong with its normal definition in /etc/environment:```
/bin/grep PATH .bashrc /etc/environment
```

BTW, which version of Ubuntu do you use?

---

