---
title: "need help copying a selected file form one drive to another"
date: 2015-09-26
forum: General Help
---

### Post by stevecook on 2015-09-26
Hello.

I am currently running Ubuntu 15. Previously Ubuntu 14. I have a Canon LBP laser printer that has always been a bit flaky to run on Linux. but I have always managed to get it to run up to Ubuntu 14. On Ubuntu 15, however, this has proved impossible. To work around the problem, I have installed an Ubuntu 14 VM inside Virtual-box and have done any printing to my Canon from there via a shared folder with the host machine.

In order to automate/make more efficient this process, I have begun to write a right-click bash script that I can use on any selected file that will send a copy of it to my VM shared folder and then will open the Ubuntu 14 VM with the shared folder open on the desktop ready for me to print it. However, I have hit a problem with the first part of the above procedure.

If I use the following command in my bash script to copy the file, it works only if I am copying from any selected file anywhere inside my main system drive (sda1) to anywhere else in my home folder, it works:

cp $1 /home/stephen/vm-printdocs

However, if I use the same command to copy a currently selected file from an external drive (sdb1) to anywhere in my home folder it does not work.

Because I am using this as a right-click context-menu script, I can't see its output to see what is going wrong. If anyone could tell what is wrong with the command or how I can view its output while it is running so I can work out for my self what is going wrong, I would be grateful. Please do not direct me to the many nautilus scripts with allow one to copy a file to another location by choosing he destination directory. I do not want or need that. I need the file to just go to the one single directory. In this case, one I have called vm-printdocs (the one I am sharing between my Ubuntu 15 host and my Ubuntu 14 VM), which is in my home folder. I just need a simple, one click command and the file will be copied to the specified directory.

---

### Post by stevecook on 2015-09-26
Okay, found a fix. Don't know why it is a fix, but it is:
  I have relocated my vm printdocs shared folder on to my sdb1 drive. Now, if I try and copy a file form anywhere in my sdb drive to this shared folder,  it works. However, it also works if I try and copy any file form my sda  drive to this folder. Someone might be able to explain why it works in  one direction (from sda to sdb) but not the other way around. No matter  though, I got it working

---

### Post by sisco311 on 2015-09-26
> **stevecook said:**
> 
If I use the following command in my bash script to copy the file, it works only if I am copying from any selected file anywhere inside my main system drive (sda1) to anywhere else in my home folder, it works:

cp $1 /home/stephen/vm-printdocs

However, if I use the same command to copy a currently selected file from an external drive (sdb1) to anywhere in my home folder it does not work.



You have to quote the parameter expansion. See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

```
cp "$1" "/home/stephen/vm-printdocs"
```

> **stevecook said:**
> 
Because I am using this as a right-click context-menu script, I can't see its output to see what is going wrong. If anyone could tell what is wrong with the command or how I can view its output while it is running so I can work out for my self what is going wrong, I would be grateful. 

You can redirect the STDERR to a file:
```
cp $1 /home/stephen/vm-printdocs 2> /home/stephen/error.log
```
or both STDERR and STDOUT:
```
cp $1 /home/stephen/vm-printdocs > /home/stephen/error.log 2>&1
```

If you want to redirect the output of the whole output (STDERR and STDOUT) of the script to a file, try something like:
```

#!/bin/bash

exec > "$HOME/output.log" 2>&1

your_commands_here
...

```For more details about redirection see: [http://mywiki.wooledge.org/BashGuide/InputAndOutput](http://mywiki.wooledge.org/BashGuide/InputAndOutput)

---

