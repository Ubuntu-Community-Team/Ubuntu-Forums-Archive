---
title: "Is windows networking superior compared to linux`s?"
date: 2007-03-24
forum: General Help
---

### Post by DjDarkman on 2007-03-24
How many times should I ask this ,I taught linux had superior networking ,but the help here is proving the opposite ,so here on my conclusions :

[COLOR="Red"]You can`t share pppoe internet internet connection in linux ,or if it is possible no one will help you.[/COLOR]

You might want to ask why I`m jumping to this conclusion ,here`s the answer :

I have a **PC** and a **laptop** and I want to **share my PC`s internet connection** with my laptop.

[COLOR="Red"]- no one ever answered my question : "How to share a pppoe internet connection?"[/COLOR]

- the closest answere was to buy a router ,why buy a router for just two computers?
  I DON`T WANT TO BUY A ROUTER

This could mean two things :

- linux`s networking lacks the technology needed for sharing a pppoe internet connection

or

- the ubuntu help is starting to cripple and people can`t even answere simple questions like this


Here are the facts again :

- In windows you can share a pppoe connection with 3 clicks
- In linux it`s impossible for me because I`m not an unix administrator


And before you say "RDFM" and "You are a noob" or "you are too noob for linux" ,I can tell you that I`m not a "noob" but I`m not an iptables expert eighter ,and THIS is a common problem ,and no one seams to care about.

---

### Post by Rhubarb on 2007-03-24
You can easily share an internet connection using Firestarter.

Firestarter is a nice GUI front end for iptables, it's in the repositories.
[http://www.fs-security.com/](http://www.fs-security.com/)

Edit: As Firestarter is just a front end for iptables (which always runs in the background), you don't need to start up Firestarter to share your internet - iptables will be doing this all the time in the background - even upon booting your computer.

---

### Post by DjDarkman on 2007-03-24
> **Rhubarb said:**
> You can easily share an internet connection using Firestarter.

Firestarter is a nice GUI front end for iptables, it's in the repositories.
[http://www.fs-security.com/](http://www.fs-security.com/)

Edit: As Firestarter is just a front end for iptables (which always runs in the background), you don't need to start up Firestarter to share your internet - iptables will be doing this all the time in the background - even upon booting your computer.

Firestarter doesn`t detect ppp0 ,I tried that earlier.

---

### Post by yopnono on 2007-03-24
I don't use pppoe and sharing (I use ethernet and a router)
But have you done a search on the internet like google?
[http://www.google.se/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=bM8&q=How+to+share+a+pppoe+internet+connection+ubuntu&btnG=Search](http://www.google.se/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=bM8&q=How+to+share+a+pppoe+internet+connection+ubuntu&btnG=Search)

---

### Post by collapse-the-control on 2007-03-24
To DJDarkman,

Unfortunately I don't know the answer to your problem, but I just wanted to say that your post is really rather rude. I don't see why any member here would even want to reply to it, when all you've done is insult the community. You should consider apologizing and then maybe others would be more willing to help out.

---

### Post by DjDarkman on 2007-03-24
> **collapse-the-control said:**
> To DJDarkman,

Unfortunately I don't know the answer to your problem, but I just wanted to say that your post is really rather rude. I don't see why any member here would even want to reply to it, when all you've done is insult the community. You should consider apologizing and then maybe others would be more willing to help out.

Facts ,see the facts ,I posted the same thing at least 3 times.
I`ve asked on irc also ,I searched on google to no avail.

And you say I have no reason to be "rude".

BTW ,see how many feisty bugs I`ve submitted to launchpad before even considering saying any more nonsense.

I`m annoyed because no one ever gave a good working answere to this question.

Here are more facts :
- RDS is the most popular ISP in Romania ,and now it`s switching to pppoe instad of lan connection ,already a lot of users switched to this new pppoe connection.

- not all people have a real reason or money to buy a router ,for example if you have a laptop and a PC would you buy a router just for two computers...?I think not

- people who a are trying to use (k)ubuntu as their primarry OS ask me how to share their internet connection with their collagues

I could not imagine how could an essential thing like this be ingored.There are a lot of places where there`s one computer that`s up 24/7 and it gives internet for the rest.

So before you judge my way of saying things ,look at the facts and look at how many times I tried to say it "nicely".I`m realy trying to help people but it`s impossible if no one helps me.

---

### Post by jeffathehutt on 2007-03-24
I'll be honest, I haven't done this in years, so the process might have changed a bit.

I have to make some assumptions, please correct me if these are wrong...
- You have a desktop computer with two nics.  One nic goes to the modem.  The other is connected by a crossover cable to the laptop.
- The nic going to the modem is configured with pppoe.
- The desktop can access the internet without any problems.

If that is true, here is what I think you need to do.

First, set the nic on the desktop going to the laptop to be static, and assign it a private IP address, such as 192.168.1.10 with a netmask of 255.255.255.0

Next, set the IP address on the laptop to be 192.168.1.11.  Set the default gateway to be 192.168.1.10.

Make sure you can ping the desktop from the laptop
```
ping 192.168.1.10
```

If that works, type this command on the desktop:
```
echo "1" > /proc/sys/net/ipv4/ip_forward
```

Now, about 4 years ago, that is all it took to share the connection.  I'm not positive those steps are still accurate, but the steps should be similar to that.

---

### Post by DjDarkman on 2007-03-25
> **jeffathehutt said:**
> I'll be honest, I haven't done this in years, so the process might have changed a bit.

I have to make some assumptions, please correct me if these are wrong...
- You have a desktop computer with two nics.  One nic goes to the modem.  The other is connected by a crossover cable to the laptop.
- The nic going to the modem is configured with pppoe.
- The desktop can access the internet without any problems.

If that is true, here is what I think you need to do.

First, set the nic on the desktop going to the laptop to be static, and assign it a private IP address, such as 192.168.1.10 with a netmask of 255.255.255.0

Next, set the IP address on the laptop to be 192.168.1.11.  Set the default gateway to be 192.168.1.10.

Make sure you can ping the desktop from the laptop
```
ping 192.168.1.10
```

If that works, type this command on the desktop:
```
echo "1" > /proc/sys/net/ipv4/ip_forward
```

Now, about 4 years ago, that is all it took to share the connection.  I'm not positive those steps are still accurate, but the steps should be similar to that.

I grately apreciate your help ,but these settings are not enough ,somehow I gotta tell iptables to do the masquarading.

Ok ,I`ve finally found a working solution ,here it is ti those who had/have the same problem I did :

apt-get install dnsmasq ipmasq

and here`s a script to share the connection that must be started each time you want to share :
you must replace ppp0 with the interface you get the internet from and replace eth0 with the interface you share your internet.

> 
#!/bin/bash
IPTABLES=/sbin/iptables
EXTIF="ppp0"
INTIF="eth0"

echo "1" > /proc/sys/net/ipv4/ip_forward


$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT

$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP

$IPTABLES -F FORWARD
$IPTABLES -t nat -F

$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT


---

### Post by jeffathehutt on 2007-03-25
Thanks for posting that solution.  Now that I think about it, when I used to share my connection, iptables wasn't even around...  Back then it was still ipchains, which isn't nearly as powerful as iptables.

---

