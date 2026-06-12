---
title: "rc.d in Hoary"
date: 2005-04-10
forum: General Help
---

### Post by Raven-sb on 2005-04-10
Hi,

Currently I am working myway through a linux book so I can improve my linux skills. The book makes reference to /etc/rc.d directories and one of the exercises is in the book involves this directory. Problem is I can't find it in my system. According to the book, rc.* is a group of directories that define active services for each run level. 

Can someone please tell me if these directories are included in Ubunto and if so where to find them and if not does Ubuntu have an eqivalent set of directories that performs the function of the rc.* directories and where they are stored.

Regards,

Raven

---

### Post by kassetra on 2005-04-10
[QUOTE=Raven-sb]Can someone please tell me if these directories are included in Ubunto and if so where to find them and if not does Ubunto have an eqivalent set of directories that performs the function of the rc.* directories and where they are stored.[/QUOTE]

Ubunt_u_ does indeed have rc*.d directories, under /etc.

---

### Post by Raven-sb on 2005-04-10
[QUOTE=kassetra]Ubunt_u_ does indeed have rc*.d directories, under /etc.[/QUOTE]

Opps, sorry for the wrong spelling.  Have said that I've run ls -a /etc and no rc*.d directories show up.  Am I doing something wrong?

---

### Post by kassetra on 2005-04-10
[QUOTE=Raven-sb]Opps, sorry for the wrong spelling. Have said that I've run ls -a /etc and no rc*.d directories show up. Am I doing something wrong?[/QUOTE]

Here's what I did and got in return:
 ```
kassetra@geisha:/ $ ls -d /etc/rc*
/etc/rc0.d  /etc/rc2.d  /etc/rc4.d  /etc/rc6.d
/etc/rc1.d  /etc/rc3.d  /etc/rc5.d  /etc/rcS.d

```

---

### Post by Raven-sb on 2005-04-10
Ah ok, 

I didn't know about the -d switch.  Thanks for the help kassetra :-P

Raven

---

### Post by kassetra on 2005-04-10
[QUOTE=Raven-sb]Ah ok, 

I didn't know about the -d switch.  Thanks for the help kassetra :-P

Raven[/QUOTE]

-d is the one I use every time I'm looking for directories... (ok so in my mind -d = directory, and I know that's not the real reason behind the switch, but I remember it that way... heh.)

---

