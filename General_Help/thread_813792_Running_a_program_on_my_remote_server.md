---
title: "Running a program on my remote server"
date: 2008-05-31
forum: General Help
---

### Post by spudthebinx on 2008-05-31
Hi, this is probably a very newbie question. I am running Hardy on my desktop pc, and edgy on my server. My server does not have a keyboard mouse or monitor so I have to do things through a putty ssh thing. The problem is it means running putty on my destkop and cannot close it, and it also interferes with unreal tournament when I run it. Basicaly, how do I run my ut dedicated server on my edgy box without using putty? Is there something I can do using webmin? or is there an equivalent of am autoexec I can add to my server so it runs ut server on start up? Thanks for taking the time to read this, I appreciate I am probably not being clear as I don't know the correct terms for things.

David

---

### Post by 505 on 2008-05-31
You have two approaches to this. The first is to run the command at startup. This is done using init scripts.
The second aproach is much easier. Install a programm called dtach. It allows you to run a command and then detach from the application and return to the terminal. I use it to run rtorrent on my server and leave that program running even after I close the ssh connection.

The basics are as follows. After dtach is install issue a command 
```
dtach -A /tmp/ut ut
```
This will open the command "ut" (and create a file /tmp/ut so keep track of it). Press ctrl+\ to return to the command line. The program keeps running. Issue the same command again to return the the running session of ut.
Hope this helps.

---

### Post by Seisen on 2008-05-31
Besides detach you could also screen which basically does the same thing.

---

### Post by quelx on 2008-05-31
> **Seisen said:**
> Besides detach you could also screen which basically does the same thing.

[http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/](http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/)

---

### Post by 505 on 2008-05-31
> **Seisen said:**
> Besides detach you could also screen which basically does the same thing.
True, but dtach is a bit simpler, that's why I recommended dtach instead of screen.

---

### Post by HalPomeranz on 2008-05-31
But both dtach and screen require you to log in and run the command manually.  The original poster was looking for a way to start the job at boot time with no manual intervention.  The easiest way to accomplish that is to simply put the program start-up command into /etc/rc.local so that it will get executed at boot time.

---

