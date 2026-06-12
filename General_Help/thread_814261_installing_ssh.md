---
title: "installing ssh"
date: 2008-05-31
forum: General Help
---

### Post by jnewstr on 2008-05-31
hi I am really new to ubuntu 
i was surfing the web and decided to start a new project
I mostly use mac's and am familiar with the terminal but nowhere near an expert.
So i have a website hosted on hosting service and was wanting to possibly move it to my own home server
but before i get to that i wanted to create a home file server
so i was looking and it seems that ubuntu would get the job done quite nicely.  I have been trying to install openssh and it won't work when i type in the command apt-get install openssh-server

what am i doing wrong and is there an easier way to do this?
I am using the standard distribution of ubuntu not the server version.
(I didn't feel like jumping into total command line just yet :) )
thanks in advance for the help

Jay

---

### Post by FuturePilot on 2008-05-31
What are the errors you get when you enter that command?

This may also help
[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by drs305 on 2008-05-31
> **jnewstr said:**
> I have been trying to install openssh and it won't work when i type in the command apt-get install openssh-server

what am i doing wrong and is there an easier way to do this?

Jay

Two things come to mind. Do you have a window with synaptic open? If so, close it first. Secondly, you must run this command as root, like this:
```
sudo apt-get install openssh-server
```

---

### Post by s-lime on 2008-05-31
sudo apt-get install ssh

---

### Post by jnewstr on 2008-06-01
thanks for all of your replies.
i try that code and it returns 
err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hard-security/main openssh-blacklist 0.1-1ubuntu0.8.04.1
it says that a couple of times and then at the end it says 
unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

any help is greatly appreciated thanks

---

### Post by jnewstr on 2008-06-01
wow sorry 
the problem was i wasn't connected to the internet...
although ethernet and everything was pluged in 
my bad 
thanks all for your help

---

