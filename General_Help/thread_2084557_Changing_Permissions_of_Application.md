---
title: "Changing Permissions of Application"
date: 2012-11-15
forum: General Help
---

### Post by Blurred Talon on 2012-11-15
I installed a program the other night with Sudo SU and now I can't get it to run.
I checked the permissions (via right clicking on the program) and root is the only one with access.

How can I change this? I'm a bit of a n00b.

---

### Post by ajgreeny on 2012-11-15
What is the program and where did you get it from, and how exactly did you install it?  I don't understand what you mean by by your statement that you installed with "sudo su".

---

### Post by Blurred Talon on 2012-11-15
Code Composer Studio V5, it's for working with TI Microcontrollers.

The file is downloaded as tar.gz, extracted and installed via a terminal window. When I first opened the terminal, I typed sudo su to give myself root access (which I shouldn't have done).

Now I cannot get the program to load.

---

### Post by searchfgold6789 on 2012-11-15
Ideally, what you would want to do is the opposite of what you did, in this case.
There should be instructions contained in the program's folder that tell you how to uninstall the program. Login as root as you did before with `sudo su' and uninstall the program. Then you can go ahead and install the program correctly. 

If you don't have instructions for uninstalling, can you tell us exactly what commands you have run? You can use the up and down arrows in your terminal to find out. You may have to log in as root (sudo su) to see what commands you ran while logged in as root.

Sincerely,
searchfgold

---

