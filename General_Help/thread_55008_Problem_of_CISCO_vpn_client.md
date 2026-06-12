---
title: "Problem of CISCO vpn client"
date: 2005-08-07
forum: General Help
---

### Post by honghai on 2005-08-07
Hi guys, I have a problem with cisco vpn client. When I was using Warty with Kernel 2.6.8, this vpn client was working perfectly with a patch of interceptor.c. After I switched to Hoary with kernel 2.6.10-686, I can't get it to work. 

The version of the vpn client is 4.6.00.0045-k9. After I installed it with the patch and started it, everything was ok, and I can ping these websites. But when I pick up my firefox to go to the website, it always shows "wait for blabla". After several minutes, firefox complains that "can't connect to blablabla". The strange thing is I can use gaim and SOMETIME thunderbird to receive email.

I think maybe there is some problem with the port 80 or?? ](*,) 

Has anybody got such a problem?

---

### Post by honghai on 2005-08-27
[QUOTE=honghai]Hi guys, I have a problem with cisco vpn client. When I was using Warty with Kernel 2.6.8, this vpn client was working perfectly with a patch of interceptor.c. After I switched to Hoary with kernel 2.6.10-686, I can't get it to work. 

The version of the vpn client is 4.6.00.0045-k9. After I installed it with the patch and started it, everything was ok, and I can ping these websites. But when I pick up my firefox to go to the website, it always shows "wait for blabla". After several minutes, firefox complains that "can't connect to blablabla". The strange thing is I can use gaim and SOMETIME thunderbird to receive email.

I think maybe there is some problem with the port 80 or?? ](*,) 

Has anybody got such a problem?[/QUOTE]

This problem was solved by using the new version 4.6.03.0190. It works perfectly for me under kernel 2.6.12.4 :-P

---

