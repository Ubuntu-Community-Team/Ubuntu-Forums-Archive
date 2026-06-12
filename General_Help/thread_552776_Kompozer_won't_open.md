---
title: "Kompozer won't open"
date: 2007-09-16
forum: General Help
---

### Post by Ryupower on 2007-09-16
Hi, I installed Ubuntu Ultimate and converted to Ubuntu CE just a few days ago. I also did this in a previous version of ubuntu ultimate, and kompozer opened without problem.

Now, when I try to open kompozer though, it uses up my CPU to like, 78% and stays like that until I kill the process. It just won't open! I tried completely removing kompozer and reinstalling, but it still has this issue! What is going on?!


Synaptic refuses to install Emerald because it doesn't want to install a dependency ( doesn't even give you a reason:  "emerald:
 Depends: libemeraldengine0 but it is not going to be installed"

So, any help is appreciated.

---

### Post by prince_niceguy on 2007-09-17
run kompozer from terminal and post the output... that should give some start...

---

### Post by Ryupower on 2007-09-17
I did, and it doesn't give you an output. It just stays like in the attachment. 

And then after staying like that for what seems like forever. It acts like it opened it. ( it just starts a new, blank "~$" line. )

---

### Post by Irony on 2007-09-17
To install kompozer I assume you just untarred it.

This means you will have to find the path to it - for example my path to kompozer is;

[PHP]user@ubuntu:~$ '/home/user/Kompozer077/kompozer' [/PHP]

---

### Post by Ryupower on 2007-09-17
> **Irony said:**
> To install kompozer I assume you just untarred it.

This means you will have to find the path to it - for example my path to kompozer is;

[PHP]user@ubuntu:~$ '/home/user/Kompozer077/kompozer' [/PHP]

nuh, it was installed through synaptic

---

### Post by Ryupower on 2007-09-19
*bump* This is very important for my web design. >.<

---

### Post by prince_niceguy on 2007-09-20
have you tried removing and reinstalling it??

---

### Post by Ryupower on 2007-09-21
> **prince_niceguy said:**
> have you tried removing and reinstalling it??

> **Ryupower said:**
> t just won't open! I tried completely removing kompozer and reinstalling, but it still has this issue! What is going on?!
.

Yep.

---

### Post by Irony on 2007-09-21
Have you tried uninstalling it and using the tarball from the kompozer site?

---

### Post by Ryupower on 2007-09-23
> **Irony said:**
> Have you tried uninstalling it and using the tarball from the kompozer site?

I haven't tried that, I will give it a shot. Thanks

---

### Post by Ryupower on 2007-09-23
it seems to be working
Thanks!

---

### Post by mircea.postolache on 2007-10-01
I had the same problem with kompozer. I looked on their site and noticed that their newest version is 0.7.10. While the Synaptic version shows 0.77 !!! That's surely a mistake in packaging on the ubuntu repository. And because of this Synaptic will always tell you that there is a newer version. I have removed 0.77 from synaptic and then installed from their site the deb package. [http://downloads.sourceforge.net/kompozer/kompozer-0.7.10-i386.deb?use_mirror=ovh](http://downloads.sourceforge.net/kompozer/kompozer-0.7.10-i386.deb?use_mirror=ovh)
Ignore the warning about newer version. 0.7.10 will work fine. (I have noticed that it installed the launcher in the Internet menu - previous version was in Programming)

---

