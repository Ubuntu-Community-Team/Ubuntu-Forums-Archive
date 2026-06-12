---
title: "vmware server and remote connection"
date: 2007-02-21
forum: General Help
---

### Post by luzi82 on 2007-02-21
I could not remote connect to the vmware server using the console from any machine, even the host machine ( using the remote method and type localhost ).  I have searched the web for 2 hours but no solution was found.

However, I finally solved the problem by installing inet.

apt-get install inet

It seems that vmware require inet to receive connection.

I wish my solution would be helpful

---

