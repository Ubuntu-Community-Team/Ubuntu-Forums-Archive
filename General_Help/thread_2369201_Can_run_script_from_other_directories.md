---
title: "Can run script from other directories"
date: 2017-08-19
forum: General Help
---

### Post by raleigh3 on 2017-08-19
I have all my scripts in a Scripts directory.

That dir is in my path, yet I can not run scripts from other directories.

It says "Command not found."

I do not want to puts my scripts in the bin directory.

Thanks.

---

### Post by vasa1 on 2017-08-19
> **raleigh3 said:**
> I have all my scripts in a Scripts directory.

That dir is in my path, yet I can not run scripts from other directories.
...
Just to be sure, what does```
env | grep "^PATH"
```show?

---

### Post by vocx on 2017-08-19
> **raleigh3 said:**
> I have all my scripts in a Scripts directory.

That dir is in my path, yet I can not run scripts from other directories.

It says "Command not found."

I do not want to puts my scripts in the bin directory.

Thanks.
How did you put the directory in the PATH?

There should be something like this in your "/home/user/.bashrc" file
```

mydir=/home/user/Scripts

export PATH="${mydir}:${PATH}"

```

This new PATH only works when you open a new terminal.

If you want the changes to take effect immediately, you can source the ".bashrc" file again.
```

source /home/user/.bashrc

```

---

### Post by raleigh3 on 2017-08-20
I found out that i can create a bin directory under home/andy and that it is automatically added to my path.

---

### Post by ajgreeny on 2017-08-20
> **raleigh3 said:**
> I found out that i can create a bin directory under home/andy and that it is automatically added to my path.
Correct.
Just rename the scripts folder to bin and everything should work.

---

### Post by again? on 2017-08-21
Something you may find useful if using a ~/bin directory.
To unclutter your file browsers home directory you can create a ~/.hidden text file and add files or folders 
that normally show in $HOME, to this file to hide.
These files/folders will only show when you choose to show hidden files.
eg my **~/.hidden** file
```
Examples
bin
gPodder
Audio
Steam
test.txt
git
```

---

### Post by raleigh3 on 2017-08-21
Thanks.

---

