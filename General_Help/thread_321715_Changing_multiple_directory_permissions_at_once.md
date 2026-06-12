---
title: "Changing multiple directory permissions at once"
date: 2006-12-19
forum: General Help
---

### Post by Orbit45244 on 2006-12-19
Hello,

I was wondering how I could change the permissions and owner a directory, its subdirectories (the subdirectories go 5 to 6 levels down), and all of their files in as little commands as possible.  I know I would have to use chown and chmod.  I don't want to be sitting at my computer all day entering chmod and chown commands into the terminal to change the subdirectories and all of their files.  Thanks.

---

### Post by aysiu on 2006-12-19
```
sudo chown **-R** username:username /directoryname
``` That will change ownership to *username* for /directoryname and all its subdirectories.

---

### Post by Orbit45244 on 2006-12-19
Will it change the files too?

---

### Post by aysiu on 2006-12-19
> **Orbit45244 said:**
> Will it change the files too?
Yes. It'll change everything inside. That's what the *-R* flag does. You can use that same flag with *chmod*, too, to change recursive permissions.

---

### Post by Orbit45244 on 2006-12-19
Thanks.  Is there any way to dump file permissions to a file, and then have chmod read that file?  Can you do this with chown?

---

### Post by aysiu on 2006-12-19
> **Orbit45244 said:**
> Thanks.  Is there any way to dump file permissions to a file, and then have chmod read that file?  Can you do this with chown?
I'm not sure I know what you're asking.

Do you just want to see what permissions a file already has?

---

### Post by Orbit45244 on 2006-12-19
What I want to do now is be able to use a command that reads file permissions and then dumps code to a file.  Then I could take chmod and have it read that file, and then it will automatically chmod the permissions I want.  For instance:

Dump the permissions to a file:
$chmod --dumppermissions /home/user/permissiondump.permissions

The command would write:
[chmod] /directory 777
[chmod] /directory/directory2 770
to /home/user/pemissiondump.permissions.

Then I could use
$chmod --readpermissions /home/user/permissiondump.permissions
and it would read the file and chmod the appropriate permissions.

Could you do that?  Your help so far will work for now, but pretty soon I expect to have some pretty advanced permissions on the directory and its files, and the directory will totally loose all of the permissions when I use a program I have that destroys permissions when it's used.

---

