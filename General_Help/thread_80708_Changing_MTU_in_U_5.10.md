---
title: "Changing MTU in U 5.10?"
date: 2005-10-22
forum: General Help
---

### Post by lehardi on 2005-10-22
Hi!
I read some FAQs about changing MTU. I'd like to change this for etho. But when I type: ifconfig eth0 mtu 1492 I got error: Bad argument. Why this command works for others but not for me?
-- 
LeHardi

---

### Post by TheReaperD on 2007-04-12
First question would be if you added "sudo" to to the beggining of the command.  It should read "sudo ifconfig eth0 mtu 1492".  This does not apply if you have set up and are logged in as root.

---

