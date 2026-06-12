---
title: "How to run updates via terminal instead of synapic package manager"
date: 2008-06-14
forum: General Help
---

### Post by reality1011 on 2008-06-14
I searched some but I was not able to find the command to run the package manager through the terminal.

I thought it was 'sudo apt-get update' but that just updates the list of available packages...


I am trying to make a script to update the system, this will eventually lead to a cron job.

---

### Post by atomkarinca on 2008-06-14
Have you tried this?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bubba_169 on 2008-06-14
You want 'sudo apt-get upgrade' :D

Or 'sudo apt-get dist-upgrade' to update everything including the kernel

---

### Post by x1a4 on 2008-06-14
Don't use apt-get.  Use aptitude instead.  Aptitude has better dependency handling, is able to resolve problems better and removes unused dependencies when removing packages.  It also has a decent curses front-end.

---

### Post by VMC on 2008-06-14
> **x1a4 said:**
> Don't use apt-get.  Use aptitude instead.  Aptitude has better dependency handling, is able to resolve problems better and removes unused dependencies when removing packages.  It also has a decent curses front-end.

Your right that is a slick front end curses, but what is the benefit over Synaptic? They appear similar. One uses curses the other GUI.

---

### Post by reality1011 on 2008-06-15
'sudo aptitude full-upgrade' works great .... thanks

---

### Post by x1a4 on 2008-06-15
> **VMC said:**
> but what is the benefit over Synaptic? 

The difference is in the way it functions.

> **x1a4 said:**
> Aptitude has better dependency handling, is able to resolve problems better and removes unused dependencies when removing packages.

It also has better search capabilities.

---

