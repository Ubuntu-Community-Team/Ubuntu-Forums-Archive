---
title: "Help needed! Error: Permission denied"
date: 2018-11-14
forum: General Help
---

### Post by minoanlinuxnoob89 on 2018-11-14
Hi there, and thanks in advance for taking the time to help me!
I'm trying to automatically backup the contents of DATA1 (external hard drive) to DATA2 (another external hard drive). I wrote a script called backupDATA2
```
#!/bin/bash
set -e
target_path="/media/nir/DATA2"
include_paths=("/media/nir/DATA1")
for item in "${include_paths[@]}"
do
include_args="${include_args} ${item}"
done
rsync -avR ${include_args} ${target_path}
```

and when I type bash backupDATA2 I get the error: 
```
sending incremental file list
rsync: opendir "/media/nir/DATA1" failed: Permission denied (13)
/media/nir/
/media/nir/DATA1/

sent 133 bytes  received 25 bytes  316.00 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.1]
```

Can anyone help? I'm very new to this....

---

### Post by ajgreeny on 2018-11-14
What filesystems are the two external disks formatted to?

If they are both ext# Linux filesystems they will both be owned by root unless you have changed ownership with a **chown** command.
Assuming they both mount automatically to /media/nir/ which you seem to be showing in your script, try running ```
sudo chown -R nir:nir /media/nir/DATA1
``` and repeat the command for DATA2.

That should allow you as user to read/write to both disks without a problem.

---

### Post by minoanlinuxnoob89 on 2018-11-14
Thank you very much! I'll be able to try that first thing tomorrow at work.

---

### Post by TheFu on 2018-11-14
A caution about backups.  File permissions, ownership, groupid are very important to be included in the backups, not just the files.  If the data is just personal data, it isn't as important, but if it includes system data, settings, configs, and programs, then the owner, group and permissions are mandatory. Restoring without those set correctly will be a failure.

File and directory permissions are a core security feature for Linux systems. It is best to learn them sooner than later. It will save hours, days, weeks, months, of frustration.

---

### Post by hartman8227 on 2018-11-15
I ran into something similar the yesterday. In my case, it was both an ownership and file permissions issue. If you start to change permissions at all make sure that your folders have an execute flag on them when you're done otherwise you will not be able to open the folders. Files don't necessarily need execute rights but it seems that folders do in order to open.

---

### Post by TheFu on 2018-11-15
> **hartman8227 said:**
> I ran into something similar the yesterday. In my case, it was both an ownership and file permissions issue. If you start to change permissions at all make sure that your folders have an execute flag on them when you're done otherwise you will not be able to open the folders. Files don't necessarily need execute rights but it seems that folders do in order to open.

Correct.  eXecute permissions are necessary to access known files inside a directory.  Read on that directory will let a userid see what is inside a directory, but only if eXecute is also available.  There are options to the chmod command to selectively set the X permissions on directories.

---

### Post by minoanlinuxnoob89 on 2018-11-16
Thanks everyone! Permissions are working now, but now it's only backing up an empty directory (not copying the contents of the directory). Even when I try a simple rsync command in the terminal : rsync -avzh /media/nir/DATA1 /media/nir/DATA2
sending incremental file list
DATA1/

sent 68 bytes  received 20 bytes  176.00 bytes/sec
total size is 0  speedup is 0.00

it doesn't transfer any content from DATA1....any advice? I think my script needs to be changed:
```
#!/bin/bash

set -e

target_path="/media/nir/DATA2"

include_paths=("/media/nir/DATA1")

for item in "${include_paths[@]}"
do
include_args="${include_args} ${item}"
done

rsync -avzh ${include_args} ${target_path}
```

---

### Post by TheFu on 2018-11-16
Please show the permissions (ls -ld ) for the source and the target, along with the output from 'id'. The actual files, assuming you have read on the source doesn't matter.
When posting, use *code tags*.

For example, here's a media folder:
```
/DD$ ls -ld .
drwxr-xr-x 14 thefu thefu 4096 Jul  6  2017 ./
```

See how my userid is the owner and has rwx?  That's important.

Is there a reason the command isn't:
```
rsync -avzh /media/nir/DATA1/ /media/nir/DATA2
```
?? Seems much easier than that script.  Also, if you don't want all the files copied to be owned by your userid - owner, group, and permissions are very important in most backups - then use sudo before the rsync command.

---

