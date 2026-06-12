---
title: "Using Ubuntu to replace windiz everywhere"
date: 2007-01-17
forum: General Help
---

### Post by hairshirt on 2007-01-17
I’ve got a good chance to getting (what is for me) a very large job for a smallish/medium sized company.

They are running a Windiz network (windiz SBS 2oo3) and have incorporated within that network about 10 xp work stations and about 10 Apple Macs.  Their web server is Windiz Web Server.

They’ve reached a point where their IT infrastructure, after laying neglected for a number of years, just doesn’t work as it perhaps once did.  Their M$ Exchange Server keeps breaking they keep loosing connectivity within the network and with their internet connection.  I could go on and on and on.

I’ve basically been given a blank sheet of paper and told to redesign and reinstall and reconfigure the lot.  Now I am (perhaps understandably) a great fan of Linux and in particular Ubuntu Linux.  I want Ubuntu to play a major role in is project.

I would like to change the web server to Ubuntu but first I have to tackle the fact that it runs a smallish M$SQL database and that the web site asp.  Does anyone have experience of converting this to MySQL?

M$ Exchange Server must be replaced.  Their must be an Ubuntu Linux Gateway put in place, and ideally I would like the network, if at all possible, to be Ubuntu Linux and for the Windiz and Macs to work within that network. 

Anyone have any idea, peals of wisdom or general advice?  Of course you are also very welcome to tell me what an idiot I must be to even think of undertaken such a task.

Many thanks in advance.

---

### Post by justifier on 2007-01-17
are you thinking of changing the workstations as in for the office staff's machines to ubuntu too?

---

### Post by oli888 on 2007-01-17
I'm fairly new to Linux and don't know much - in fact nothing about servers ;) !

However, I did a Google search for you and perhaps this could be useful:

[http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html](http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html)

The section entitled Migration Tools and the sections below that seem to be relevant. If not, I'm afraid I can't help. 

Good luck! :-D

Oli

---

### Post by hairshirt on 2007-01-17
Thanks justifier 

That's a very good point that I should have made clear in my post.

No... I think that would be too much of a culture shock together with all the other changes that I will propose.  Should still be possible thought... Shouldn't it?

Many thanks for your input.

PS And thanks to oli888... checking that link now.  I've read a little about migration from M$SQL to MySQL but, perhaps like most, have never actually attempted it.  Thanks again oli888... That link was very useful.  I'll refer back to that link when the time comes.

---

### Post by hairshirt on 2007-01-17
Do you know what... I love this community.  It's aways been friendly and helpful. Thanks again guys.

---

### Post by hairshirt on 2007-01-18
Goodness me…  I really did think that this would provoke a little more interest and feedback.

---

### Post by alanandhispc on 2007-01-18
One main question i would ask is how extensive are you use active directory? unfortunatly, when it comes to it, if your using group policy, there no better alternative without costing you a pretty penny. otherwise read on.

Are there any central applications being run on the server, other than exchange?

If not, the server could certainly be replaced with a ubuntu one, with samba taking place of active directory. if this is your only server, then im guessing the userbase is lower than 50. that way you won't have to look into ldap backends for samba just yet.

For replacing exchange, theres quite a few solutions, but two that incorporate groupware is
[http://www.citadel.org/doku.php/installation:debian](http://www.citadel.org/doku.php/installation:debian) or [http://www.egroupware.org/](http://www.egroupware.org/) if your heavily usiing public folders, that will be one thing you will have to investigate, as this sort of thing isn't as widespread in other email solutions.

you could still run asp pages, by installing mono and apache, some tinkering maybe required as your milage may vary.


i'd recommend an swap out migration, putting in a new server that has ubuntu on it. that way, you can configure samba and your email solution of choice and join the workstations to the samba domain.
to migrate email, one idea would be to configure all the mailboxes on the new solution, and connect via imap in outlook/thunderbird and then connect to the exchange server too, then move the emails on the client side. if the number of mailboxes are low.

ideally this would be a weekend job and a plan for this should ideally take a month or so to ensure you have all the basis covered.


this is very brief and i might be wrong in some places, but that should get you started.


Alan

---

### Post by alanandhispc on 2007-01-18
in addition, it might be worth while if you could do a network diagram for us, as that will help loads on suggesting what to do.

---

### Post by hairshirt on 2007-01-18
Thanks alanandhispc 

More of just the sort of input I was looking for.  Re the diagram.  Of course the existing structure is in place but I've been given a blank sheet of paper and I want Ubuntu to play a major part is this reconfigeration.

I was considering fitting new HD's to the servers and configering them that way with Unbuntu on a dual boot basis before making the switch completely.

---

### Post by oli888 on 2007-01-18
Glad I could help even though I have no idea myself! ;)

---

### Post by alanandhispc on 2007-01-18
Hi,

Even so, it would be good how everything connected at the moment, so the migration to the new system is as smooth as possible.

Alan

---

### Post by alanandhispc on 2007-01-19
hi,

also, how are the user accounts' profiles and my documents stored?

Alan

---

