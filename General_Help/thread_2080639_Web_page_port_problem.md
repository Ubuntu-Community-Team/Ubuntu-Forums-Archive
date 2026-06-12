---
title: "Web page port problem"
date: 2012-11-04
forum: General Help
---

### Post by nicksimpson32 on 2012-11-04
Hi everyone, could anyone point me in the right direction please.
I have installed apache2 on 12 04 lts desktop, 
To see my web page internally/externally I have to follow my [www.mysite.com](www.mysite.com) with the port number.
Without the port number, internally i get my router login page and externally i get a blank page.
Any ideas!!
No other web software installed

---

### Post by pkadeel on 2012-11-04
for local access you need
[http://localhost](http://localhost)

for access within LAN you need to configure apache to listen on the network ip address of the server

access from external sources requires configuration of your router as well.

---

### Post by nicksimpson32 on 2012-11-04
> **pkadeel said:**
> for local access you need
[http://localhost](http://localhost)

for access within LAN you need to configure apache to listen on the network ip address of the server

access from external sources requires configuration of your router as well.

Thank you for your reply and help pkadeel.

---

