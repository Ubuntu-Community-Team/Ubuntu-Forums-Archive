---
title: "how to use laptops when home dirs are on NFS server"
date: 2007-01-08
forum: General Help
---

### Post by amagi on 2007-01-08
I have been looking into the following problem for a while and now I hope I can get some opinions of others on what the best practices are. The situation is as follows:

A server is available on the network which stores the user accounts (ldap) and the home directories (NFS).
When a user is connected to the network there is no problem, the server is available so also the login details and home directory are available.
However, now we have a laptop user who also needs to work at clients. When he is at a client the ldap server is not available and even worse, the whole home directory is not available.

This seems like quite a standard setup as a lot of companies use laptops. What I would like to know is what solutions are available for linux to overcome this problem. I.e. make the home dir and login info available 'offline'?

---

### Post by kj1h234lkj1234 on 2007-01-08
Perhaps the laptops establish some sort of VPN with the server and access the directories that way?

There's no way they're sending that sort of info plaintext across the Internet into a potentially hostile network... VPN seems to be the logical solution.

---

### Post by amagi on 2007-01-08
Thanks for the reply, but what I mean is a bit different. When you have a laptop you simply do not always have a network connection. You might be working from the train, at your house where you do not have a connection to your network. In these situations you need some sort of caching mechanism where your home folder is kept locally on your laptop but as soon as you get back to your netwerk gets synchronised with the server version of your home folder.

I just read so little info on this on the internet. Everytime people talk about linux for enterprises they talk about webservers, email servers, etc. but almost nowhere is more info on how to manage accounts, home folders etc. which play nice with laptop users. I might be looking in the wrong place so I just hope to get more info here through this posting

---

### Post by kj1h234lkj1234 on 2007-01-08
Ahh, sorry for misreading your post.

That is a good question, I have no clue how "roaming" and "local" profiles work in the Linux world. :-k

---

