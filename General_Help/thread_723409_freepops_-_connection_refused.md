---
title: "freepops - connection refused"
date: 2008-03-13
forum: General Help
---

### Post by ogee on 2008-03-13
I have installed freepops on  my HP Pavilion notebook running Ubuntu 7.10 from the Blackmoon package (ver 0.2.6-1) and updated the Lua's. 
I then created a new user in Evolution making the pop server "localhost" and the smtp server "localhost:2500". No problem with the install or with creating a new user but when I do a send/receive I get the error message
     "Could not connect to localhost: connection refused"
Has anyone run into this or have any ideas ?

---

### Post by eriqjaffe on 2008-03-13
localhost:2500 is just for the POP3 server, you'll have to use whatever SMTP server your ISP provides for you.

---

### Post by ogee on 2008-03-13
eriqjaffe,
I  changed the smtp to my centurytel address and I still get the same connection refused error message. I think it's the pop3 that's giving me the problems. 
thanks

---

