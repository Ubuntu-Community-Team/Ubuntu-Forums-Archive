---
title: "Writting a script"
date: 2006-07-15
forum: General Help
---

### Post by nami on 2006-07-15
Hi

I've been using Linux (Ubuntu) for some time now, but still consider myself a Linux terminal beginner.

I would like to know how to write a little script which when run, will ls into a given directory.

Any help will be appreciated.

nami

---

### Post by ayoli on 2006-07-15
i dont really understand interest of making a script to ls a dir since you can do ls  /dir/you/want but here's a script:

```
#!/bin/bash
if [ -d $1 ] 
    then
    ls $1
    else
    echo "$1 does'nt exist"
fi
```
you may also have a look to this very complete [guide]("http://www.tldp.org/LDP/abs/html/") for bash
regards.

---

### Post by Lunar_Lamp on 2006-07-15
As a bit more info, in a very simple to understand way:

Every bash script starts with: #!/bin/sh or #!/bin/sh

This means "use bash to interpret this script".

You will need to make the script executable, by using 'chmod 755 SCRIPT'.

To execute it you will need to type './path/to/filename' unless you transfer it to /usr/bin (I think that's the directory, I can never remember and am not on *nix at the moment).  If you do this you should just be able to type in the command as wanted.  Another way of doing this is creating an alias in your ~/.bashrc file (details of how to do it are in the file itself).

---

