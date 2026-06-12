---
title: "can anybody help with rsync to another machine?"
date: 2007-06-26
forum: General Help
---

### Post by mdurham on 2007-06-26
Hi, I'm trying to rsync from one machine to another, both running Gutsy. 
I get the error message:
> ssh: connect to host stationg2 port 22: Connection refused

I 'imagine' that I must run 'rsync --daemon' on the receiving end, and open the SSH port 22 on the firewall. Is that correct?
What more do I need to do to make it work? Any ideas?
Both computers can see each other on the LAN.
Cheers, Mike

---

### Post by jynyl on 2007-07-22
Did you find any answer to this?
I have the same problem here.

TIA

---

### Post by jynyl on 2007-07-22
ok - having ssh installed and running on the other machine sure helps :)

---

### Post by mdurham on 2007-07-22
> **jynyl said:**
> ok - having ssh installed and running on the other machine sure helps :)

No jynul, I didn't have any answers. but thank you for the info, I'll give it a try tomorrow.
Mike

---

### Post by fjgaude on 2007-07-22
Yes, make sure you have installed on each machine both ssh client and server. Then all you need is the password.

frank

---

### Post by jynyl on 2007-07-23
Yes, how should I get the password thing set up?

I run a script (with rsync commands in it) on my laptop, and it backs up to my PC, but asks for password at each rsync command.  There must be a convenient but secure way to do this.  (Laptop and PC are on a home LAN.)

TIA

Peter

---

