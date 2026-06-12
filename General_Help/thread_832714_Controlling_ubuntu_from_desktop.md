---
title: "Controlling ubuntu from desktop?"
date: 2008-06-18
forum: General Help
---

### Post by gamingneeds on 2008-06-18
Hey,

Is there a specific program that will let me remotely control my ubuntu server from my Windows desktop at my office?

I have heard of tightVNC and some others, but not sure how they work exactly or if they are compatible with ubuntu.

Any help or even input here would be nice.

Thanks.

---

### Post by dstein on 2008-06-18
The program cygwin provides a Unix-like shell for Windows. So if you download cygwin, you can type the following from the shell: ```
$ ssh username@domain
``` This will give you access to a terminal. There is also a way to install X Windows on cygwin and then use ```
$ ssh -Y username@domain
``` This will allow you to run graphical programs. However, it has been awhile since I did this. I hope this helps.

---

### Post by kalesh7 on 2008-06-18
if you only need command line just download putty and connect from that using shh.

---

### Post by gamingneeds on 2008-06-18
So if I'm trying to run graphical programs, I should go with X Windows?

---

### Post by kalesh7 on 2008-06-18
> **gamingneeds said:**
> So if I'm trying to run graphical programs, I should go with X Windows?
Yeah, I guess so, though I never had to do it myself, ubuntu(and almost any linux) uses the X windowing system so logically X windows route should do it.

---

### Post by cariboo on 2008-06-18
Use the remote desktop program that is installed by default. Turn the server on by going to System-->Preferences-->Remote Desktop and select what you need to connect. It works from windows with any of the vnc variants.

Of course you will have to have X running on your server.

With no gui use ssh

Jim

---

### Post by gamingneeds on 2008-06-18
How do I add this GUI? Also, how do I do this via SSH?

Thanks.

---

### Post by lavinog on 2008-06-20
ssh:
[http://doc.ubuntu.com/ubuntu/serverguide/C/openssh-server.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/openssh-server.html")
to have gui control you need Xorg installed
```
apt-get install Xorg
```
you will also need to install the gui equivalents of the programs you want to run remotely...this will generally require alot of libraries to be installed.

It is a good idea to learn how to use the command line for managing a server.

But it is nice to have a server with gui apps on it for a portable desktop...like when i am at school I can ssh to my server and use programs i want to use

---

