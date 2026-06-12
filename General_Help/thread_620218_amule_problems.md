---
title: "amule problems"
date: 2007-11-22
forum: General Help
---

### Post by linux noooob on 2007-11-22
HEY! back and i am giving it another try i have opened both tcp and udp ports in my firwall and router:

4662
4242
5000
4672
4665
and yes i also added way more on my firewall!!!!
The top arrow is still red with the bottom one yellow and kad is off like what is :confused:

HELP!

---

### Post by Hallvor on 2007-11-23
You have opened more ports than you have to. :) 

-Check your WAN IP. If it ends with a zero, you will get a low ID.
-Check your router once more to see if you have opened and forwarded the ports correctly.
-Try to use something else than the default ports.

---

### Post by linux noooob on 2007-11-24
my ip ends in 7 and i have to ask when it asks for my private ip what do i put?

---

### Post by Hallvor on 2007-11-25
I am not sure if I follow you...

Here are solutions to most common lowid problems:
[http://forum.emule-project.net/index.php?showtopic=48127](http://forum.emule-project.net/index.php?showtopic=48127)

---

### Post by linux noooob on 2007-11-25
sorry what i mean is that when i am forwarding a port it asks for a name a protocol (TCP UDP or both) and then it asks for the private ip and the public port

(note i use a DI-524 dlink router)

---

### Post by disturbedite on 2007-11-25
i have the same problem, lowid.  but its cuz i only have a cable modem & no router... guess i'll have to get one...

---

### Post by Hallvor on 2007-11-25
> **linux noooob said:**
> sorry what i mean is that when i am forwarding a port it asks for a name a protocol (TCP UDP or both) and then it asks for the private ip and the public port

(note i use a DI-524 dlink router)


Check this one for help:
[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

---

### Post by Hallvor on 2007-11-25
> **disturbedite said:**
> i have the same problem, lowid.  but its cuz i only have a cable modem & no router... guess i'll have to get one...

You don`t need a router to get a high ID. All you need is open ports.

---

### Post by linux noooob on 2007-11-25
thats is the website i used but see the thing is i know there is alot of "ranking" in amule so i was wondering if i uploaded alot of files would that increase my "rank"??

---

### Post by Hallvor on 2007-11-26
> **linux noooob said:**
> thats is the website i used but see the thing is i know there is alot of "ranking" in amule so i was wondering if i uploaded alot of files would that increase my "rank"??

If you upload more than a megabyte to someone, you will advance in his/her queue.

[http://www.amule.org/wiki/index.php/FAQ_eD2k-Kademlia#What_is_all_that_credits.2C_rate_and_score_stuff_about.3F](http://www.amule.org/wiki/index.php/FAQ_eD2k-Kademlia#What_is_all_that_credits.2C_rate_and_score_stuff_about.3F)

---

### Post by disturbedite on 2007-11-26
> **Hallvor said:**
> You don`t need a router to get a high ID. All you need is open ports.
oh, if thats the case, then i guess i misunderstood.  well, i forwarded ports more ways than you can imagine but i have never, ever managed to get a highid with amule.

could it be that my isp uses certain things like NAT or re-routing that makes me not able to attain a high id?

---

### Post by Hallvor on 2007-11-27
> **disturbedite said:**
> oh, if thats the case, then i guess i misunderstood.  well, i forwarded ports more ways than you can imagine but i have never, ever managed to get a highid with amule.

could it be that my isp uses certain things like NAT or re-routing that makes me not able to attain a high id?

Yes, it could be. But try changing the default ports before you give up to non-standard p2p ports below 10000.
Some have also reported success with ports such as 1755 and 445.

---

### Post by jointstereotype on 2007-11-27
If it's any help, I use the same router and have never had a problem getting a highID. I had to forward 2 ports and I was ready to go.

---

### Post by disturbedite on 2007-11-27
> **Hallvor said:**
> Yes, it could be. But try changing the default ports before you give up to non-standard p2p ports below 10000.
Some have also reported success with ports such as 1755 and 445.
well i did try other ports, but not 1755 and 445, thanks, i will try that.

UPDATE:
thanks for the tip, but i finally figured out how to access my modem's interface.  (didn't think it was possible before).  i tried forwarding those ports but it didn't work....

EDIT:
ok i have a question.  forgive me if this sounds stupid, but as i said, i forwarded the ports from modem's interface.  do i have to forward those same ports with iptables as well?  cuz i tried it with just the modem's interface but that didn't work...

---

