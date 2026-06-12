---
title: "network interfaces"
date: 2007-10-04
forum: General Help
---

### Post by Trance Gemini on 2007-10-04
Hi!

As I can see bluetooth related stuff is a dead stone to ALL ubuntu community. I am saying so because almost all that kind of topics remains unanswered.

While I was solving my [own topic]("http://ubuntuforums.org/showthread.php?p=3472661#post3472661") (because of I didn't get answers), I have found the solution on russian.
The solution was to add an interface called bnep0.

And what do you know? :) First I have added this interface using this lines that were added in /etc/network/interfaces

```
iface	bnep0 inet static
address	192.168.0.30
netmask	255.255.255.0
network	192.168.0.0
gateway	192.168.0.1
auto	bnep0
#map	bnep0 
```

After that I saw my interface via ifconfig!!! OK, then I managed to connect to my other PC using sudo pand --connect  mac_address, and I got file sharing running!

How Great!, - I thought. And rebooted.

Now, on my lines in the interface file I fot this response:

```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
bnep0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
bnep0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
bnep0: ERROR while getting interface flags: No such device
Failed to bring up bnep0.
```

And, of course, nothing works.

Whaddahell?

---

