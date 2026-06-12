---
title: "upgrade failure"
date: 2015-10-28
forum: General Help
---

### Post by cmcanulty on 2015-10-28
on one xubuntu 14.04 computer I am suddenly getting weird output from upgrade command each time it give a different %

```

librarian@gateway:~$ sudo apt-get upgrade
[sudo] password for librarian: 
librarian@gateway:~$ ... 1%
```

---

### Post by speartip on 2015-10-28
Are you running: "sudo apt-get update" first?
Have you tried changing to a different mirror in case the one you are trying is down for some reason?

---

### Post by cmcanulty on 2015-10-28
yes I did update first, how do I set a mirror from the command line?


> **speartip said:**
> Are you running: "sudo apt-get update" first?
Have you tried changing to a different mirror in case the one you are trying is down for some reason?

---

### Post by speartip on 2015-10-28
> **cmcanulty said:**
> how do I set a mirror from the command line?
It's easier doing it via gui.
Install synaptic. then in Settings/Repositories, change the mirror you are downloading from, then click "reload".
If there are any errors it should tell you.

---

### Post by slickymaster on 2015-10-28
> **cmcanulty said:**
> yes I did update first, how do I set a mirror from the command line?

See these: [http://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main](http://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main) and [http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line](http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line)

---

