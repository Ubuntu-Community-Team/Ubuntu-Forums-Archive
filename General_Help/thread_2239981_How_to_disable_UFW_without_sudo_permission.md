---
title: "How to disable UFW without sudo permission"
date: 2014-08-17
forum: General Help
---

### Post by gio4 on 2014-08-17
Hello, so I locked myself out of my server due to the firewalls, long story short, I managed to be able to log in with another user but that user doesn't have sudo permissions.  I was trying to run the command "sudo ufw disable" but I wasn't able to since I did not have permissions.

So I was wondering if there was a say I could disable the firewall or maybe open a port in the firewall without having sudo permissions?

I also have access to the server with this user, I only have access to the SSH.

Thanks!

---

### Post by deadflowr on 2014-08-17
If i understand you are accessing the server with ssh through the second non-admin user?
If this is correct from the ssh session could you try to su into your user, which should give you your users rights, sudo et al.
simply
su <username>
it'll ask for that users password, and from there you can run whatever sudo command you want.
to end type exit, and you will be returned to the original user logged in through ssh.

But, no, there is no way to change ufw without some form of root access(sudo).

---

### Post by gio4 on 2014-08-17
I ran into another problem, I am using Java iKVM Viewer to be able to access my server, but it seems that toggling caps on and off is bugged.  Caps are off in my keyboard but it still types in caps.  It seems like it has a weird pattern too.  Some times I doubt tap caps and caps are off, some other times its still on.  Its kind of hard to explain, hopefully I explained enough to make some sort of sense.  It is not my keyboard either, I tested it on other places other than that program and it works fine.

Got any idea on what I could do?  My password is a combination of lower caps, caps, and numbers.

---

