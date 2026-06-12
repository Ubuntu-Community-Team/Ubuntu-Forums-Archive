---
title: "nautilus and Sudo not working"
date: 2008-05-05
forum: General Help
---

### Post by Hotel on 2008-05-05
Hi i have a serious problem on my Ubuntu system (an old Dell Dimension 4100 Pentium 3) 
Where nautilus loads but dose not display any files (my desktop and the command line do) and Sudo only works sometimes 
and always displays the error message 
```
sudo: unable to resolve host linux-desktop

```
many applications that require root privileges do not load at all whilst others load then freeze

---

### Post by p_quarles on 2008-05-05
Okay, two things here:

1) Don't use sudo to open graphical programs. The graphical sudo wrapper "gksu" is the tool to use for this purpose. E.g.,:
```
gksu nautilus ~/
```

2) This is a common bug with Ubuntu 8.04. To fix sudo, you will need to boot into recovery mode and fix the /etc/hosts file. 

First, find your correct computer name:
```
hostname
```

Load /etc/hosts in nano:
```
nano /etc/hosts
```
And change the second line to include the output of hostname. If your computer were named foo, it should look like this:
```
127.0.1.1      foo
```
Reboot, and sudo should work properly.

---

### Post by Hotel on 2008-05-05
> 1) Don't use sudo to open graphical programs. The graphical sudo wrapper "gksu" is the tool to use for this purpose. E.g.,:
Code:
```

gksu nautilus ~/

```

this dose not fix nautilus which was the only program i was running using sudo the others being stuff like synaptic package manager(dose not load) and update manager(freezes when you press check) and programs like network manger display and error message (when you press unlock)

@2 this appears to fix sudo
but still dose not fix the other problems

---

### Post by dreesemonkey on 2008-05-05
> **p_quarles said:**
> Okay, two things here:

1) Don't use sudo to open graphical programs. The graphical sudo wrapper "gksu" is the tool to use for this purpose. E.g.,:
```
gksu nautilus ~/
```

2) This is a common bug with Ubuntu 8.04. To fix sudo, you will need to boot into recovery mode and fix the /etc/hosts file. 

First, find your correct computer name:
```
hostname
```

Load /etc/hosts in nano:
```
nano /etc/hosts
```
And change the second line to include the output of hostname. If your computer were named foo, it should look like this:
```
127.0.1.1      foo
```
Reboot, and sudo should work properly.

I registered to say thanks.  This is my first install of ubuntu that I've really been playing with and I've had this problem apparently since I installed wine.  

From another thread, it may also be an issue when you have a multi-word hostname.  Mine was originally xxxxxx-ubuntu and just changed it to ubuntu in both /etc/hostname and then /etc/hosts per your advice.  Thanks :)

Finally it's happily chugging along installing updates!

---

### Post by Hotel on 2008-05-06
> **Hotel said:**
> this dose not fix nautilus which was the only program i was running using sudo the others being stuff like synaptic package manager(dose not load) and update manager(freezes when you press check) and programs like network manger display and error message (when you press unlock)

@2 this appears to fix sudo
but still dose not fix the other problems

Dose anyone know how to fix the rest of my problem 
i have no idea what is causing this!

---

