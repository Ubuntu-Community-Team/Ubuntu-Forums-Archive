---
title: "Trash Confusion"
date: 2007-10-15
forum: General Help
---

### Post by lonjim2 on 2007-10-15
Hi Everyone,

I think this happened after I updated the kernel when I reformatted my machine to a new Ubuntu install.  For some reason, I have locked system folders like Sudo, Network Manager, HAL, cups and console in the trash.  I didn't put them there and was wondering if anyone might know how to "restore" these files so I can get their entries out of my trash.

I have included a screenshot of the current trash with these files.

Many thanks!

---

### Post by erginemr on 2007-10-15
They are probably residual process id (*.pid) files from your older system. They suspiciously look like process names rather than real files and folders. If your system runs fine, then there is no reason for not to delete them once and for all from your computer.

To do this, you will need to access to these files with root privileges. 
Use 'sudo su' from the console to become root. 
Then 'cd .Trash' to go into the trash directory. 
Make sure that you are in your .Trash directory by checking with 'pwd',
otherwise you may end up with deleting all the files in your home directory.
First check its content with 'ls -a' for a final check before the action.
Delete all files by issuing the command 'rm *'
Delete all sub-directories by issuing the command 'rm -r *'
Give up your root priviliges with 'exit'
Finally, check your trash from the desktop to make sure that it is empty.

---

