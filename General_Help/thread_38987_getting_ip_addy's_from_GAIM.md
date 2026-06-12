---
title: "getting ip addy's from GAIM"
date: 2005-06-02
forum: General Help
---

### Post by Digitallysick on 2005-06-02
how do i get ip addy's through gaim? i used to do it in icq99 for Windowz, I am just wondering  if i have to have a plugin, or what ? i am welcome to any ideas

---

### Post by Arthemys on 2005-06-02
What do you mean, do you want to get the IP address of whom you're talking to?

---

### Post by betrayed on 2005-06-02
For people on aim that will not be possible unless you direct connect to talk to them. For icq you can just look at their info and if they have not blocked it it will be shown there

---

### Post by Arthemys on 2005-06-02
Silly centralized aol services.

---

### Post by Digitallysick on 2005-06-05
what about yahoo, will it be the same way?? i guess netstat wouldn't show me the users ip, probably just the yahoo servers ip?

---

### Post by Arthemys on 2005-06-05
[QUOTE=Digitallysick]what about yahoo, will it be the same way?? i guess netstat wouldn't show me the users ip, probably just the yahoo servers ip?[/QUOTE]
Exactly, you would need to establish a direct connection to the other person using something like AIM's "Direct Connect" feature, which for me never works. I would hope it's never used for nefarious purposes. ;)

---

### Post by zafar on 2005-06-05
[QUOTE=Arthemys]Exactly, you would need to establish a direct connection to the other person using something like AIM's "Direct Connect" feature, which for me never works. I would hope it's never used for nefarious purposes. ;)[/QUOTE]

If you are behind a router, go into Gaim Preferences > Network and then uncheck "Autodetect IP Address" and then put in your public IP in the textfield. Then go in your router and open up port 5190 for both tcp and udp. After that, you should be able to Direct Connect to other people. When you try it says "Attempting to connect to *username* at *ip: port* for Direct IM."

---

### Post by Arthemys on 2005-06-06
[QUOTE=zafar]If you are behind a router, go into Gaim Preferences > Network and then uncheck "Autodetect IP Address" and then put in your public IP in the textfield. Then go in your router and open up port 5190 for both tcp and udp. After that, you should be able to Direct Connect to other people. When you try it says "Attempting to connect to *username* at *ip: port* for Direct IM."[/QUOTE]
Tried that, always gets borked cause someone isn't smart on their end or I end up with someone stealing the port from me on the NAT box.

---

