---
title: "Chown command after Lamp install - is it necessary?"
date: 2004-11-23
forum: General Help
---

### Post by filattiera on 2004-11-23
Good afternoon to everybody.

I have installed apache2, php and mysql from apt-get (Synaptic).

Well, after this I have configured the config file and changed the mysql password and users.

I have done also:
chown -R root:mysql usr/sbin
chown -R root:root usr/bin

But I have an error under phpmyadmin due to permission problem.  I think that it depends on the above commands.
Are these command necessary?
If  not, as I can return to the old permission on these directory?

In other words, which are the correct permission for the usr/sbin and usr/bin?

Thanks.
Luca.



 :!:

---

