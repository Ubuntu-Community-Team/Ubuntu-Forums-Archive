---
title: "I set up a server using Ubuntu Server,, but how do I configure it to be acce-"
date: 2013-02-22
forum: General Help
---

### Post by jnLink on 2013-02-22
-accessable globally? A step by step instruction please?

---

### Post by Roasted on 2013-02-22
What is it you want to be accessible? You want to be able to access the terminal in it from anywhere? If so, sounds like a job for SSH. You can forward the SSH port (default is 22, but not a bad idea to change it in the SSH config and then forward that new port). Once the port is forwarded you should be able to do ssh [email]user@external.ip.addres[/email]s, etc. Then you'll get a prompt. Highly recommended you set up SSH keys instead of using regular passwords. Hope this helps.

---

