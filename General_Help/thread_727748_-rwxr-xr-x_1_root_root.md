---
title: "-rwxr-xr-x 1 root root"
date: 2008-03-18
forum: General Help
---

### Post by ccclay on 2008-03-18
Looking for help. Thank you very much !!!

I am following the Setup page for Ubuntu TightVNC Server 
[http://www.davelachapelle.ca/guides/ubuntu-tightvnc-server/](http://www.davelachapelle.ca/guides/ubuntu-tightvnc-server/)

However, I dont know how to do with this step :

Save the file and make sure the permissions are as follows:
[PHP]
  -rwxr-xr-x 1 root root [/PHP]

I have tried this

[PHP]:/etc/init.d$ -rwxr-xr-x 1 root root
bash: -rwxr-xr-x: command not found
:/etc/init.d$ chmod -rwxr-xr-x 1 root root vncserver
chmod: cannot access `1': No such file or directory
chmod: cannot access `root': No such file or directory
chmod: cannot access `root': No such file or directory
chmod: changing permissions of `vncserver': Operation not permitted[/PHP]

---

### Post by Olav on 2008-03-18
First, do:

```
ls -l /etc/init.d/tightvncserver
```
to see if the permissions aren't correct already.

If you installed as root (or with sudo) ownership as root:root should not be a problem.

Do:

```
sudo chmod +x /etc/init.d/tightvncserver
```
to set the execute permission.

You should **really** learn a bit about ownership and permissions of files. This is fundamental knowledge that will help you tremendously in future installations,

---

### Post by Arthur Archnix on 2008-03-18
> You should **really** learn a bit about ownership and permissions of files. This is fundamental knowledge that will help you tremendously in future installations

I'd file this under good, but not strictly necessary advice. I used ubuntu for over a year quite successfully before I'd even heard of the chmod command.

That being said, being able to change file permissions has in fact helped me tremendously. :popcorn:

I've been able to prevent accidental deletions of files, prevent other users from seeing my files, and other stuff like that.

---

