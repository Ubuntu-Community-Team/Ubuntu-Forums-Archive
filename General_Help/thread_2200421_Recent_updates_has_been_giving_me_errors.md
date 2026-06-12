---
title: "Recent updates has been giving me errors"
date: 2014-01-19
forum: General Help
---

### Post by jcsa1986 on 2014-01-19
Hi there,


This is my first post and I'm not sure if this is the right category to post this. Sorry if is not.


This is more likely a question than asking for help.


A few days ago I updated my system and after restart, it started giving some errors (which I already reported). I thought this was related to something I did recently, you know that we Linux users tend to make several changes to our systems and sometimes (if not most of the time hehe) we break things. But today I turned on my old computer (that I use as a "server") and there were some pending updates, so I updated the system. In the middle of that update I started getting some errors too, so now I'm not sure if this might be a global issue with Ubuntu.


This are the details of one of the problems on my main system:

[COLOR=#333333][FONT=Ubuntu Mono]ProblemType: Package[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]DistroRelease: Ubuntu 13.10[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Package: syslinux-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]themes-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]debian 12-2[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ProcVersionSign[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]ature: Ubuntu 3.11.0-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]15.23-generic 3.11.10[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Uname: Linux 3.11.0-15-generic x86_64[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ApportVersion: 2.12.5-0ubuntu2.2[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Architecture: amd64

[/FONT][/COLOR]The other computer is a 32 bits architecture.


Has anyone incurred any issues like this lately? Because if not, I would have to do some digging into what could be wrong with them.


Thanks! :)
[COLOR=#333333][FONT=Ubuntu Mono][/FONT][/COLOR]

---

### Post by Bashing-om on 2014-01-19
jcsa1986; Hi ! welcome to the forum .

Any problem/error is worth investigating as small things over time can escalate.
1st step in checking is to update and upgrade the installed packages:
```

sudo apt-get update
sudo apt-get upgrade

```
and see what the package manager thinks, and the hints that the package manager provides for solutions.

3rd party software is often times out of the package manager's jurisdiction and is on you to manage that software.

[INDENT][INDENT]we strive to be
[INDENT][INDENT][INDENT]the master of our machines
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jcsa1986 on 2014-01-20
Hi Bashing-om, thank you for your replay.


I'm sorry, I thought that I will be notified via email on any replays to my post, but I wasn't (probably a check I didn't notice somewhere).


I was just curious to see if anyone else was having the same behavior, mostly because my 2 computers failed on a system update, but aparently it was not (since anyone else has commented something about it). I did the bug report and by doing some research I noticed that many other users had the same problems.


Last night I recieved a partial system upgrade which reinstalled (I believe) the faulty packages and since then I'm not getting the error at startup anymore.


I appreciate you took the time to read my post, I would love to become an active user of this comunity and hopefully help others with the knowledge I've acquired through all this years.


Best regards.

---

### Post by Bashing-om on 2014-01-20
jcsa1986; Hey,

Great things straightened out, partial upgrades always have the probability of being problematic !

As to contribution to the community through this forum, you have already begun. Believe me, all it takes is to respond to someone's request for assistance. Not one of us knows everything but everyone knows somethings. Just read and respond to what you can. 
Every little bit helps.

[INDENT][INDENT]bread cast upon the waters
[/INDENT][/INDENT]

---

### Post by jcsa1986 on 2014-01-20
Yes sir! By experience I can assure you that partial upgrades can break the whole system hehe but luckily this was not the case, it was for that package specifically so by the moment it seems that everything is working fine.


Thanks again!

---

