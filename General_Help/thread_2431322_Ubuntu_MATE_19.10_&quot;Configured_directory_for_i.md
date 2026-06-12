---
title: "Ubuntu MATE 19.10: &quot;Configured directory for incoming files does not exist . ."
date: 2019-11-14
forum: General Help
---

### Post by Kurt_Alan on 2019-11-14
When I CLI ```
/home/username/Downloads
```  "Downloads" does not exist. Google search mentions use of blueman-services, but I cannot find any clear statement of problem or resoltion. 

Your help appreciated.

---

### Post by Bashing-om on 2019-11-14
Kurt_Alan; Humm -

Maybe a bit more info about your system - as the Downloads directory is a default creation on all debian installs:
> 
sysop@x1804mini:~$ ls -al /home/sysop/Downloads
total 8
drwxr-xr-x  2 sysop sysop 4096 Sep 21 19:33 .
drwxr-xr-x 26 sysop sysop 4096 Nov 14 15:11 ..
sysop@x1804mini:~$


Are you perhaps not substituting your system user name for the place holder "username" in the path "/home/username/Downloads" ?

In the above example my username is sysop.

Else there is a setting in the browser for where to direct dowloads to be directed to.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2019-11-15
Are you really typing /home/yourusename/Downloads? That would try to execute a program called "Downloads" in /home/yourusername. To list the contents of a directory use ls, e.g.

```
ls /home/yourusername/Downloads
```

---

### Post by Kurt_Alan on 2019-11-25
It does help, thank you. For unknown reasons, my error message disappeared after several reboots. "ls" confirms Download intact.

---

### Post by Kurt_Alan on 2019-11-25
This helps. Thank you for clarifying.

---

### Post by Bashing-om on 2019-11-25
Kurt_Alan; Good deal :)

We mark this one up as "reason for outage:unknown" :D

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

-Sometimes ubuntu does magic.-

---

