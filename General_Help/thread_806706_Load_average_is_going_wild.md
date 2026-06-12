---
title: "Load average is going wild"
date: 2008-05-25
forum: General Help
---

### Post by faifas on 2008-05-25
Hello fellows,

I'm having a weird issue and wanted to find out if any of you know how to deal with it.
I've got myself Ubuntu box and online RPG game hosted on it.
The problem is that apache and mysqld is going wild (I mean it).

load average: 1.22, 1.20, 1.07

That's an usual load when I only have 40 players online.
Tried stopping apache, server load went to 0.02 (ircd was using it)

Server speed: 2.0Ghz
RAM: 500mb

My server is good enough for such project and I can bet that I have a bug somewhere in my PHP code, that causes a never ending loop and apache with mysqld are going wild.

Mysql is using ~20% of CPU and few apache childs are using ~11% each, so that's really not normal.

What do I want you to help me with is a tool for showing php files CPU usage or something similar, so that I could find out which of my files are causing that server load.

Thanks in advance,
Faifas

---

### Post by faifas on 2008-05-29
Since no one is replying me, I've decided to tell others who'll have same problem how to solve it.

That might cause a lot of visitors requesting your pages frequently.

What did I do:

Turned keepalive to off

StartServers         15
MinSpareServers      15
MaxSpareServers     65
MaxClients          256

and lowered allowed memory in php.ini

Hope this helps!
Faifas

---

