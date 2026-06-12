---
title: "Feisty, internet dsl connection trouble"
date: 2007-10-18
forum: General Help
---

### Post by ReyCazador on 2007-10-18
I used pppoeconf to config my ADSL modem on my Dell Inspiron B30 notebook. It worked perfectly for 2 days third day I try the pon command in the terminal and I get this 
" /usr/sbin/pppd : In file /etc/ppp/peers/provider: unrecognized option '/dev/modem/' 

Somebody please help me. Thank you very much

---

### Post by Samhain13 on 2007-10-18
"pon dsl-provider" ?

---

### Post by ReyCazador on 2007-10-18
Dude thanks for reminding me, it now seems to connect but then the browser does not oad pages.
I used plog it says
Serial Link appears to be diconnected.
Connect time 2.5 minutes.
Sent 0 bytes, recieved .1065 bytes.
restoring old default route to eth0
Connection terminated.



So what now, help again, Please. Thanx

---

### Post by ReyCazador on 2007-10-18
Guys please help, I really like Ubuntu but I cant work with it as it is , so please help.

---

### Post by Samhain13 on 2007-10-18
Funny I got the same message a while ago, "Serial Link appears to be diconnected." However, I'm suspecting that this has to do with my modem (or ISP even) and I have no further knowledge on that, sorry.

Anyway, I just waited a bit and tried "pon dsl-provider" again until "plog" gave me a different message that indicated my connection information.

I'm really sorry I can't be of any further help.

---

