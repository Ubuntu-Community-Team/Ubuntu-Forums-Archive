---
title: "phpBB stmp Server"
date: 2007-01-18
forum: General Help
---

### Post by weirdlookinguy on 2007-01-18
Hey!  I'm trying to set up a small website, hosted on a computer in my own home.  It's not for a business or anything, but rather just for fun.  I set up a forum using phpBB and although the forum is working fine, nobody can register because phpBB has no outgoing smtp server!  All I need is an smtp server, I would use GMail but their smtp server uses different ports and SSL!  Can anyone help me?  All I need is an smtp server, perhaps there is free webmail that has an smtp server I could use?  All I need is smtp, that's all.

weirdlookinguy

---

### Post by dcstar on 2007-01-18
> **weirdlookinguy said:**
> Hey!  I'm trying to set up a small website, hosted on a computer in my own home.  It's not for a business or anything, but rather just for fun.  I set up a forum using phpBB and although the forum is working fine, nobody can register because phpBB has no outgoing smtp server!  All I need is an smtp server, I would use GMail but their smtp server uses different ports and SSL!  Can anyone help me?  All I need is an smtp server, perhaps there is free webmail that has an smtp server I could use?  All I need is smtp, that's all.

weirdlookinguy

Install the **postfix** package.

---

### Post by weirdlookinguy on 2007-01-18
It's installed.  Telling phpBB to not use a smtp server fails too.

---

### Post by dcstar on 2007-01-18
> **weirdlookinguy said:**
> It's installed.  Telling phpBB to not use a smtp server fails too.

Well, if it is installed and running then you have a SMTP server running on your system.


The command: ```
telnet localhost 25
``` will show if it is running.

---

### Post by weirdlookinguy on 2007-01-18
Thanks, I'll try that when I get home.  However, Postfix is installed but it is not configured, does it have to be?  I went into terminal and typed apt-get install postfix, it said the latest version was already installed (i'm on 6.10 Edgy).  What else do I need to do?

---

### Post by weirdlookinguy on 2007-01-18
nope, running telnet localhost 25 gives me this: 

"Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused"

---

### Post by dcstar on 2007-01-18
> **weirdlookinguy said:**
> nope, running telnet localhost 25 gives me this: 

"Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused"

Try it again with the IP address of the server, if it still gives the same result then something is either stopping the SMTP server from starting or blocking that port.

---

### Post by weirdlookinguy on 2007-01-18
Hey, trying it with the server's address on my network (192.168.0.2) gives me the same result.  When I go into terminal and apt-get install postfix, it says it can't install amavisd (errors were encountered processing amavisd-new).  Help?  When I go into terminal and type  "postfix", it says:

postfix: fatal: open /etc/postfix/main.cf: No such file or directory

---

### Post by dcstar on 2007-01-19
> **weirdlookinguy said:**
> Hey, trying it with the server's address on my network (192.168.0.2) gives me the same result.  When I go into terminal and apt-get install postfix, it says it can't install amavisd (errors were encountered processing amavisd-new).  Help?  When I go into terminal and type  "postfix", it says:

postfix: fatal: open /etc/postfix/main.cf: No such file or directory

Well, the first thing is to install the package correctly , go into Synaptic and remove/re-install it.

---

### Post by iSplicer on 2008-03-03
I would please like some further discussion on this topic. After installation of Postfix, what do I enter during phpBB isntallation where I am required to enter the SMTP server information and login details? I am new to this so help would be greatly appreciated!

Thankyou!

---

