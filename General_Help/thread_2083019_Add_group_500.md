---
title: "Add group 500?"
date: 2012-11-11
forum: General Help
---

### Post by Vezzel on 2012-11-11
Hi!
 
I have to access som folders from a disk which has been attached to a NAS. some of the folders can I acces - no problem. But some of the folders I do not have the right persissions to read. When I read the permissions of the folder, user 502 owns the folder and have read and write access. Group 500 has read-access.
 
How can I get access to the folder? Read-acces is enough. I think to make a group with ID 500, and then I should be able to read the folder. But I dont know how to do it.
 
Running Ubuntu Live CD v12.
Could someone guide me? (I'm faily newbie to Ubuntu...)
 
Regards Vezzel - Denmark

---

### Post by Lars Noodén on 2012-11-11
Here is one way to create a group with the gid of 500

```

sudo groupadd -g 500 nas
sudo gpasswd --add vezzel nas

```

You'll have to log out or start a new terminal for the changes to take effect.

---

