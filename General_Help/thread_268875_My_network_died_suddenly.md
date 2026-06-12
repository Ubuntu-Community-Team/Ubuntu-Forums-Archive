---
title: "My network died suddenly"
date: 2006-09-30
forum: General Help
---

### Post by Inferno. on 2006-09-30
I always search in internet when something happened with my linux, but I can't think how to solve this problem. I was eating, and when I finished i went to my computer, open firefox, entered in my usual forums and then I saw that mercury didnt work, the azureus stops uploading, a couple of seconds later firefox show me a error message.

I can't see any webpage, can't make ping with the console. I tried to reset the service (network-admin, I changed from dhcp to static, clicked ok, waited, and then I changed again to dhcp (I was hoping that this will fix the problem, because I dont know how to do it by console). Nothing happened. So... i rebooted my pc :(

The problem is still here. So i cheched my mother's computers and she have a connection. The router is working, but my machine dont. So I open my virtual machine / vmware with XP just to see if i cant connect to my shared folders... and here i am, i'm posting this with my fake xp inside ubuntu (Where i cant do anything related to internet) ._.

I have fluxbox, ubuntu 5.10, i didn't install anything, i didnt do anything, I was just checking two forums that I always see and then i realize that mercury didn't connect me to the msn network... then the azureus.. then firefox.

Anyone? (Sorry for my english, I have writed the best that I could)

---

### Post by tagra123 on 2006-09-30
Try turning the router off and then back on. 

Reboot the computer and see if it starts working.

---

### Post by Inferno. on 2006-10-01
Well, It's fixed. I wrote this and it worked

ifconfig eth0 down
route del default
ifconfig eth0 192.168.0.10 netmask 255.255.255.0
route add default gw 192.168.0.1

Anyone knows why this happened?

---

