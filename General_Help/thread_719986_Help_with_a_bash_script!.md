---
title: "Help with a bash script!"
date: 2008-03-09
forum: General Help
---

### Post by v1cho on 2008-03-09
How can I make a bash script that first copies a file, then runs a command, then after the command has finished copies another file, unmounts a volume and then shuts down my PC? :D

---

### Post by scottro on 2008-03-09
The most straightforward way is to simply put the commands, one after the other into the script.  

Something like

cp file file1
command (whatever)
cp file2 file 3
sudo /sbin/shutdown -h now

The problem is that sudo wil ask for your password unless you edit /etc/sudoers and allow the user running the script to perform the shutdown command without a password. 

There are all sorts of more sophisticated checking mechanisms available, but a script is basically a series of commands.  

Just one example--if you don't want it to copy file2 unless the command definitely completes successfully, you could do

cp file file1
command &&
cp file2 file3

The && at the end means don't continue unless this completes successfully. 

This is all going under the premise that you already know the name of the files that you're going to copy and don't really need any variables.

---

### Post by v1cho on 2008-03-09
> **scottro said:**
> The most straightforward way is to simply put the commands, one after the other into the script.  

Something like

cp file file1
command (whatever)
cp file2 file 3
sudo /sbin/shutdown -h now

The problem is that sudo wil ask for your password unless you edit /etc/sudoers and allow the user running the script to perform the shutdown command without a password. 

There are all sorts of more sophisticated checking mechanisms available, but a script is basically a series of commands.  

Just one example--if you don't want it to copy file2 unless the command definitely completes successfully, you could do

cp file file1
command &&
cp file2 file3

The && at the end means don't continue unless this completes successfully. 

This is all going under the premise that you already know the name of the files that you're going to copy and don't really need any variables.
Thanks you! These &&s were what I really needed, thanks again :)

---

