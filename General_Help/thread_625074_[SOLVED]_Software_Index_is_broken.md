---
title: "[SOLVED] Software Index is broken"
date: 2007-11-27
forum: General Help
---

### Post by Lenois on 2007-11-27
Hi everybody. 

Today I downloaded and installed Frostwire. After the installation and a reboot, Frostwire couldn't start. So after reading some threads I realized Java was not installed. So I ran a command to install Java (got it in one of the threads). After that, Frostwire still didn't work. But now I get a message from the Update Manager : Software Index is broken. 

Now my biggest concern in not to get Frostwire and Java working. I would just like to fix the Update Manager. I am new to Linux so I don't really know that much, but I think this is the Java installation that caused the problem. 

I ran 'sudo apt-get install -f', just like the error message says. This is the output:
```

lenois@lenois:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
lenois@lenois:~$ 
```

There are some other threads where people reported the same problem but their output for the above command was different, so it is not helpful.

Any help will be appreciated greatly. 

Lenois

---

### Post by ajgreeny on 2007-11-27
In a terminal run 
```
 sudo dpkg --configure -a
``` and see if that helps, as the error says.

---

### Post by Lenois on 2007-11-28
ajgreeny

Before posting here I tried that (dpkg --configure -a), but it didn't work. Now I realize that I forgot the 'sudo' in front. So it fixed the problem. Java updated and Frostwire now works. 

Thanks for the help.

---

