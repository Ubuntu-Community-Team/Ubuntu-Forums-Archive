---
title: "Accidentally clear the filesystem permissions"
date: 2007-11-22
forum: General Help
---

### Post by tepegoz on 2007-11-22
hi foks,
I accidentally changed the permissions of the whole filesystem.  What I did is:
chmod -R 700 *
on the root.  So the permissions of the filesystem is corrupted.  Since I didnot enabled root user, I even could not sudo since sudo file permission is also corrupted.  
I rebooted the computer with the live cd and changed everything to 755.  Now I can login to terminal, but since the filepermissions of the configuration files are wrong, I cannot login to gnome yet.  
Is there any way to restore the default file permissions of all the files in the filesystem?

PS: I now learned that I should have been enabled root user.

Thanks in advance

---

### Post by mpierce on 2007-11-22
Danger Will Robinson...

So, let's try to fix it. All the files in the /etc directory are owned by root.root so:

Let's do this from the terminal
   1) sudo -i
   2) sudo chown root.root /etc/*
   3) sudo chmod 755 /etc/*
   4) exit

In case you need to reset the permissions on sudoers, the permissions should be set to:
   1) chmod 440 /etc/sudoers
It is owned by root.root

Hope this helps...

---

### Post by tepegoz on 2007-11-23
Thanks for reply,
I solved the problem, I mean, I converted the file permissions to their previous states as much as possible.  What I did is the following:
1. I booted the system with the live cd and collected the file permissions of the live cd files with "find" command.  
find . -print -printf %m\t > file.txt
2. I then imported this to spreadsheet and generated a long script containining "chmod XXX <file name>" commands for each file in the file system.  I am pretty sure that it is possible to generate this script without spreadhseet, using awk for instance, but I did not have time to learn how to do that.
3. Then run the generated script for the real operating system root.

That is all.  Actually there are some additional files in the real os file system.  I visited them manually.

---

