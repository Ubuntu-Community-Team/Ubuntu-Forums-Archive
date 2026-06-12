---
title: "Slow torrent download"
date: 2007-05-31
forum: General Help
---

### Post by Zdravko on 2007-05-31
Hi there! My torrent download speed is very slow. Why? How do I fix his issue?

---

### Post by JSThePatriot on 2007-05-31
One thing you should do is forward the proper ports to your machine to allow for peer connections. That will greatly help your speed. I was having trouble with speed while using Azureus, but after the most recent kernel update, everything has been wonderful. (I think my wireless was acting up, because I noticed I haven't had any troubles since the latest kernel update)

I hope this helps,
JS

---

### Post by Zdravko on 2007-05-31
How do I forward the proper ports?

---

### Post by JSThePatriot on 2007-05-31
It depends on what router you have (I assume you are behind one), and the torrent client you are using as to what ports are needed by the program.

So I need to know the router, and the torrent client (I would like to recommend that you try Azureus ... available through the package manager).

Hopefully I can assist further,
JS

---

### Post by Azakus on 2007-05-31
I use Azureus instead of gnome-btdownload. I would use that instead as it is a very good, powerful client and very secure. Also, don't use the repo's version of Azureus as it keeps crashing with every Java I've tried. Get the actual source and just use that.
[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

---

### Post by JSThePatriot on 2007-05-31
> **Azakus said:**
> I use Azureus instead of gnome-btdownload. I would use that instead as it is a very good, powerful client and very secure. Also, don't use the repo's version of Azureus as it keeps crashing with every Java I've tried. Get the actual source and just use that.
[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

I have yet to have trouble out of the repository, but I will certainly look at their SF page. Do they have an AMD64 .deb package?

Thanks,
JS

---

### Post by Zdravko on 2007-05-31
I am behind a router, yes.
I use gnome-btdownload.

---

### Post by JSThePatriot on 2007-05-31
> **Zdravko said:**
> I am behind a router, yes.
I use gnome-btdownload.

What type of router? Linksys, D-Link, and/or Netgear...

Also I would love to recommend you get Azureus. It is a much better, and faster client.

JS

---

### Post by GabrielDunn on 2007-05-31
Beyond opening your ports, I think its a good idea to maximize your upload speed.  I have noticed a great speed increase in download when I max my upload speed.

---

### Post by JSThePatriot on 2007-05-31
> **GabrielDunn said:**
> Beyond opening your ports, I think its a good idea to maximize your upload speed.  I have noticed a great speed increase in download when I max my upload speed.

That can certainly be true. You do however have to be careful because on several ISP's I have been on the more you up load the slower the download. Because for some reason it's harder for ISP's to give you any upload speed.

JS

---

### Post by Zdravko on 2007-06-01
> **JSThePatriot said:**
> What type of router? Linksys, D-Link, and/or Netgear...

Also I would love to recommend you get Azureus. It is a much better, and faster client.

JS
Its a D-Link. Ok, I will download Azureus.

---

### Post by Zdravko on 2007-06-01
I use now Azureus... The same story. Download speed = 5KB/s.
But Azureus tests the port as OK!!! :(

---

### Post by Zdravko on 2007-06-01
Now Azureus said : "You are behind a router, enable forwarding port...". Then the speed dropped to 0. What to do next? :(

---

### Post by Hallvor on 2007-06-01
1. Have you logged on to your router, opened and forwarded the correct port(s)? 
2. Change the default port(s) in Azureus also.
3. Install firestarter and open the port(s). (sudo apt-get install firestarter)

---

### Post by regomodo on 2007-06-01
Guys, he doesn't know how to forward the correct ports. It's useless just suggesting a different Bittorrent app

Here is a great site on how to use your router correctly.

[http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

Take note of what port number  you chose for your torrent app. Also, know what your ip address is as well. To find that type

$ ifconfig

in terminal.

That should get you started

---

### Post by regomodo on 2007-06-01
> **GabrielDunn said:**
> Beyond opening your ports, I think its a good idea to maximize your upload speed.  I have noticed a great speed increase in download when I max my upload speed.

I found i have to keep a balance. My max upload speed is ~45KB. If i left my torrent wide open the download seems to suffer. I have to leave my upload around 35KB and all is rosy. Due to my street having a load of students my 10Mb download is more like 512Kb. Average download for torrents is about 150Kb/s

---

### Post by Zdravko on 2007-06-03
> **Hallvor said:**
> 1. Have you logged on to your router, opened and forwarded the correct port(s)? 
2. Change the default port(s) in Azureus also.
3. Install firestarter and open the port(s). (sudo apt-get install firestarter)

I logged into my router and opened the port Azureus uses. No effect! What to do next?

---

### Post by enfantterrible on 2007-06-04
i have the same issues
bitlord on windows works just fine (downloads up to 300/400 kB/sec) but no luck in ubuntu.

dont like the default gnome app because i cannot setup anything (dont even know how to launch the gui after i installed it)

azureus keeps telling me nat problems during setup but then would work... for a while, then everything drops to zero.

i have a linksys router and i always port forwarded no problem in xp :(

---

### Post by Hallvor on 2007-06-11
Have you opened the ports in Ubuntu using Firestarter? Opening the ports in the router is only half the job. You also need to open the ports in iptables using Firestarter.

If you can upload and download very fast for a few seconds, before the connection suddenly drops, it is probably your ISP throttling you. Try a client with protocol encryption if you think this is the case. (Azureus has this feature.)

---

### Post by dkaddict on 2007-07-24
I really don't pay too much attention to forwarding ports and what have you. I get really good speeds with Ktorrent and utorrent run through WINE without enabling upnp or forwarding anything. I use a high number for the port KTorrent listens on (92440 or something like that) and just let utorrent pick a random one each time I use it. My uploads on both are set to unlimited and I seed files all the time I have it running. When it is going good, I get an average of 500kbps.

Now for the catch. After a little while trying to figure all of this torrent stuff out, I discovered 'bandwidth throttling'. My ISP, British Telecom, throttles Bit Torrent downloads between 4pm and Midnight every day. They do so, apparently, in order reduce the load on their servers at 'peak times'. My Torrents, which fly in at nearly half a mega byte a second, drop to ***12kbps MAX***. I am trying to figure out how to get around this behaviour that my ISP uses to restrict what was sold to me as 'unlimited 8MiB broadband'. It ain't 8meg and it ain't unlimited. End of.

I suggest doing a Google search for 'Bandwidth Throttling' in whatever country your ISP is based. British Telecom aren't the only ISP in the UK who do this. 

If you want to see how well Bit Torrents work, do the following>

Download a torrent file of your liking. *Make sure* it has plenty of 'seeders'.

Open file with Ktorrent or utorrent in WINE. Do so at, say 6am (YEP, Get up early or have an all nighter-2am to 6am are the best times for me).:-\"
In Ktorrent, open up settings or preferences and change the port to listen on to a higher number-this shouldn't matter though as it never has for me, I just do it to be double sure.

Don't enable upnp, it has only made mine slow. Play about with the rest to get best speed. Utorrent can be left as it is and I get a 700mb file in about 20mins (40max) Which, all things considered is plenty fast enough I reckon.

I have been down the port forwarding road and found it to be a windy, cumbersome path which rarely bore any fruit. It just complicates matters IMHO. But then again, I am just a reformed Joe Bloggs point click merchant who spent twenty years prior to finding Ubuntu imprisoned in Novell land.

Hope I have helped.

(Hijack time) If anyone knows how to beat the bandwidth shaping I have described, please please please tell. I want ***_UNLIMITED_*** COS THAT'S WHAT I PAY FOR:mad::mad::mad:

---

