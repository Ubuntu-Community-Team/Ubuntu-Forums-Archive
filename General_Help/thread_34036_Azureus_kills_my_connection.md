---
title: "Azureus kills my connection"
date: 2005-05-13
forum: General Help
---

### Post by SodomizedPeanut on 2005-05-13
I appear to be having a problem with Azureus. The program runs fine, but merely by virtue of running, it kills my connection to the internet. It doesn't even have to be using any bandwidth. As soon as I terminate the program, I can resume using the internet as normal Some very helpful people on the IRC channel suggested that perhaps Azureus was opening too many connections for my router to handle, but I've used torrents with many more connections before (in windows, that is). Does anybody have any suggestions about what might be going on?

Many thanks in advance for any help you might offer.

---

### Post by Maestro23 on 2005-05-13
[QUOTE=SodomizedPeanut]I appear to be having a problem with Azureus. The program runs fine, but merely by virtue of running, it kills my connection to the internet. It doesn't even have to be using any bandwidth. As soon as I terminate the program, I can resume using the internet as normal Some very helpful people on the IRC channel suggested that perhaps Azureus was opening too many connections for my router to handle, but I've used torrents with many more connections before (in windows, that is). Does anybody have any suggestions about what might be going on?

Many thanks in advance for any help you might offer.[/QUOTE]


Hmm... I use Azureus myself in a dual boot setup between XP-Pro and Kubuntu in conjuction with Verizon DSL, have never had Azureus shut itself down or kill the connection.  Did a quick search on **google**, and found this discussion in a forum.  Might put you on the right path to an answer.  Good luck...

Link:[http://forums.whirlpool.net.au/forum-replies.cfm?t=332529](http://forums.whirlpool.net.au/forum-replies.cfm?t=332529)

---

### Post by SodomizedPeanut on 2005-05-15
As a follow up to my own question, and to provide an answer for anybody who might have had the same problems, I found this little snippet whilst looking at a page about my router:

> 
Azureus, the latest version 2.3.0.0 has a new Distributed DB system, this thing can KILL your connection. try turning it off, and make sure your connections are set low. i run Azureus 24/7 and i have 200 global connections with 75 per torrent and 8 Max outbound connection attempts, with Distributed DB turned OFF (plugins.. dist db.. uncheck enable)

for port problem, under Nat Recipes there is one posted for Azureus, it works just make sure you list the port you intend to use (6881) and make sure its pointed to the currect IP Address on your Local Network, you will probably want to setup your puter that is runing Azureus to be static local ip (like mine is ip 192.168.1.5 sub 255.255.255.0 gate 192.168.1.1 dns 192.168.1.1) that way the rule is allways valid, even localy dhcp can switch your ip around mine used to bounce betwen .3 and .4 all the time..



This from the excellent BT Voyager 205 page at corz.org ([http://corz.org/comms/hardware/router/bt.voyager.205_router.how-to.php](http://corz.org/comms/hardware/router/bt.voyager.205_router.how-to.php))

Go there if you're using BT Broadband. It's essential.

---

