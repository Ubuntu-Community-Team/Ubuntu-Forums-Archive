---
title: "Unable to execute any application from /usr/bin"
date: 2014-07-29
forum: General Help
---

### Post by xdeb on 2014-07-29
Hi everyone,
I am unable to execute any file from /usr/bin.
for every app i wanted to execute i got error message failed to execute child process /usr/bin/appname permission denied.
please help in setting right permission for /usr/bin.
Thanks

---

### Post by moore.bryan on 2014-07-29
From a terminal, go to /usr/bin--i.e., "cd /usr/bin"--and check to make sure its files are executable with "ls -l". 

Executable files have an "x" corresponding to who may execute the file in order of identity; that is, the first three letters after "d" correspond to the user--in this case, you--the next three, the group owner of the file; the final three, everyone. 

If *none* of the files in /usr/bin are executable, you'll have to make them such with "sudo chmod +x -R /usr/bin"; "chmod" tells Linux to change the permissions of the files, the "+x" tells it to make them executable, the "-R" switch tells chmod to be recursive--i.e., into the directory and subdirectories--and the location is obvious.

---

### Post by xdeb on 2014-08-01
@moore.bryan thanks for the reply. All the files in /usr/bin folder had execute permission. I just changed the permission of /usr/bin directory to 755 and everything is working fine.I am not sure of default permission. Are these permission safe or we should restrict executable permission to group/owner

---

### Post by Morbius1 on 2014-08-02
Um .....
> ~$ stat -c "%a %n" /usr/bin
755 /usr/bin

/usr/bin should have been at 755 from the beginning so not sure what happened to yours.

---

### Post by moore.bryan on 2014-08-02
Completely agree with Morbius1; your default install should have set permissions at 755. Wonder what went wrong...

---

