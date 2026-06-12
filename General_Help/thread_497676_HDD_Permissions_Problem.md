---
title: "HDD Permissions Problem"
date: 2007-07-10
forum: General Help
---

### Post by txhughes on 2007-07-10
Hey all,

Under Ubuntu 6.04, I used an external, ext 2 formatted hard drive for Fortran programming and although I had the initial beginners problems of setting permissions for the user to write to the drive, it had been working fine. I could compile and run the programs in the terminal window.

I recently installed Feisty 7.04 and now I seem to have lost the ability to execute programs. I have tried chown and chmod to set the permissions and, as far as I can tell the permissions are correct for reading writing and executing. I can read and write files and compile programs, but not execute them. The error that comes up in the terminal (bash) is simply: 

bash: ./ks: Permission denied

Also, root cannot execute either and the following message is displayed:

sudo: unable to execute ./ks: Permission denied

So far I have tried recursively setting permissions, reformatting the drive and resetting file permissions, resetting the user etc. The output of ls -l is currently drwxrwxrwx for all the files, with myself set as the user. Does anyone know of anything else I might try to solve the problem of the non-executing programs? Or, please, can someone point me in the right direction?

Any help would be most appreciated!

Tom

---

### Post by txhughes on 2007-07-13
Just thought I'd post the solution I found in case anyone else experiences the problem. Although the permissions were as they should be for executing programs, the partition was (for some unknown reason) being automatically mounted with the noexec option. I dont know how to change this to automatically mount exec on boot, other than manually mount using the terminal command:

sudo mount <*device*> <*mount point*> -t ext2 -o rw,exec 

If anyone knows how to get Ubuntu to automatically mount the external drive as exec, I'd welcome the input.

Tom

---

### Post by dagnabit dang doohickey on 2007-07-13
Check your fstab file (/etc/fstab). Add "exec" to the mount options section for that partition.

---

### Post by stchman on 2007-07-13
This should help you.  You need to add/edit a line in your fstab.  it may look something like this:


/dev/hda3       /media/storage ext3  auto,defaults,rw  0   0

/dev/hda3 = partition

/media/storage = mount point

ext3 = ext3 file system

auto = auto mount partition
defaults = all users can execute programs
rw = read and write to the partition

Hope this helps.

---

