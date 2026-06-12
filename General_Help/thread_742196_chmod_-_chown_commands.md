---
title: "chmod - chown commands"
date: 2008-04-01
forum: General Help
---

### Post by stzednym on 2008-04-01
Dear Ubuntus

please i can not find the commands CHmod or Chown in my terminal ( missing operand)???

please help

also i did not find them by Synaptic Packagae Manager

thanks in advance, Viele Grüße
yamos2002

---

### Post by Slushdoot on 2008-04-01
Are you typing it in all lower case?

What exactly are the commands you're passing it?

---

### Post by scrooge_74 on 2008-04-01
the commands are chown and chmod  all in lower case

---

### Post by cdenley on 2008-04-01
They are located in /bin. They are both part of the package "coreutils", and always come preinstalled.

---

### Post by scrooge_74 on 2008-04-01
you forgot to add that they are in the path so you can invoke them from any place in the system

---

### Post by ibuclaw on 2008-04-01
```

:~/$ ls -l myfile
drwxr-x---  2 **aname aname**    4096 2008-03-06 00:11 myfile

:~/$ chown
chown: missing operand
Try `**chown --help**' for more information.

:~/$ chown --help
Usage: chown [OPTION]... **[OWNER][:[GROUP]] FILE**...

:~/$ chown myname:myname myfile

:~/$ ls -l myfile
drwxr-x---  2 **myname myname**    4096 2008-03-06 00:11 myfile

```

Hope this clears up any confusion.

The same applies to **chmod** too. only the permissions numbers are used instead

ie:
```
 chmod 754 myfile 
```
For better understanding of the permission numbers, think of it as their binary equivilant.
7 = 111 = rwx
6 = 110 = rw-
5 = 101 = r-x
4 = 100 = r--
etc...

And the permissions are set to the following users in order
**OWNER : GROUP : OTHER**
Owner gets the highest number, Guest/Other gets the lowest number respectedly.

Regards
Iain

---

### Post by stzednym on 2008-04-02
yes they are in bin folder but i can not use them
please, how can i add them to the path?

regards

---

### Post by stzednym on 2008-04-02
you are right i can see them installed in my bin but i can not use them?? please any advice

---

### Post by kpkeerthi on 2008-04-02
> **stzednym said:**
> yes they are in bin folder but i can not use them
please, how can i add them to the path?

regards

What happens when you type **chown** and **chmod** at the command prompt? Post the output here. 

If you are getting 'missing operands', do as tinivole suggest.

---

### Post by briareos on 2008-04-02
Make sure that you have rights to chown/chmod for the specific file . If you are not the owner of the file or donot have write permission to the file , you will not be able to change ownership/permission of the file using chown/chmod as a normal user.

---

### Post by stzednym on 2008-04-02
yes they are lowercase as usual.
 and i am working with tiny os
[http://www.tinyos.net/tinyos-2.x/doc/html/install-tinyos.html](http://www.tinyos.net/tinyos-2.x/doc/html/install-tinyos.html)

---

### Post by stzednym on 2008-04-02
> **briareos said:**
> Make sure that you have rights to chown/chmod for the specific file . If you are not the owner of the file or donot have write permission to the file , you will not be able to change ownership/permission of the file using chown/chmod as a normal user.

i am the owner as administrator but also did not work, i get:
[COLOR="Blue"]chmod: missing operand[/COLOR]

??

---

### Post by stzednym on 2008-04-02
> **kpkeerthi said:**
> What happens when you type **chown** and **chmod** at the command prompt? Post the output here. 

If you are getting 'missing operands', do as tinivole suggest.

[COLOR="Blue"]I get missing operand , i am working with STEP5 of this tutorial if you know 


**[http://www.tinyos.net/tinyos-2.x/doc/html/install-tinyos.html](http://www.tinyos.net/tinyos-2.x/doc/html/install-tinyos.html)**


[/COLOR]

---

### Post by cdenley on 2008-04-02
You still haven't posted the exact command you are trying to run. As demonstrated by tinivole, "missing operand" means you are not using the command correctly. If you don't tell us what command you're trying to run, we can't help you correct it.

---

### Post by cecilpierce on 2008-04-02
type chmod --help,
you have to tell it what you want it to do.

---

