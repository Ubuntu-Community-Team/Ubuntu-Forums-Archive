---
title: "apt-cache problem, 100% cpu"
date: 2008-06-03
forum: General Help
---

### Post by janwar on 2008-06-03
Hi,

Yesterday I've updated my Ubuntu installation from Gutsy to Hardy and since then my CPU is used 100% all the time. I've noticed that the app that is causing this problem is apt-cache but I'm not able to kill it because the pid of apt-cache constantly changes. I'm not the only person who encounter this issue, someone posted the same problem [here]("http://ubuntuforums.org/showthread.php?t=763508"), but unfortunately no one helped.

There are some other problems with software compatibility but I can handle them by myself. Thanks in advance for any ideas how to fix this.

---

### Post by danwood76 on 2008-06-03
You could try killing apt-cache from the terminal:
```

sudo killall apt-cache

```

apt-cache is the program that is used to search through the aptitude software list and display meta data.
It shouldnt be running all the time, are you doing any updates or software installs?

---

### Post by janwar on 2008-06-03
Thanks for the reply.
Just tried "sudo killall apt-cache" command and it killed apt-cache but it relaunched itself instantly :| So the pid changes are probably caused by terminating and relaunching apt-cache in a loop.

I'm not doing any updates nor software installs at the moment...

---

### Post by danwood76 on 2008-06-03
Well you could try doing an apt-get update to see if its something to do with apt.

```

sudo apt-get update
sudo apt-get upgrade

```

---

