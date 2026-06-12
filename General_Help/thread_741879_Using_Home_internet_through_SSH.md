---
title: "Using Home internet through SSH"
date: 2008-04-01
forum: General Help
---

### Post by wnaBsd8d on 2008-04-01
Hey everyone,

I have a small problem...well at least i think it is a problem

i have set up an ssh server on my home computer..and when i ssh into it from outside my network i can get in fine and see my files and such.

The problem is when i type localhost port 1080 into my firefox socks configuration it dosnt allow me to use my home internet.

any ideas?

i use putty to ssh into my server ...uses port 443 and dynamic forward of 1080

thanks in advance

---

### Post by justleen on 2008-04-01
make sure AllowTCPForwarding is enabled in /etc/ssh/sshd_config

---

### Post by kevdog on 2008-04-01
You have seen this post correct:

[http://ubuntuforums.org/showthread.php?t=723025&highlight=ssh](http://ubuntuforums.org/showthread.php?t=723025&highlight=ssh)

Maybe I could use this post as a starting point to help you.

---

### Post by wnaBsd8d on 2008-04-02
Hey guys thanks for your replies...it seemed i just overlooked something minor and after checking i felt rather stupid....

moving on tho....it seems i cannot sftp into the ssh server using the same port 443..

this works when i am on the computer that has the server

but not from remote locations


any ideas ?

thanks in advance

---

### Post by justleen on 2008-04-02
im assuming you use ```
 sftp -oPort=443 
```
otherwise it wil just use the default port

---

### Post by wnaBsd8d on 2008-04-02
i use filezilla so yeah i set it to ipaddress port 443 SFTP normal login then connect and it never wants to connect

---

### Post by justleen on 2008-04-02
hmm..
ok so putty is set up for forwarding.
you can ssh into your system
other ports are being forwarded correctly, just not sftp?

Anything in /var/log/messages or auth.log?

---

### Post by wnaBsd8d on 2008-04-02
yeah 

i can go on the internet and stuff using localhost port 1080 

but the filezilla when i try and connect is just stubborn i dont know whats going on

its a portable version of filezilla so i dunno

---

### Post by justleen on 2008-04-02
shouldnt you point filezille as well to port 1080 if that is the port you choose to tunnel on?

---

### Post by wnaBsd8d on 2008-04-07
port 1080 from my understanding is the forwarded port not the port of the ssh server

so that port wont work

i have no idea why this doesn't work

theoretically it should...and as i said when i connect to it from home it works...using filezilla i connect on port 443 (sftp protocol) and i works.. (thats on the computer that has the server)

but when i try somewhere else it times out

what to do :(

---

