---
title: "running a command from java code with sudo"
date: 2013-07-31
forum: General Help
---

### Post by john8 on 2013-07-31
hi if i wanted to run a command from netbeans / eclipise i would use htis code:

Runtime runtime = Runtime.getRuntime(); 
runtime.exec("the code u want to execute in the command line"); 

however if the command needs sudo how does one pass in the password?

---

### Post by beidl on 2013-07-31
Use gksudo instead of sudo for a graphical password input dialog.

---

### Post by codemaniac on 2013-07-31
For obvious security reasons password less sudo is not recommended. However you can set up sudo such a way that it won't require password for certain commands/scripts. 

You can place your commands("the code u want to execute in the command line") in a shell script and let sudo know to run that script without password. 

Type sudo visudo at the terminal to open the sudo permissions (sudoers) file.

add an entry like below in the sudoers file, just below the this line. %sudo ALL=(ALL:ALL) ALL

```
your_username  ALL=(ALL) NOPASSWD: /home/your_username/sudoCommands.sh
```

You can also find more information about sudoers on the below link. 

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by john8 on 2013-08-01
thanks for replys i am ttrying to use gksudo to achieve 
         Runtime runtime = Runtime.getRuntime(); 
         runtime.exec("gksudo commandtorun \npassword \n");
however this doesint pass the password to the gksudo window whats am i doing wrong ? 
thanks

---

### Post by codemaniac on 2013-08-02
you have to change the sudo configuration to let it run without password for a specific command. 
Please read post #3.

---

### Post by codemaniac on 2013-08-02
you have to change the sudo configuration to let it run without password for a specific command. 
Please read post #3.

---

### Post by john8 on 2013-08-03
> **codemaniac said:**
> you have to change the sudo configuration to let it run without password for a specific command. 
Please read post #3.

thanks for reply but the problem is i need to run a command from my code not a bash file, everytime the command runs the code is different so i dont think this would work

---

### Post by john8 on 2013-08-03
ah i use gksudo to run cmd then used robot class to sendkeys to the window on top solved thanks for all replys all very usfull thanks how does one mark thread as solved

---

