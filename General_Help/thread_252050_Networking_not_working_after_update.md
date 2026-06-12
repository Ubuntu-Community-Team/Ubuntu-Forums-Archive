---
title: "Networking not working after update?"
date: 2006-09-06
forum: General Help
---

### Post by tph on 2006-09-06
I've been using ubuntu for some time now, and I've been happy with it, but yesterday I downloaded some updates and went to sleep only to notice that I can't get on my network now. I'm connected to the router directly with a wire, but ubuntu just can't use it even though windows can (writing from windows now).
ifconfig didn't give me an IP and restarting the networking-service or the computer didn't help. Also, when trying to access my router with opera the cpu-load kicked right to 100%.

(I don't remember what the updates where, except maybe mysql5)

---

### Post by marianom on 2006-09-06
Were they libmagick9 or libmysqlclient15off or libssl0.9.8 or mysql-common or openssl?

---

### Post by TDKBacke on 2006-09-06
@tph: Welcome to the club: [http://ubuntuforums.org/showthread.php?t=246557](http://ubuntuforums.org/showthread.php?t=246557) ;)

@marianom: I am quite sure libmagick6 was updated before the network on one of my machines became unusable. But since when does a graphics library affect networking? :confused:

---

### Post by marianom on 2006-09-06
TDKBacke: hi.
Since tph did not remember what packages he updated I just listed the ones that were announced in the Security Forum hoping he could recall and start searching how to fix it from there.

Hope you guys can fix this issue asap!!

---

### Post by tph on 2006-09-07
I don't know if it helps, but I know have imagemagick installed (with various libs), mysql with various client libs (running local test-server for php+mysql) I also think I've got libssl installed, I'll try removing some of those packages and see if I can access my network.

---

### Post by marianom on 2006-09-07
It seems you've installed the same security fixes I have pending right now.

To rest the case I should install them now and see if my network fails upon startup but I'm afraid I'm not brave enough!!

---

### Post by TDKBacke on 2006-09-10
It would be nice to know, whether marianom was not brave enough to update or whether he updated and - as a result - isn't able to tell us about it now. ;)

Anyway, I guess I have to spend this sunny sunday reinstalling and configuring kubuntu. Hopefully the "broken" packages aren't used during an internet install ...

---

### Post by tph on 2006-09-11
Ok, I'm on my network with ubuntu again, seems some update made it so that my pc can't communicate with the dhcp, but I just set ips manually and voila, will look more into this though.

---

### Post by marianom on 2006-09-12
Hi.
Sorry for the late post but this weekend my boy was born and a proud father has no time for computers!!!.

Anyway, I installed all recommended updates and after rebooting several times (just to be sure) I have no issues to report regarding the packages.

---

