---
title: "Impossible to log in my session"
date: 2017-01-19
forum: General Help
---

### Post by sebgondron on 2017-01-19
Hi everyone!

I have a surprising issue: I can't log in my session  on Kubuntu 14.04 LTS. I can log withou any issues on the Guest session.  When i enter my password, the authentication field vanishes and then I  stay block indefinitely on the blue screen of Kubuntu. The loading icons  don't even appear.

I have used a lot lately a live system: the  last version of Kali Linux. I used to access my documents on my Kubuntu  partition, including my documents on this session, in the /home. I can  still access to all of these documents from my live version. Before the  problem appears, I was doing a lot of forensics on an image on this  session, but I don't think it can be related.

This is my problem, I hope somebody has an idea about the origin of my problem.
Thanks for you help,
SebGondron

---

### Post by ajgreeny on 2017-01-19
Use Ctrl+Alt+F1 when you get to that blue screen of Kubuntu which should take you to a tty command-line where hopefully you can login with your username and password (password will not show as you type).

Once logged in use command ```
ls -la | less
``` which will list all files and folders in your home with permissions and you will be able to scroll up and down with the cursor keys to look for any files or folders not owned by you; perhaps by root instead.

It would be interesting to know what you were doing with Kali; did you edit any of those session files that you say you accessed?

---

### Post by sebgondron on 2017-01-19
I was doing memory forensics. And I only use volatility frameworks, the  last version (2.6). I have used on the image on my session I was  studying the plugins imageinfo, pstree and memdump. I was root. Those  were the last things I have done before loosing my access to my session.
I have modified or removes files on my session directly from Kali the last three weeks, but this morning I had no problems to log in my session.

The rest of the afternoon I have worked on images directly on my USB.

---

### Post by sebgondron on 2017-01-19
I connect through the Ctrl + Alt + F1 way.
First of all, I have an error :

> E: Unknown Error: '<class 'KeyError '>' ("The cache has no package names 'wine-devel-i386'") run-parts: /etc/update-motd.d/90-updates-available exited with return 255

However, I am connected to my sessions. By list the file at the root of /home, I have three interesting files that weren't here before and I am thinking there are related to this problem:

> 
janv. 19 22:10 .Xauthority
janv. 19 22:11 .xsession-errors
janv. 19 21:40 .xsession-errors.old


The times of the files correspond to my last attempts to log on graphically (thus the X). Have you encountered such a case before :)?

---

### Post by sebgondron on 2017-01-20
But those three files hqv strange righm thoug they are owned by the non-root user of the session. They all have the rights:
"-rw------"

There is an issue here? It should alo "rw" for the user?

---

### Post by ajgreeny on 2017-01-20
Those -rw------ permissions for the files are quite normal and OK, so no need to worry about that as long as they are owned by you as user, not root, which I am not sure about from your post.

---

### Post by sebgondron on 2017-01-20
They are owned by the user, sorry for my formulation.

---

### Post by steeldriver on 2017-01-20
Have you looked at the contents of the .xsession-errors file?

```

tail ~/.xsession-errors

```

---

### Post by sebgondron on 2017-01-21
There is nothing in it :/

---

### Post by steeldriver on 2017-01-21
Is there a ~/.xsession-errors.old file? if so, what's in that?

---

### Post by sebgondron on 2017-01-21
There is one, also completely blank.

---

