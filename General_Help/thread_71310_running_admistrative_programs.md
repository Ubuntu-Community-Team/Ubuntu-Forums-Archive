---
title: "running admistrative programs"
date: 2005-10-02
forum: General Help
---

### Post by siku on 2005-10-02
I created a root password by doing 
sudo passwd root
I am able to "su" and able to run programs as root that way.
But when I run programs like synaptic or click on the updates available baloon, it asks me for the root password, I type the same root password and this is the error it gives me:
"Failed to run /usr/bin/update-manager as user root:
 Wrong password."
help

---

### Post by tehwa on 2005-10-02
Ubuntu uses sudo instead of straight root access. When a program wants to run as sudo, it will ask for your user password, as opposed to your root password.

It might seem strange at first. This wiki entry will help you:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

