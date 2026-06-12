---
title: "is iptables/Netfilter really that safe?"
date: 2008-04-03
forum: General Help
---

### Post by bone2006 on 2008-04-03
I know people always say that Linux is more secure than windows and the majority of the software I load comes from the repository, but every time I use windows my firewall warns me for the first time something is accessing the internet and if I should allow it.

Maybe it's paranoia, but there's something about having a pop up warn you that something is trying to access the internet compared to setting rules, in which I feel maybe isn't as secure.

I mean if I'm not mistaken if I open certain ports with iptables, then another application can even access those ports on my system.

---

### Post by zvacet on 2008-04-03
Read [this.](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bone2006 on 2008-04-03
thanks so much
I haven't read it all, but it looks great so far.  I appreciate the link

---

### Post by Crafty Kisses on 2008-04-03
> **bone2006 said:**
> I know people always say that Linux is more secure than windows and the majority of the software I load comes from the repository, but every time I use windows my firewall warns me for the first time something is accessing the internet and if I should allow it.

Maybe it's paranoia, but there's something about having a pop up warn you that something is trying to access the internet compared to setting rules, in which I feel maybe isn't as secure.

I mean if I'm not mistaken if I open certain ports with iptables, then another application can even access those ports on my system.

I've never had any trouble with them, so I'd say those programs are pretty safe. :)

---

### Post by sekinto on 2008-04-03
If you feel like something is connecting to your computer that you don't want to you could actively monitor your active connections with something like Firestarter.

---

### Post by bone2006 on 2008-04-04
see the article or post still didn't really answer my question.  I don't have a feeling something is on my system, but how would I know?  I mean if I have to look at something and monitor it, then how lazy I am it would be maybe once every 6 months.

Maybe it is a windows mentality, but it does make me feel more secure that I have to even grant firefox permission to access the internet.

I guess it's that people also feel that Linux doesn't have spyware, because the majority of software is open source.  But if Linux picks up and more applications move over to Linux, then we'd have spyware, you could select not to use these products, but how would you know if maybe one of these using the internet?

I think monitoring is not a great idea either, because it could be a certain time frame it access the internet, maybe a certain action from the user it accesses the internet.

I'd just prefer to have something pop up telilng me....................hey...........this program is trying to access the internet.  Select Yes or No

---

### Post by mcduck on 2008-04-04
As long as you only install programs from Ubuntu's repositories you can be absolutely sure that you won't get any spyware or viruses, and therefore it's not necessary to have any application-based filtering on firewall, or to restrict outbound connections.

Actually as long as you don't install any server programs you don't even need a firewall, as there are no programs running that would respond to incoming connections from the network. Having all ports open is safe if nothing is listening to those ports. :)

---

### Post by bone2006 on 2008-04-05
See it's one of those things that I kind of feel if your running a server you feel different, if your running a desktop most users like graphical interaction.  

I've downloaded programs that were not in the repository before, to list just two really quick that come off the top of my head, peazip and ipblock.  

I've also added listing to the repository source such as medibuntu, because I want DVD play back.  Maybe something else come out that I feel I really want and I can't seem to find it.  For instance a friend that just tried linux told me he had to have winamp on his machine.  I told him about xmms, but he wasn't happy well I actually found winamp for Linux.   

If one of the strong points about Linux is FREEDOM, then I want the freedom to download an application from the internet.  

It is possible that it's an argument that can't be won.  I love Linux, but sometimes I can see why Linux makes more sense in the server world, I can see why it's winning or has won on the server side.  But in the desktop world I do find somethings missing in Linux.  I use Linux almost 99.9% of the time at home, but I feel certain things are missing and this just happens to be one of them.

I would prefer to have a fresh install of Ubuntu, as it starts up, I enabled a feature and I click on firefox I'm warned that this application is trying to access the internet.  I can understand why running a server you wouldn't want this.  I'm running ubuntu server on one machine without any desktop environment, but on my ubuntu install it's something I would like having.

I guess you could say I might be alone since it seems nobody has developed something of this nature?

---

