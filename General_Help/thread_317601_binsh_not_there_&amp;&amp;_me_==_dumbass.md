---
title: "/bin/sh not there &amp;&amp; me == dumbass"
date: 2006-12-12
forum: General Help
---

### Post by ZmasteR-AES on 2006-12-12
ok so ive been usin ubuntu for ages now and linux for a long time before i started on ubuntu....well i recently got a new lappy and slapped ubuntu 6.06 on and then recently thought heh wot the hell ill upgrade to 6.10,,,,that caused no end of problems but with some help i managed to iron them all out. Now im trying to get beryl to run and installin the ATI drivers (i have a ATI x1100) and with the driver i had to follow a post by malloc where he said to run

mv /bin/sh /bin/SH 
and then back again after install ....which was fine i did that no probs...now im installin the driver again on my lappy cos i uninstalled it outta frustration of beryl still not workin, but this time wen i installed the driver, i FORGOT to switch /bin/SH back to /bin/sh which means now when i boot up in normal or recovery,,,i got no sh which means i cant get into ubuntu....

any help plz guyz? i need my lappy up and runnin ASAP.

TIA

---

### Post by taurus on 2006-12-12
Boot from a LiveCD, mount the partition where / is, and change it back...

---

### Post by ZmasteR-AES on 2006-12-14
not long after posting for help i actually thought,,,,hey how about if i boot to livecd and mount lol....
thx for response anyway..

my main problem now is after pissing around with ATI drivers my GUI has screwed up and i have tried reinstallin drivers, but the top bar of all my windows have disappeared and stick to the top of the screen , i wonder if any has had this problem and is there a way to fix it?

i have attached a screen shot of wot it looks like, help would be appreciated as i cant work very well cos i cant even select objects on the screen without closing the front windows.

TIA

---

### Post by Gustav on 2006-12-14
Press alt+F2 and type "metacity" and see if it helps. (If not, try in a terminal and check the output)

---

