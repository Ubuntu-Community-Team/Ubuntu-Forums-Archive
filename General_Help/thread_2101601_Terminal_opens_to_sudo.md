---
title: "Terminal opens to sudo"
date: 2013-01-05
forum: General Help
---

### Post by Rutilus on 2013-01-05
Straight after reinstalling Ubuntu 12.10, I did a couple of sudo commands and exited. Now, as soon as I open a terminal, I'm asked for my sudo password. I have to enter a wrong password three times to get a user terminal prompt. This hasn't happened on any previous Ubuntu installation.

Restarting the computer made no difference. I searched the web and the forums without getting an answer probably because I can't think of the right keywords. Can anyone please help? Thanks.

---

### Post by fdrake on 2013-01-05
check /etc/passwd file: make sure that your username has your right home directory, not root's home.
```

gksudo gedit /etc/passwd 

```

---------------------------
if that's not the case run this command please 
```
env | grep home
```
is the result your home path?

---

### Post by Rutilus on 2013-01-05
Both tests seem positive: they show /home/username.

---

### Post by fdrake on 2013-01-05
it may be that is something wrong with sudo program itself. ?
use a console (ctrl+alt+f1) or the terminal and login into root 
```

sudo su

```
then reinstall sudo 
```

apt-get remove --purge sudo
apt-get install sudo && apt-get update
exit

```

to come back ate the prev : ctrl+alt+f7

---

### Post by Rutilus on 2013-01-05
I had created a .bash_aliases file with an alias command but I hadn't wrapped the command with: alias aliasname=" ... ". Having corrected that, the Terminal opens to user prompt.

Thanks, fdrake, for helping me and so quickly too.

---

### Post by fdrake on 2013-01-05
> **Rutilus said:**
> I had created a .bash_aliases file with an alias command but I hadn't wrapped the command with: alias aliasname=" ... ". Having corrected that, the Terminal opens to user prompt.

Thanks, fdrake, for helping me and so quickly too.
well i had not idea you have created the aliases file. Glad you solved the problem. You can skip my prev post then.

PS. make sure to mark the thread as "solved" for other ppl.

---

### Post by Rutilus on 2013-01-05
Thanks, fdrake. Would you mind telling me how to mark the thread as solved? I tried two things that failed (look at the titles of the posts!) and I was just starting to browse the forums to try to find out when I saw you had posted again and might not mind telling me. Thanks!

---

### Post by fdrake on 2013-01-05
> **Rutilus said:**
> Thanks, fdrake. Would you mind telling me how to mark the thread as solved? I tried two things that failed (look at the titles of the posts!) and I was just starting to browse the forums to try to find out when I saw you had posted again and might not mind telling me. Thanks!

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Rutilus on 2013-01-05
Thanks again and a good way to tell me.

Future readers please note that I hadn't seen - so haven't tried anything in - fdrake's post about the sudo program and reinstalling sudo.

---

