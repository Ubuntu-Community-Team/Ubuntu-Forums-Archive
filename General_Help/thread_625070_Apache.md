---
title: "Apache"
date: 2007-11-27
forum: General Help
---

### Post by knutschr on 2007-11-27
I wolkl like to make my machine a server.
I don't know anything about this.
I want to do it as I will be able to give movies of GB size to my friends.

I installed apache2 with Synaptic.

Trying to start it;
> knut@Knut:~$ sudo apache2
[sudo] password for knut:
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

What do I do wrong?

---

### Post by hsweet on 2007-11-27
Installing Apache is just one link in a chain.  
Do you have a registered name?
Do you have a static IP?
Can you set up your own name server so other people can find you?

sudo apache2 does not mean anything.  When you install it it usually runs in the background and the daemon starts automatically.  Check your running processes.

Or better yet, try this.  In your browser's address window type "http://localhost"
If the install worked, you will see a default page.

If that much is working, you can register a name, persuade (means $) your ISP to give you a static IP, learn bind and you are in.

I would recommend that you read a book.  It's not that hard, but there is a lot of pieces.

Oh yeah, you also have to learn how to restrict access so the whole world does not download your stuff.

Or if you want the whole world to do that, why can't you just set up some file sharing system?

---

