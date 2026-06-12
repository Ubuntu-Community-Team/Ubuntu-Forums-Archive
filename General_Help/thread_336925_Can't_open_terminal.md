---
title: "Can't open terminal"
date: 2007-01-12
forum: General Help
---

### Post by vahidg on 2007-01-12
Hi,

After running the 'su' command in gnome-terminal a couple of times since it wasn't logging in to root but staying in the current user, my terminal suddenly closed. Since then I cannot use the terminal (gnome-terminal) because it closes almost immediately every time I try to open it. I see 'vahid@ubuntu: ~' in the title but before the command line is given the terminal is gone. I have deleted .bash_history and tried reinstalling gnome-terminal and even Konsole, which shows the exact same behavior. 

Any help would be greatly appreciated!

---

### Post by energiya on 2007-01-12
Press Alt+F2 and run "xterm" . If it works, try running gnome-terminal from it and see if any errors appear.

---

### Post by vahidg on 2007-01-12
Energiya,

The exact same thing occurs. Before I get the command line it closes.

---

### Post by floke on 2007-01-12
You could try uninstalling and reinstalling it from the repos?

---

### Post by vahidg on 2007-01-12
Steve,

I've already tried that. I've tried the reinstall and uninstall/install option, but with no success. None of the terminals (xterm, konsole, gnome-terminal) work...

---

### Post by energiya on 2007-01-12
I can only think of two things:
1. can you login in a terminal? (Alt+Ctrl+F1)
2. try looking in the system logs... maybe something pops there

Sorry, but I can't think of anything else...

---

### Post by vahidg on 2007-01-12
Energiya,


> **energiya said:**
> I can only think of two things:
1. can you login in a terminal? (Alt+Ctrl+F1)


Thanks, good pointer. Well, it appears I cannot log in, neither with root nor with my own user. I just get the login prompt thrown back at me. Do you know where I could find the appropriate logs for tracing this problem? It's a bit difficult finding them without a terminal...

Thanks in advance.

---

### Post by energiya on 2007-01-13
- you can get the system logs from the menu: System > Administration > System Log. 
- you could also try having a look at the System > Administration > Users and Groups and see if something is wrong.
- try rebooting and choose the "recovery mode" option (you should be logined as root), and might be able to use the terminal from there, becouse I think it is a permissions issue (but not sure). 
Searched the forums but I have no ideea what is the exact cause of what is happening to your terminal.

---

### Post by vahidg on 2007-01-14
Hi Energiya,

Thank you for your reply. I managed to change the shell using the 'Users and Groups' application to tcsh, and was able to use the terminal. So the problem is with bash. If I run bash in the terminal now I get the following:

ubuntu:~> bash
bash: setenv: command not found
bash: setenv: command not found
Segmentation fault (core dumped)

I don't know why setenv should be called when I execute bash. I've tried searching for occurences of 'setenv' in order to find out why bash is calling it but haven't found anything useful.

On a possibly related note, gdb doesn't work. I found this after trying to run it on bash. 

ubuntu:~> gdb
Segmentation fault (core dumped)

For now I have my terminal (tcsh) back, but the reason for this problem remains a mystery. So any clues would be appreciated!

Thanks already.

---

