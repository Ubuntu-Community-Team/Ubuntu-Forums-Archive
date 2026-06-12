---
title: "Ultra Minimal Install"
date: 2007-02-27
forum: General Help
---

### Post by sc30317 on 2007-02-27
Hey all,

I would like to know-  I want to remove all the programs from my ubuntu installation, and then reinstall only the programs that I need.  is there any way to do this?

Thanks

---

### Post by Nythain on 2007-02-27
server install disc without selecting to install any servers should do the trick, or maybe the alternative method disc

---

### Post by llamakc on 2007-02-27
The easiest way to answer this question is for you to tell us what you consider the packages that you need, are.

---

### Post by kerry_s on 2007-02-27
Here's the mini.iso, just do the server install and build up from there.->
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

server
login
sudo su
nano /etc/apt/sources.list
uncomment all repos
apt-get update
apt-get install x-window-system-core gdm (your de/wm and what ever else you want) 
reboot
login

---

