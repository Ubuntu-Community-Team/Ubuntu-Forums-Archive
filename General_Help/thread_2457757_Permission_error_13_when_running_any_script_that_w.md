---
title: "Permission error 13 when running any script that writes to disk"
date: 2021-02-08
forum: General Help
---

### Post by hsweet2 on 2021-02-08
The backstory: I want to run a script from systemd that writes a small bit of information to disk at startup (not to a log).  It generates a permission  error and dies. 

So, I tried to simplify the problem to the point of just running the simplest possible script ```
echo "Some text" >> file
```  from the command line.  It runs when I am in my home folder, but I get the same error, as the same user if I run it from /etc/.

Same issue with an equivalent perl script.

The file permissions are all the way down to 777.

---

### Post by TheFu on 2021-02-08
>  The file permissions are all the way down to 777. 
I hope not!!!  Doubt a system would boot.

Learn Unix permissions a little deeper.  The userid that a process runs as is the permissions that matter.  Generally, systemd units should run as root, so the only way they can't write somewhere would be if the file system were mounted read-only. That's a vast generalization. Exceptions exist.
Make the "file" write to /tmp/. 
Never asume a 'pwd' in any script. Fully specify all file and directory locations for all commands, inputs and outputs.

---

### Post by Impavidus on 2021-02-09
A command like```
echo "text" >> file
```will append some text to a file. It needs write permission on the file. Further, if the file doesn't exist, it will create the file, for which it needs write permission on the directory. So check permissions on the directory too. But don't change permissions on /etc.

---

