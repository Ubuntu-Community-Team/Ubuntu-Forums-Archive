---
title: "ubuntu as server"
date: 2004-10-26
forum: General Help
---

### Post by Razvan on 2004-10-26
Hi folks,

is tried to set up a vsftpd server to be able to suck my files,when im at school or somewhere else,

i disallowed anonymous and have it use port 20 & 21

i sit behind a dlink router/firewall thing and told it to farward port 20 & 21 requests to my box

so when I try to acces it from my own box (either with 127.0.0.1 or my DYNdns) it works, also from other local boxes

but any body out there cant acces my PC, SSH didn work neither, allthough I also told my router to make my ssh accesible

btw. other boxes can be accesed via ssh from outside (with changed router settings)

my hosts.allow is only ALL: ALL and my hosts.disallow is empty =D>


thanks for any help!

EDIT: and sorry for my confusin english :-)

---

### Post by JProgrammer on 2004-10-26
It might be your dlink modem rather than Ubuntu in this case I know my Billion router/firewall in addition to forwarding these ports also has another page of configuration just on those standard ports for ftp and web servers etc check it out and make sure you it isn't blocking these ports by default and not even getting to your NAT firewall

---

### Post by Razvan on 2004-10-27
thanks, but it runned with another box, when we just changed the IP to which it shall forward the requests.

and agian, sorry for my english :-)

EDIT : i'll try to find some hints in the log file of the router...but just now im at school so this wint be 2 soon

---

### Post by luiska on 2004-10-28
Hi 

Something that I noticed was that the SSH server isn't installed by default. So when you try to access the machine by SSH you will get no connection or connection refused.

Hope it helps
luiska

---

### Post by shufla on 2004-10-28
Hello,

[QUOTE=Razvan]thanks, but it runned with another box, when we just changed the IP to which it shall forward the requests.

and agian, sorry for my english :-)

EDIT : i'll try to find some hints in the log file of the router...but just now im at school so this wint be 2 soon[/QUOTE]

You have to know, that all ubuntu servers are configured only for local connections. Paste here execution of ```
lsof -ni 4 | grep LISTEN
``` for further analysis..

Best regards,
Lukasz Nowak

PS. No-native english speakers, like me - do we have to be sorry all the time for our english or not? ;) We are doing our best!!

---

