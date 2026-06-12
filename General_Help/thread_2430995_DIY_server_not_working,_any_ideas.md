---
title: "DIY server not working, any ideas?"
date: 2019-11-10
forum: General Help
---

### Post by jasper1378 on 2019-11-10
Hello all, 

I'm creating a personal server on an old desktop. I'm following this article [https://www.instructables.com/id/Set-up-your-very-own-Web-server/](https://www.instructables.com/id/Set-up-your-very-own-Web-server/). It's all set up but when I try to access it through my browser using the domain or public ip, it just says connecting for a long time and then chrome says "took to long to respond". It works when I type the private ip into the address bar though. Any ides on how I could fix this?

---

### Post by HermanAB on 2019-11-10
To debug it, you need a test method that will give you meaningful error messages.

One simple way is to install 'telnet', then do:
$ telnet localhost 80

See what happens and google the error messages.

---

### Post by jasper1378 on 2019-11-10
Thanks, I'll try it.

---

### Post by ppbiju on 2019-11-10
Do share more details about your server
1. OS 
2. your server meant for which type of server ie file server, web server etc.
3. Details about the modem make name model name etc.

if you provide these details it would be easier for give a solution

from your post I think it would be problems with any of the following 
1. may be your internet connection is slow
2. the configuration of your modem may not be correct set port forwarding is to be set correctly
3. your firewall configuration in your client / server system may block 

check above and replay

---

