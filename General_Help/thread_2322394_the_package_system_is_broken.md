---
title: "the package system is broken"
date: 2016-04-27
forum: General Help
---

### Post by lgt2 on 2016-04-27
i get this message when im trying to update or download something


Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by nerdtron on 2016-04-27
Hi,

Can you post the entire output of "sudo apt-get update" here? Also did you add any PPA before this happened?

Please use [noparse] ```
 code tags 
``` [/noparse] for easier viewing/reading of you output.

---

### Post by lgt2 on 2016-04-27
here you go 
```
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [92.2 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [93.3 kB]
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Fetched 185 kB in 0s (264 kB/s)                   
Reading package lists... Done
```

---

### Post by Bashing-om on 2016-04-27
lgt2; Hello;

Way to brief of an output .. maybe take the package manager's advise and run:
```

ls -al /etc/apt/sources.list
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

```
to get a notion of where the fault may lie .

[INDENT][INDENT]the package manager does not lie
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-04-27
The URLs to several software repositories are missing. Everything happens for a reason. If we deactivate some repositories then we lose those sources of software and cannot install anything. The OP's sources.list file is missing the Main & Universe repositories and possibly others as well.

System Settings>Software & Updates. Re-activate the repositories.

---

