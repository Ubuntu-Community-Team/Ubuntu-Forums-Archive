---
title: "Remote Desktop - Please Help Me Set It Up"
date: 2007-03-12
forum: General Help
---

### Post by Brian Boyko on 2007-03-12
Hello.  I would like to be able to access my Ubuntu-based desktop at work.  SSH is nice, but I'd like to be able to access the full UI.  

The computer at home is running Ubuntu Linux; the computer at work is running Windows XP.  

Anyone know how I can pull this off?

---

### Post by siciliancasanova on 2007-03-12
[This thread]("http://ubuntuforums.org/showthread.php?t=380240&highlight=remote+desktop") shows what I use to do mine.

---

### Post by Brian Boyko on 2007-03-13
I've enabled Remote Desktop, and set up an account with DYNDNS but I think I may be screwing up the portforwarding. :(   I can't seem to telnet or ssh or ftp into my box.  I keep getting "connection refused" errors which makes me think DYNDNS is hitting my router and not my home box. 

-- Brian.

---

### Post by Brian Boyko on 2007-03-13
Here's the error I get. 

XXXXX@XXXXX-desktop:~$ ftp XXXXX.homelinux.com
ftp: connect: Connection refused
ftp> 


Same thing with Telnet.

---

### Post by alamba on 2007-03-13
Yes, dyndns is hitting your home router since the public IP interface is on your home router. You would need to enable port forwarding for 22 (ssh) on the router to your ubuntu box.

A

---

### Post by Brian Boyko on 2007-03-13
> **alamba said:**
> Yes, dyndns is hitting your home router since the public IP interface is on your home router. You would need to enable port forwarding for 22 (ssh) on the router to your ubuntu box.

A

Damn; the problem is that I thought I -have- enabled port forwarding for 22, 21, 5900, etc...

-- Brian.

---

### Post by alamba on 2007-03-14
What make and model is your router?

A

---

