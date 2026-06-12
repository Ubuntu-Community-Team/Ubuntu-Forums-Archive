---
title: "Samba4/bind9/dhcp"
date: 2013-06-25
forum: General Help
---

### Post by nappullus on 2013-06-25
[SIZE=2][FONT=arial]Hi,[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]I don't get my head around it.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]I can get bind9 and dhcp to work, so that dhcp updates the dns.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Also the combination samba4 and bind with dlz is working.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]But as soon I try to join samba4 to the one or dhcp to the other I get ERRORs.

[/FONT][/SIZE]
[SIZE=2][FONT=arial]The HowTO SAMBA4 doesnt give me anything for this problem.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]It would be great if someone can give me a hint or a workaround.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]Also, I tried to split these services (dhcp/bind - samba4) on two machines, so that samba4 has his own domain and internal dns and forwarding each other, didn't work out.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]Please Help[/FONT][/SIZE]
[SIZE=2][FONT=arial]
Cheers
nappullus[/FONT][/SIZE]

---

### Post by gordintoronto on 2013-06-26
What version of Ubuntu?

It might help of you described what you want to do. I always use Samba, and I have never needed to use Bind, and I have a mix of DHCP and static IP systems.

---

### Post by nappullus on 2013-06-26
Thanks for so quick reply gordintoronto.


I am using Ubuntu 12.04 LTS server.

I like to achieve a functional Samba4 AD with mixed windows and linux machines.

e.g:
realm: example.org
domain: EXAMPLE

 
Also, I need a DHCP server, which should update the DNS entries in Samba internal DNS or in BIND for all the clients, who don't join the Domain.

I guess I found out what the problem is. Samba and DHCP try to update one zone (example.org) and that's giving me ERRORs.
So, now the question is, what if I create one zone for samba and one for dhcp. Is it possible that each can comunicate to the other?

Or any other solution?

Thanks for help
nappullus

---

### Post by gordintoronto on 2013-06-26
Sorry, I can't help with Server. Desktop is slower and needs more memory, but it can do everything Server can do -- and it's much. much easier to manage.

---

