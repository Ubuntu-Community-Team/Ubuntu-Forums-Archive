---
title: "Can t connect some pages"
date: 2005-08-14
forum: General Help
---

### Post by alanrr_sr on 2005-08-14
Hi,
I've installed Ubuntu, but I can not connect to some address in firefox. Some examples, mail.yahoo.com, [www.yahoo.com](www.yahoo.com), [www.submarino.com.br](www.submarino.com.br). Some times, (1 in 30) I am able to open the page, but most of the time they fail to load. I tryed to disable ipv6 on firefox, but it didn't work . I tryed to disable kernel ipv6, but it didn't work too.
I tryed to connect to yahoo from links to, and I have no success. So, I tryed connecting using telnet, and I have the problem too.
I have no firewalls, and my connection is fine, because i can connect to others sites, at the same time, with no problem.
One more example. After i type yahoo address, firefox shows "Waiting mail.yahoo.com", and after some time, connection expires.

Any help??

PS: I tryed booting knoppix, and I don't have this problem with it, at the same computer, at same connection (pppoe)

---

### Post by invalid on 2005-08-14
Is it just firefox that you are having problems with?

Do you get the same problems using a browser like Konqueror or plain Mozilla?

Can you ping the address?

Can you get there by using the IP instead of a hostname?

---

### Post by alanrr_sr on 2005-08-14
No, I am having problem with links and raw telnet to port 80  too. I didn't try another browser because I trust in raw telnet ;), and since every one (firefox, links and telnet) give me the same answer.....

I can ping any address, fast and without any problem.... Using telnet, I can connect to host, send a http request, but i never receive the page..., with links and firefox, same thing...the page never arrives.

I've tryed ip and hostname, and there is no diferrence..just no response... The strange thing is I can connect to a lot of pages without problem.... but some pages is just impossible.

My route table is ok, my resolv.conf too. 

It's the first time i see that in my linux way of life...

Again... I disabled ipv6 on firefox, and ipv6 on modules (I am pretty sure because I can't find ipv6 when I run lsmod  ;-)  ) 

Waiting help..before give up ubuntu.... pleaaaase..i loved it!!!

PS: I saw one thread with the same problem at old ubuntu... unforntunatelly, without answer [http://ubuntuforums.org/archive/index.php/t-1970.html](http://ubuntuforums.org/archive/index.php/t-1970.html)

---

### Post by alanrr_sr on 2005-08-18
No solution?? No ideas?? Can I drop ubuntu??

Thx

---

### Post by heimo on 2005-08-18
[QUOTE=alanrr_sr]No solution?? No ideas?? [/QUOTE]

Put one computer between your router and Ubuntu box, listening network with tcpdump or ethereal and watch where it hangs. :-/ Yeah, I know - lot's of work, maybe for nothing. You could do that locally too, at first. May give hints. Seems a bit weird problem.

[QUOTE=alanrr_sr]
Can I drop ubuntu??[/QUOTE]

That's legal, but not recommended. ;)

---

