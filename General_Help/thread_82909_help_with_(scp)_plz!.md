---
title: "help with (scp) plz!"
date: 2005-10-27
forum: General Help
---

### Post by serlex on 2005-10-27
ok im trying to copy a file from my Unix account @University using scp. cant get it to work.

tried

$ scp [email]username@ssh.ee.port.ac.uk:/home/fox/students/name/hello/b143.pdf[/email] Mydocuments

this should connect to my account and copy 'b143.pdf' to Mydocuments folder, right?

but says no such file or directory.

---

### Post by ipn1nj4 on 2005-10-27
from your unix account

scp filename user@host:/~

---

### Post by bogoliubov on 2005-10-27
Hello. I think I've had this problem too. I usually do it like this:
$ scp [email]username@servername.uk:location/file.pdf[/email] Mydocuments

I don't write ":/home...", since I think the path should be from you homedirectory, and the first folder you write should be without the "/".

Bad explanation perhaps, but hopefully you'll get the picture.
Ohh, why don't you try using sftp instead. It's not very good, but better than scp!

Cheers!

---

### Post by serlex on 2005-10-27
university dont use ftp :(, they said i can do it by scp

---

### Post by serlex on 2005-10-27
thanks it worked :)))), i dont wanna start another thread (because it looks like im posting every problem i come across here :( )

problem is i can not edit any files, it says "you are not the owner, so you can not have these persimissions"

any ideas?

---

### Post by Riverside on 2005-10-27
[QUOTE=serlex]thanks it worked :)))), i dont wanna start another thread (because it looks like im posting every problem i come across here :( )

problem is i can not edit any files, it says "you are not the owner, so you can not have these persimissions"

any ideas?[/QUOTE]You cannot edit files on which machine - your machine at home once files have been retrieved from your University account using scp, or files on your University account machine once logged in using ssh?

---

### Post by serlex on 2005-10-27
no, the files on my machine, system files. some times i need to edit them, but cant

---

### Post by Riverside on 2005-10-27
[QUOTE=serlex]no, the files on my machine, system files. some times i need to edit them, but cant[/QUOTE]If they are system files such as those in /etc/, the file ownership will look like:

-rw-r--r--  1 root root 21 2005-10-18 22:05 resolv.conf

In order to edit a file owned by root, you need to edit with root privileges.  The standard way to do that in Ubuntu is to run the following command:
> anthony@trafford:/etc$ sudo gedit resolv.conf
Or substitute your favourite editor, I would use:

> anthony@trafford:/etc$ sudo vi resolv.conf
The use of sudo gives you root privileges needed to edit files owned by root (you will be prompted for your password).  Does this help?

---

### Post by serlex on 2005-10-27
great cheers m8, it works, do i have to do this everytime i wanna edit?

---

### Post by Riverside on 2005-10-27
[QUOTE=serlex]great cheers m8, it works, do i have to do this everytime i wanna edit?[/QUOTE]If you want to edit files owned by root, yes.  To see file permissions and ownership, run command ls -l in the directory concerned.

---

