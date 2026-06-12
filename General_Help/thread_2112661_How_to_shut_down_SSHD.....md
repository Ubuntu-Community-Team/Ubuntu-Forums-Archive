---
title: "How to shut down SSHD.... ?"
date: 2013-02-05
forum: General Help
---

### Post by lynxus on 2013-02-05
Hi guys,

I am pulling my hair out with Ubuntu at the moment ( I'm a red-hat guy )

How on earth do i shut down the SSHD service?

I try:
stop ssh
stop sshd
/etc/init.d/sshd stop

etc etc etc NOTHING!!! is stutting it down.

I simply want to shut it down, edit the config file and enable again ( Via a console )

Also,
Does anyone know where its "real" config file is? There seems to be some odd link between ssh and sshd ?

This is confusing the hell outta me :(

---

### Post by dino99 on 2013-02-05
deleted, sorry wrong thread.

---

### Post by Habitual on 2013-02-05
```
sudo service sshd stop
```

/etc/ssh/sshd_config ?
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by lynxus on 2013-02-05
> **Habitual said:**
> ```
sudo service sshd stop
```

/etc/ssh/sshd_config ?
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

service doesnt work in Ubuntu?

Anyway,
Turns out that the service *was* stopped.. But for some reason ubuntu keeps the SSH session open ( Rather than kicking me off )

Grr.

Anyway,
Any ideas where the "actual" config file is?
I see two and both seem to be doing something.

---

### Post by Doug S on 2013-02-05
> service doesnt work in Ubuntu?well, it does if you are anywhere near up to date. However the command is:```
sudo service ssh stop
```not "sshd". For older versions this should work:```
sudo /etc/init.d/ssh stop
```For config file locations, I only know of where Habitual mentioned. Perhaps list the two locations and file names you found so as to help us help you.
 
Edit: By the way, and as mentioned in the next posting below, stopping sshd does not terminate an exisiting session, it just prevents any new ones. (I tried it and came back to comment, and noticed the below post).
If desired, and if simply logging out is not an option, you will have to manually kill the existing session. Example:```
doug@doug-64:~/init$ ps aux | grep ssh
root     24550  0.0  0.1 134512  6072 ?        Ss   Jan29   0:01 sshd: doug [priv]
doug     24733  0.0  0.0 134648  2360 ?        S    Jan29   0:07 sshd: doug@pts/0
doug     26407  0.0  0.0   9384   880 pts/0    S+   08:31   0:00 grep --color=auto ssh
doug@doug-64:~/init$ sudo kill 24733
[sudo] password for doug:
```

---

### Post by iponeverything on 2013-02-05
> **lynxus said:**
> service doesnt work in Ubuntu?

Anyway,
Turns out that the service *was* stopped.. But for some reason ubuntu keeps the SSH session open ( Rather than kicking me off )

Grr.

Anyway,
Any ideas where the "actual" config file is?
I see two and both seem to be doing something.

Stopping the service under red hat does not kick you off either, it just stops the listener that is forking the children to handle the request. 

 /etc/ssh/ is where your configs live - there one for client and one for the server.

---

### Post by lynxus on 2013-02-05
> **iponeverything said:**
> Stopping the service under red hat does not kick you off either, it just stops the listener that is forking the children to handle the request. 

 /etc/ssh/ is where your configs live - there one for client and one for the server.

Oddly every redhat box I have kicks me off when i service sshd stop.

Anyway,
Thanks for the reply.

Finally got it all working. :) ):P

---

