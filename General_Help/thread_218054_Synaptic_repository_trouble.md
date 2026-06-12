---
title: "Synaptic repository trouble"
date: 2006-07-18
forum: General Help
---

### Post by Dave54 on 2006-07-18
I wanted to install Linux DC++ (a direct connect client). I found the "download" page [here]("http://linuxdcpp.berlios.de/document.php?id=1"). I have no idea what that line of code is or how to use it (on the site). I looked up "CVS" and saw the word "repository". So I opened Synaptic, and added a custom repository with the line "cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login"

Well, it didn't take me too long to find out that wasn't right. At this point, when I open Synaptic, i get the error message: > E: Type 'cvs' is not known on line 32 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem. I looked for the repository to remove it, but couldn't find it. (Also, I clicked the "Remove" button to see if it would bring up another window, and I think I removed a much needed repository that I can't figure out how to get back.)

Can anyone help?

Thank-you.

---

### Post by mlind on 2006-07-18
cvs is a version control system, which uses repositories too, but has nothing to do with APT.

you must install cvs package
```

sudo aptitude install cvs

```

then *checkout* a **module** you want
```

mkdir -p ~/tmp/linuxdcpp
cd ~/tmp/linuxdcpp
cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co -P **linuxdcpp**

```


for your second question, there's a checkbox for "Disable smilies in text"

---

### Post by Dave54 on 2006-07-18
Thanks, but can anyone help me undo the damage I've done by adding a false repository? For example, when I try that, I get:> dave@ubuntu:~$ sudo aptitude install cvs
E: Type 'cvs' is not known on line 32 in source list /etc/apt/sources.list
E: Type 'cvs' is not known on line 32 in source list /etc/apt/sources.list
E: The list of sources could not be read.The problem is that none of the repositories is the one I added, so I can't figure out how to remove it.

---

### Post by mlind on 2006-07-18
> **Dave54 said:**
> Thanks, but can anyone help me undo the damage I've done by adding a false repository? For example, when I try that, I get:The problem is that none of the repositories is the one I added, so I can't figure out how to remove it.

```

sudo gedit /etc/apt/sources.list

```

and remove line 32 that seems to cause problems.

---

