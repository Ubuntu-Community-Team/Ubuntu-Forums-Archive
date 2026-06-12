---
title: "How can I convert my old PC into something more practicle."
date: 2008-06-10
forum: General Help
---

### Post by Malisis on 2008-06-10
How can I make my old PC [Pentium(R) 4 CPU 2.50GHz, 504mbRAM] Into a server of sorts for personnel files and music. While I want to be able to access it through a local network I want to be able to access it from anywhere with internet. Is this possible? If so, is it possible to have it accessible from both an XP OS and the Linux OS?  Right now it is running XP and is very bloated with years of pointless files and programs ect, and I want to make it useful in this or a similar capacity. Thank you for your assistance in advance.

---

### Post by LoneWolfJack on 2008-06-10
You can install apache, activate directory listings and put all your files into the web root. As long as you have a static IP address, you'll be able to access your files from anywhere in the world... create a .htaccess file to restrict access.

---

### Post by Vivaldi Gloria on 2008-06-10
I regularly use sshfs to mount a remote directory as a local one. I use the command

```
sudo sshfs [email]user@remote.machine:/remote.dir[/email] /where/to/mount/localdir -o allow_other
```

Now the remote directory becomes no different than a regular local directory. So you can browse, play etc. as if it is a regular directory on your computer.

sshfs is a layer on top of ssh so it is secure. The default settings of /etc/ssh/sshd_config only allow LAN connections but they are easy to change. Also use a non-standard port (smthg other than 22).

The only problem is that I always used it with linux computers, so I don't know how it works with Windows. May be you can do it somehow by installing putty on windows or maybe there is a version of sshfs for Win. 

In linux it is very easy to intall. You install ssh server on your P4 and install sshfs on the computer you use to reach the P4.

---

### Post by MacAnthony on 2008-06-10
If you go the route of apache, you could setup a webdav server and then yes, any webdav client would be able to access the files.

[http://httpd.apache.org/docs/2.0/mod/mod_dav.html](http://httpd.apache.org/docs/2.0/mod/mod_dav.html)

---

### Post by Malisis on 2008-06-10
Thank you for your assistance, I'll give it a try.

---

