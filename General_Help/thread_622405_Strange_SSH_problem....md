---
title: "Strange SSH problem..."
date: 2007-11-24
forum: General Help
---

### Post by bigbob6383 on 2007-11-24
well I'm trying to simply SSH into my website "site.org" but can't ever get it to work.
I can use PuTTY or WinSCP on my Windows partition and it works fine, but on either of my Linux partitions I give it the command and nothing happens.

I'm sure none of my commands are wrong or anything so I have no idea what's going on...
I mean this is what I put in the terminal:
```
~$ ssh user@site.org
```

I was looking around for some solutions, but mine seems a little more out of the ordinary than the issues I've seen.

I hope you guys can help - thanks

(btw, i also posted this in the networking section but it had absolutely no activity so i'm trying here instead)

___________________________________________________________________________________________________________________
**SUM UP OF EVERYTHING**

Okay, so here's the sum up of everything:
- No computers on my network can connect to the SSH/FTP site
- All computers on my network can connect to any other SSH or FTP site
- My friend has gotten his SSH to the site to work without any issues at all

---

### Post by jken146 on 2007-11-24
Do you have ssh-server installed on the box you are trying to connect to?

---

### Post by bigbob6383 on 2007-11-24
> Do you have ssh-server installed on the box you are trying to connect to?
yes, I've successfully connected to the server many, many times via PuTTY or WinSCP in Windows...

---

### Post by bigbob6383 on 2007-11-24
c'mon guys - any ideas at all? :???:

---

### Post by scxtt on 2007-11-24
is there a firewall on the sshd host (**sudo iptables -L**)?  does your windows partition use the same LAN IP you linux partition(s) use?

---

### Post by bigbob6383 on 2007-11-24
> **scxtt said:**
> is there a firewall on the sshd host (**sudo iptables -L**)?  does your windows partition use the same LAN IP you linux partition(s) use?

I don't believe there's any firewall although there may be...but connection works perfectly using PuTTY without any edits in Windows --- I even tried building the PuTTY unix version for Linux but although the SSH connection works in Windows it doesn't work in any of my other operating systems (I've tried on two different forms of linux)

And yes, the two os's have the save IP's (well basically since i connect through a router)

---

### Post by geirha on 2007-11-24
Could it be a nameserver issue? can you try ssh with ip-address instead of hostname?

---

### Post by scxtt on 2007-11-24
post the output of: **sudo iptables -L** just to be sure ...

i'm thinking there's some config issue where the server is expecting a certain type of request and not getting it from your linux ssh clients ... i've not had that problem myself ...

are you sure networking is working in linux? (had to ask ;))

---

### Post by bigbob6383 on 2007-11-24
> Could it be a nameserver issue? can you try ssh with ip-address instead of hostname?

no, i tried the IP of the site as well and it still didn't work

My networking is fine - i can FTP perfectly from it and SSH to any server it seems (although I only tried it into my own computer) - to all except the one i actually want to connect to!!!! ](*,) So i guess it must be something with the server :-k
And here's the output from "sudo iptables -L" **on *my* computer** (i'm not sure if this is what you wanted, but i can't do this on the server computer since i don't have access to it)

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
[B]
[POSSIBLY IMPORTANT][/B] y'know, i forgot to mention that the first time i tried to SSH into the site via Linux (with the SSH wizard or whatever in a LiveCD of BackTrack2) it actually worked, but then every time after that that i tried, it would just completely stall like it still does even though i've tried it the *exact* same way...
did it mysteriously learn to reject communication from Linux or what?!?!? i'm so confused:confused:

---

### Post by bigbob6383 on 2007-11-25
hey! i think i figured out the problem!

the terminal resolves the IP of the "site.org" to a different site ("site.net") which does *not* have an SSH, thus causing it to not be able to ever connect!

But does anyone have any ideas on how i could resolve this issue? :-(

---

### Post by scxtt on 2007-11-25
you could add it to your /etc/hosts (depending on how your nsswitch.conf is setup) ...
```
<site ip>          site.org
```
but if you use the IP, it should work - which you said it didn't ... also, if site.org works in windows, it should work in linux - unless your "nameserver" is drastically different ...

can you post an **nslookup site.org** (and maybe site.net) from both OSes?

---

### Post by bigbob6383 on 2007-11-25
actually sorry - i just tried it in windows (i havent been on it in a while :)) and it turns out it doesn't work there either...

and the worst part is, is that i just told my friend to try on his computer (since he also has an account on the SSH) and it worked for him!

so i thought maybe i'd have to change some of my router settings, but they all look fine! I don't know what to do :cry:

**UPDATE:** I also tried to connect from another computer from my network behind the router and it didn't work so it's definitely got something to do with the router...

---

### Post by bigbob6383 on 2007-12-04
Alright I really have no idea what happened, but after like 2 weeks or something it finally works again.
I forgot to talk to the server guys, but it just started working again... so, y'know i'm not complaining.

oh well, whatever :roll:

---