### Post by Koori23 on 2008-04-05
You hear it over and over again. "You don't need a firewall in Ubuntu". I will respond by saying this.. That is true, but if you're coming over from the Windows world, you are force fed that logic, it takes ALOT of time to undo and reverse that thinking.

If one were to physically open a port, then yes, another machine could use that as a stepping stone for a DOS attack or something.

I think you need to look at the history of Linux/Unix to understand why security is better overall. Not perfect, but better. We can trace our lineage from System V way back in the 1970's. Our present product is almost a history lesson in trial and error. Any remote attack that could be tried, has been tried at some point. Since we always have something new that's trying to get us, those items have to be upgraded and updated to cope. 

It's good to skeptical about the current configuration for this reason.

Whoever mentioned that "My Windows machine warns me everytime something is connecting to the Internet". Well, in my experience, Windows warns you about EVERYTHING. Information overload to the point of clicking "OK" to every message that pops up. Even with all these security centered questions, has anyone ever wondered why Windows (Even Vista) has issues still? It's probably because every trojan, rootkit or virus is programmed to turn those security services off.

---

### Post by LaRoza on 2008-04-05
By default, there are is nothing listening, so it doesn't matter. If you are using a router and this is a home computer (not a server), then you are fine.

---

### Post by brian_p on 2008-04-05
> **bone2006 said:**
> I know people always say that Linux is more secure than windows and the majority of the software I load comes from the repository, but every time I use windows my firewall warns me for the first time something is accessing the internet and if I should allow it.

Your computer is intended to access the internet. If there is a program you don't want to allow that access to remove it from the machine..

> Maybe it's paranoia, but there's something about having a pop up warn you that something is trying to access the internet compared to setting rules, in which I feel maybe isn't as secure.

It's not paranoia. Silliness, perhaps.

The solution is in your hands. This is Linux after all. All you want is a warning pop-up and you will be happy? Correct? Write a script which pops up a message of your choice and then runs a renamed firefox when you exit it. Name the script firefox and put it in /usr/bin after renaming /usr/bin/firefox to something else. 

> I mean if I'm not mistaken if I open certain ports with iptables, then another application can even access those ports on my system.

You're mistaken.

---

### Post by bone2006 on 2008-04-06
I think it's the samething that some people get offended if you call the operating system Linux, since it's just the kernel and when I was referring to windows, I wasn't referring to any program on windows itself, but more programs like norton's firewall, zonealarm, comondo....etc they all generally have something in common.

I don't want a script to watch firefox and I do believe a lot of people open up ports, espeiclaly if your using torrents or a lot of applications from the repository you'll most likely open up ports 6881 to 6889........maybe 22 if you have an ssh server.  I feel a lot of people open up ports, but hey I guess again I'm alone.

Or could it be that people want to defend linux to the death when it doesn't have something?  

I believe there might just be other reasons.  It seems windows firewalls watch applications that are trying to access the internet and also close ports, while every seems to only care about open ports.  Maybe I need to start identifying windows applications instead of saying just windows, because it seems people think I"m referring to default applications, but something like zonealarm.

Just a simple question?  You enjoy torrents, so you get deluge, you open ports 6881 through 6889 for instance and your enjoying your application.  Linux becomes popular and it seems 50% share in the market at this time.  Well there's now more closes source applications out there, more priority software with trail versions and games out there as well.  You can grab a CD from the store and play a game..............

It just so happens the game you played that's legit installs the needed software on your system, it waits after you've played the game 10 times, then sends maybe personal data to it's head quarters.  Just collecting information about what player you selected.........................doesn't matter.  The point is I think people are full of it to say they are going to just watch and open up logs every day.

I think people seem to treat a server and a desktop the exact sameway.  The scenario above wouldn't happen on a server, but on a desktop environment many many many people wish they could play games on their Linux desktop system.   Many people hope that the popularity improves in Linux, so that more users, more developers, more hardware support.

I do understand theirs pros and cons to everything.  The firewall systems for windows desktop systems seem to be resource hogs, they take your system down to a crawl.

---

