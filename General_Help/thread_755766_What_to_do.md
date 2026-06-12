---
title: "What to do?"
date: 2008-04-15
forum: General Help
---

### Post by jhmac77 on 2008-04-15
I have heard that one reason people give up on Ubuntu and other Linux programs is they reach a point they cannot do anything else to correct the problem and they erase the whole thing and go back to Windows.

For example if your not perfect in downloading and installing and you get a mistake note saying you must do it manually.  You go to terminal and put in the information and get a "blank" .  So how do you do it manually.  I guess you have to be a Ubuntu IT to figure it out and unless you get an intelligent answer and complete answer on how to do it, you give up and go back to windows.

Or sometimes like stupid me you erase the install and start all over hoping not to make any more mistakes-HA HA!

This is a major problem with Linux!

Jim

---

### Post by wieman01 on 2008-04-15
Major problem is that most people don't want to learn new stuff. It's less to do with Linux per se.

---

### Post by jhmac77 on 2008-04-15
It says report the error  to whom???  and do it manually how???????????

---

### Post by jhmac77 on 2008-04-15
I cannot copy and paste the message!!!

---

### Post by atomkarinca on 2008-04-15
This is not a problem if you don't want it to be. Most programs can be easily installed via Add/Remove. If you can't find it there and you have to compile the program, it's explained in details in the INSTALL file. If you get errors during the compilation, most probably it means you don't have a package needed and it tells you this. You can easily find that missing package in the Synaptic or on [Ubuntu Packages]("http://packages.ubuntu.com"). And if you can't find anything, just copy the output of the terminal and paste it here. I'm sure there will be someone who has encountered the same problem and solved it somehow.

---

### Post by jhmac77 on 2008-04-15
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.


What to do?

---

### Post by wieman01 on 2008-04-15
Moved back to general help. Please rephrase your question. The first post isn't really clear... What help do you need?

---

### Post by mali2297 on 2008-04-15
> **jhmac77 said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.


What to do?

Is it a support question or are you trying to make some kind of point?

Anyhow, open a terminal and type
```

sudo dpkg --configure -a

```

---

### Post by jhmac77 on 2008-04-15
Thanks!!  That is helpful!
Jim

---

### Post by RJ Hythloday on 2008-04-15
My first 2 attempts an *nix were gentoo and ubuntu 6.10 and I went back to windoz after both attempts, I have been using *nix for a few months now and almost put xp back on the family machine - I found a fix to keep flash from crashing every 5 minutes or it woulda been done.

---

### Post by jhmac77 on 2008-04-15
Now it says I have a broken package and need to go the the broken filter to do what?
How  do I fix the broken package.Where is the broken filter?
Jim

---

### Post by mali2297 on 2008-04-15
Try
```

sudo apt-get -f install

```

---

### Post by jakupl on 2008-04-15
It is very easy. Just do what it tells you. Go to synaptic package manager, press "custom filters", press "broken. You will now see your broken packages.
and do whatever it tells you.

---

