---
title: "locked out"
date: 2007-06-14
forum: General Help
---

### Post by jedson3 on 2007-06-14
I locked myself out of my system. When I booted up this morning a message popped up about how there was something wrong with my home/.dmrc file. It needed to be set at 644 for permissions. I had trouble finding a .dmrc file using a ls -a command. But I went ahead and tried to chmod that address to 644. I ended up changing the permissions in the home directory to 644. (ARRRGG). So now of course I can't execute anything. I can't solve the underlying problem which is that I need a re-built left hemisphere in my brain. But is there anyway that I can now get to a command prompt in my installed system (I am working off the CD for UBUNTU now) and change the permissions in my home file back to 755 – which I think is the right default? Or maybe a way to install a new Ubuntu os off my CD under my old data files?

PS What is it with that .dmrc file anyhow??? 

jedson

---

### Post by warcriminal on 2007-06-14
This article actually shows you how to reset the password in linux, but what you need to follow is the "single-user mode" instructions to get you to the command prompt level so that you can issue commands.

[http://www.goitexpert.com/entry.cfm?entry=Reset-Linux-Password](http://www.goitexpert.com/entry.cfm?entry=Reset-Linux-Password)

---

### Post by jedson3 on 2007-06-14
Very cool. That worked. Good to see my data back. Also, it seems like a useful thing to know for future reference. Thanks. 

jedson

---

