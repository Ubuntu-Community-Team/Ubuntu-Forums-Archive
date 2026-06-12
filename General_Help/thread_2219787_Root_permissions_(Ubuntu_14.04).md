---
title: "Root permissions (Ubuntu 14.04)"
date: 2014-04-25
forum: General Help
---

### Post by mike176 on 2014-04-25
Hello
Why do I get a message saying "you are not the owner therefore you cannot change permissions". I can't find where I tell Ubuntu I am the owner.
Thanks
Mike

---

### Post by grahammechanical on 2014-04-25
The message says it all. System files and folders are not owned by us, the user. They are owned by Root. It is the way that Linux works. When we use root/administrator privileges to create or copy and paste files/documents then those files also become owned by Root because we are Root at the time we are running those tasks.

Linux works this way to prevent malicious code from changing system configuration files to allow the malicious code to do even more damage to the operating system. Ubuntu goes one step further by disabling the Linux Root account. It is very dangerous to run an operating system as Root or administrator.

In ubuntu when we need to do something that requires root or administrator privileges we are asked to authenticate. Then, if we are the administrator, we put in our password and that authenticates the action. It is the password that we created when we first installed Ubuntu. When we use Ubuntu we use it as a standard user even though we are the administrator. We only use Ubuntu as administrator for those tasks that need administrator authentication. Ubuntu protects us.

Why do you want to change the permissions and what files do you want to do this to? A little knowledge is a dangerous thing. Explain a little more to us and we might be able to tell how to do what you want.

Regards.

---

### Post by WoodenWalker on 2014-04-25
Sounds like you are trying to edit system files. You might want to be careful with that.... To do it you have to set yourself as root though. But yeah... Always be careful when you are the using the root account.

---

### Post by mike176 on 2014-04-25
thanks for that. i don't want to edit system files, i just wanted to know why i'm not the owner. Still on the steep learning curve after being brain washed by winyouknowwho for the past 35 years.:guitar:Free at last. thank god almighty, free at last!

---

### Post by Bashing-om on 2014-04-25
mike176; Hello,

Perhaps these links will help you in climbing this curve of learning:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://mywiki.wooledge.org/Permissions](http://mywiki.wooledge.org/Permissions)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

I trust this helps. and
[INDENT][INDENT]Welcome to our world - open source -> no secrets
[/INDENT][/INDENT]

---

