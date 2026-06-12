---
title: "Dell M5200 Printer Help"
date: 2007-05-07
forum: General Help
---

### Post by mbb102488 on 2007-05-07
I am having an absolute hard time getting a Dell M5200 to work over a network. Can anyone give me some direction as to what I should do, I am on a school network and the printer is connected though a server I believe. 

Thanks

---

### Post by lkfung on 2008-01-02
I had the same problem when I added the automatically detected printer.
But I finally fixed it by adding the printer as a network printer(TCP/Socket, HP....), then type the IP address of the printer in the Host field and leave the Port 9100 unchanged. 
In this way, the printer works.

Hope this will help.

---

