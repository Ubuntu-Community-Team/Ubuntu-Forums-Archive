---
title: "Need program to test file system operations"
date: 2014-01-17
forum: General Help
---

### Post by krafczyk-matthew on 2014-01-17
I'd like to use a program which allows me to test file system commands without actually modifying the file system.

For instance. I'd like to build a list of commands to apply to a directory tree which exists in several locations. I'd like to test it first without actually modifying the files to see if everything is correct.

like I'd like to use mv to move directories around or rename them. I'd like to use rm to remove files and directories, etc..

After applying these operations, I'd like to use ls to inspect the files in each directory, and check that everything is correct.

Then I would be able to apply the commands I tested like a bash script to all the locations that I'm interested in modifying the same way.

Any help is appreciated!

---

### Post by ian-weisser on 2014-01-17
Create (or copy) a set of directories/subdirectories in /tmp to play with.
Delete the /tmp version when finished.

---

### Post by krafczyk-matthew on 2014-01-17
Wow.. why didn't I think of that.. so simple..

Thanks for the suggestion. I think that will work nicely.

---

