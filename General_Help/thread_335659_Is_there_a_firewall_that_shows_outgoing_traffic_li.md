---
title: "Is there a firewall that shows outgoing traffic like ZoneAlarm"
date: 2007-01-10
forum: General Help
---

### Post by tc101 on 2007-01-10
I have a firewall router and have installed firestarter, so I am not worried about someone coming into my system from the outside.

However, anyone could put extra code in a game or utility that I might download and run.  That code could search my system for sensitive data, like a social security number in a tax file, and send it out from my system.  

In windows ZoneAlarm, it gives you a message any time any program is trying to access the internet.  Is there anything like this for linux?

---

### Post by az on 2007-01-10
> **tc101 said:**
> 
In windows ZoneAlarm, it gives you a message any time any program is trying to access the internet. 

Actually, it will give you a message when *some* program is trying to access the internet.  Some programs are not part of what it will notice - that's one of the flaws of application-based firewalls.  They are basically useless unless the whole stack (your entire OS) is secure.

Being that the software that makes up ubuntu is open source - and uploaded to the archives in source form, and that not just anybody can upload there, it is highly unlikely that any kind of malware would be there or last very long there.

That being said, if you insist, there are some proprietary apps that do what you say.  Panda is in the Dapper-commercial repository, (I think).  It used to be, anyway.

A firewall (any kind) is useless on a desktop system.

---

### Post by tc101 on 2007-01-10
> A firewall (any kind) is useless on a desktop system.

Could you say more?  There are obviously lots of people who disagree with you on that, but I would like to hear more about your point of view.

---

### Post by schilcha on 2007-01-10
If you're really paranoid, have a look at selinux. There you can define which processes what ressources (including the network). I don't have any practical experience with it, but be warned that selinux is anything but trivial.

---

### Post by Oki on 2007-01-10
I am no "really paranoid", but I agree - it would be ok to watch the traffic - even the outgoing.

---

### Post by az on 2007-01-10
> **tc101 said:**
> Could you say more?  There are obviously lots of people who disagree with you on that, but I would like to hear more about your point of view.

What more is there to say?  An application-based firewall is just as insecure as the OS on which it runs.  A packet filter firewall is useless on a linux desktop because you know (and control) what is listening to the network. If you install something that is going to talk to the network (bittorrent, webcam, etc...) you are just going to allow trafic through thorse ports anyway.

If you have nothing listening to the ports, you don't need to block them.  There is no danger.

And there is no way to be "invisible" while you are on the net.  The moment you browse a web page, someone knows your there, regardless of whether all your ports are "stealthed".

---

### Post by Pocket Aces on 2008-01-12
I would like a firewall similar to ZoneAlarm for my Ubuntu machine (now my primary station) as well.

I have one very simple reason for this, which I feel az has overlooked.  Many applications "phone home" which I do not like.  I'm not talking about nefarious malware but simply applications which check for updates, download new content, send usage information or communicate with the companies servers in some way.

An example is the Rhythmbox music player which ships with Ubuntu by default.  When you play an MP3 is goes to the internet to find the album cover.  In this particular application that service can be disabled, but by default you are creating a record of every MP3 you play on some remote server.

I would much rather have a blacklist by default so when I tried to play an MP3 my firewall told me "Rhythmbox is attempting to access the internet" so I could stop it, rather than letting every app access the net and only after using it for a while realizing data about what MP3s I was listening to is being sent over the internet.

Port-based blocking won't work for this as a program could easily just use a standard port like 80.

---

### Post by ubutufan on 2008-01-12
Firestarter is the name
Install from synaptics. you can monitor everything whether others consider this paranoia or not

---

### Post by chrisccoulson on 2008-01-12
> **tc101 said:**
> I have a firewall router and have installed firestarter, so I am not worried about someone coming into my system from the outside.

However, anyone could put extra code in a game or utility that I might download and run.  That code could search my system for sensitive data, like a social security number in a tax file, and send it out from my system.  

In windows ZoneAlarm, it gives you a message any time any program is trying to access the internet.  Is there anything like this for linux?

If you want to make sure that applications can't access sensitive data (orany data that the application doesn't need in order to function), then sandbox them with Apparmor. That's exactly what I have done for all closed-source games / applications that I run. It is better than being notified that an application is connecting to the internet, especially if that application normally connects to the internet (eg, an online game) anyway. Being notified that an application is connecting to the internet doesn't give you any useful information about what the application is doing, but Apparmor does. You already have Apparmor if you're running Gutsy, you just need to profile your applications.

Download the Apparmor quick start guide and have a read: [http://www.novell.com/documentation/opensuse103/pdfdoc/book_opensuse_aaquick/book_opensuse_aaquick.pdf]("http://www.novell.com/documentation/opensuse103/pdfdoc/book_opensuse_aaquick/book_opensuse_aaquick.pdf")
Also check out /usr/share/doc/apparmor-docs/

Have you got any applications in mind that you'd like to protect?

---

### Post by nixclusive on 2008-01-12
AFAIK presently there's no easy solution to application level firewall in linux. thankyou very much.

---

### Post by daninkorea_ on 2008-04-17
> **az said:**
> Actually, it will give you a message when *some* program is trying to access the internet.  Some programs are not part of what it will notice - that's one of the flaws of application-based firewalls.  They are basically useless unless the whole stack (your entire OS) is secure.

Being that the software that makes up ubuntu is open source - and uploaded to the archives in source form, and that not just anybody can upload there, it is highly unlikely that any kind of malware would be there or last very long there.

That being said, if you insist, there are some proprietary apps that do what you say.  Panda is in the Dapper-commercial repository, (I think).  It used to be, anyway.

A firewall (any kind) is useless on a desktop system.

What about stopping a windows program that you're running in Wine from accessing the net? Or not wanting programs to access the net while you're using them? Don't those two needs qualify?

---

