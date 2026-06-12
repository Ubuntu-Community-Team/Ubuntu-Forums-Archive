---
title: "Open git-gui on Ubuntu 13.10"
date: 2013-10-26
forum: General Help
---

### Post by kanishkdudeja on 2013-10-26
I just installed GIT by the command:

sudo apt-get install git

But how do i open the GUI Interface? git-gui has been automatically installed with git. But when i search git in the dash, it shows no applications.

How do i open the GIT Bash or the GIT GUI on Ubuntu?

Thanks.

---

### Post by TheFu on 2013-10-27
I am unaware of any git-gui being automatically included with the git package. It isn't on my systems.

```
~$ git-gui
git-gui: command not found
```

A few GUI options: [http://www.maketecheasier.com/6-useful-graphical-git-client-for-linux/](http://www.maketecheasier.com/6-useful-graphical-git-client-for-linux/)

---

### Post by mren on 2014-01-17
Installation of the 'git' alone will not install 'gitk' and 'git-gui', you have to install them explicitly:
```

~$ sudo apt-get install gitk git-gui

```
then issue
```

~$ git gui

```
to start.

---

