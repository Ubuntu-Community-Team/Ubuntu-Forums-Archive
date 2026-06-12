---
title: "LAMP Cannot Connect Outside of my House"
date: 2007-10-27
forum: General Help
---

### Post by HaXiT on 2007-10-27
Hello,
I can't connect to my LAMP from outside my house. I used many methods, they work in my house but no outside. Can anyone help. Thanks in advance.

BTW: this is the link if you want to test out: [http://haxit.sytes.ent](http://haxit.sytes.ent)


Thanks
HaXiT

---

### Post by andhar on 2007-10-27
sounds like an issue with your router, make sure the IP and port is properly forwarded.

---

### Post by HaXiT on 2007-10-27
OK, i think i figured it out. Sory about the post. If it doesnt work, ill post a reply telling that. Thanks you soo much though :)

---

### Post by #Reistlehr- on 2007-10-27
most likley your ISP blocking port 80.

If you add a new listen port in apache's config restart, tell your router to forward the new port to your ip of the lamp server, you should be able to connect on the new port.

---

