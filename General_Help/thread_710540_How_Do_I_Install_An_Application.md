---
title: "How Do I Install An Application?"
date: 2008-02-28
forum: General Help
---

### Post by L1882 on 2008-02-28
OK, total newbie here.

I realise I'm going to look really silly here but you have to understand, until now I've been a total Microsoft boy and so I'm not used to actually having to think for myself.

So I have downloaded a Citrix ICA client (10.6) for Linux. How do I install it? Its in a compressed folder but there's no trusty setup.exe so now I'm lost.

Any help gratefully received.

---

### Post by y-lee on 2008-02-28
It depends upon what is in  the compressed folder. For reference see [How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by L1882 on 2008-02-28
Cheers Y-Lee

That helped - I managed to get it all sorted

---

### Post by FuturePilot on 2008-02-28
Most of the time, the piece of software you want is in the repos. In that case it's as easy as ```
sudo apt-get install <package-name>
```

Another good guide on installing stuff
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by trobbins on 2008-02-28
Step-by-step instructions begin around page 18 of this guide:

[http://support.citrix.com/servlet/KbServlet/download/180-102-17370/Unix_Client_Administrator_Guide.pdf](http://support.citrix.com/servlet/KbServlet/download/180-102-17370/Unix_Client_Administrator_Guide.pdf)

When you see "privileged user" this usually means the root user.  To run a command as root, type "sudo" before the command, like ```
 sudo ping localhost
```.

I would use the tar.gz version that they have instead of the rpm.

---

### Post by knutschr on 2008-02-28
> I would use the tar.gz version that they have instead of the rpm.
Why is that?

---

### Post by TheWizzard on 2008-02-28
> **trobbins said:**
> Step-by-step instructions begin around page 18 of this guide:

[http://support.citrix.com/servlet/KbServlet/download/180-102-17370/Unix_Client_Administrator_Guide.pdf](http://support.citrix.com/servlet/KbServlet/download/180-102-17370/Unix_Client_Administrator_Guide.pdf)

When you see "privileged user" this usually means the root user.  To run a command as root, type "sudo" before the command, like ```
 sudo ping localhost
```.

I would use the tar.gz version that they have instead of the rpm.

if there's no deb, only rpm, i'd advice you to use alien. this programme converts rpm to deb.

if you build from source, please do yourself a favour and use checkinstall to create a deb!

---

### Post by L1882 on 2008-02-28
In the end I used the tar-gz file - unzipped it.

There was an installer script inside - all incredibly easy.

I guess it's just difficult being a novice again - most of what I know is useless on the Linux. Still, it certainly seems to run a lot faster than windows

---

### Post by TheWizzard on 2008-02-28
> **L1882 said:**
> In the end I used the tar-gz file - unzipped it.

There was an installer script inside - all incredibly easy.

I guess it's just difficult being a novice again - most of what I know is useless on the Linux. Still, it certainly seems to run a lot faster than windows

start using checkinstall asap! it'll help you.

---

### Post by trobbins on 2008-02-29
Wow TheWizzard, thank you for pointing out checkinstall.  I always wanted a program like this but didn't know one existed.

---

### Post by TheWizzard on 2008-02-29
> **trobbins said:**
> Wow TheWizzard, thank you for pointing out checkinstall.  I always wanted a program like this but didn't know one existed.

glad i could help :popcorn:

---

