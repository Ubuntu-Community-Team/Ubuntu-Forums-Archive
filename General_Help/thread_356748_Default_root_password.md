---
title: "Default root password?"
date: 2007-02-08
forum: General Help
---

### Post by Mygly on 2007-02-08
I'm trying to run peerguardnf on ubuntu 6.10 and when i try to load it it asks for the root password. I type in what I thought it was and it isn't recognizing it. Is there some kind of default root password?

---

### Post by meng on 2007-02-08
Ubuntu uses sudo rather than having a root password enabled. Try typing your user password instead.

---

### Post by Maestro23 on 2007-02-08
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Mygly on 2007-02-08
It doesn't take my password, and when I tried using ```
sudo pgtext
```
It says "Please enter root password to Load PG." I then type in my password only it appears as plain text and then nothing else happens. I can press enter, keep typing, etc. and it won't ever go back to the prompt.

---

### Post by Maestro23 on 2007-02-08
> **Mygly said:**
> It doesn't take my password, and when I tried using ```
sudo pgtext
```
It says "Please enter root password to Load PG." I then type in my password only it appears as plain text and then nothing else happens. I can press enter, keep typing, etc. and it won't ever go back to the prompt.

Where did you get the peerguardian file from?

---

### Post by Mygly on 2007-02-08
I put these```
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main
```
In my /etc/apt/sources.list file and used synaptic.

---

### Post by meng on 2007-02-08
If you really must, you can do this
sudo passwd root

and set a root password. It's not really the Ubuntu way, but you have the freedom to do it.

---

### Post by Mygly on 2007-02-08
Would there be any way to undo that at a later time?

---

### Post by meng on 2007-02-08
sudo passwd -l root
will disable the root password

---

