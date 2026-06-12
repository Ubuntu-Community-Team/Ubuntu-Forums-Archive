---
title: "permission denied to root user"
date: 2014-03-07
forum: General Help
---

### Post by tankarakesh.38 on 2014-03-07
Hello, 
Recently i installed Ubuntu 13.10.  I created no users except one ie root as "rakesh". which changing certain permission, I unable to change. However "sudo apt-get update" was working with my general password. But I am unbale to change certain thing. It is saying Permission denied. asking for root user.

Please help me.

---

### Post by lisati on 2014-03-07
Ubuntu comes with the user "root" disabled by default, and the first user you create (usually during installation) has admin privileges. Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tankarakesh.38 on 2014-03-07
Thanks for your reply. 
I followed as shown but still permission is denied

---

### Post by coffeecat on 2014-03-07
You need to tell us exactly what you are doing which causes the permission denied error to appear. If you are able to run "sudo apt-get update" as your rakesh user, then rakesh is able to elevate to root privileges just fine. Which would mean that whatever is causing the permission denied error is a special case on your system.

Or do you mean that you are no longer able to run "sudo apt-get update" since changing something on your system? Your first post is not clear. 

Please also post the exact and full error message.

---

### Post by ajgreeny on 2014-03-07
You still have not made it clear whether or not you enabled the root account on your system so please tell us exactly what you did
If you did enable that account, there will not be many users here who have experience to help you, as it is something that is neither recommended nor necessary, hence the link from lisati telling you how things are done in Ubuntu

---

