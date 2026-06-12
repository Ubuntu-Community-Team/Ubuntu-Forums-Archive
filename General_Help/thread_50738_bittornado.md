---
title: "bittornado"
date: 2005-07-21
forum: General Help
---

### Post by k4rp0r on 2005-07-21
New guestion (again)...

somethimes when im using bittornado it says for example: "port 6681 is blacklisted".
how can i change the port?????????

thanks.

---

### Post by horsefactory on 2005-07-21
Use --minport and --maxport to change the ports, so --minport 3400 --maxport 3410 will give you the port range of 3400 - 3410 free.

---

### Post by k4rp0r on 2005-07-22
ok, but how can i use those commands, i mean where to type/but them, how to use them?? (cant find find anything)

---

### Post by bored2k on 2005-07-22
[QUOTE=k4rp0r]ok, but how can i use those commands, i mean where to type/but them, how to use them?? (cant find find anything)[/QUOTE]
 Just launch bittornado, click on advanced and change your ports there. Make sure your ports are forwarded.

[http://www.portforward.com/](http://www.portforward.com/)

---

### Post by k4rp0r on 2005-07-22
there arent anything that says port in bittorrent---->advanced section. all there is are these: "try this before using", "documentation" and "name/comment translations". thats it! Nothing about ports :(

---

### Post by bored2k on 2005-07-22
[QUOTE=k4rp0r]there arent anything that says port in bittorrent---->advanced section. all there is are these: "try this before using", "documentation" and "name/comment translations". thats it! Nothing about ports :([/QUOTE]
 You said bittornado, not bittorrent. They are quite different.
[CENTER][IMG]http://img319.imageshack.us/img319/1304/see3eu.jpg[/IMG][/CENTER]

And by the way, you are using an old bitTORRENT. The new one is a lot better and does include it:
[CENTER][IMG]http://img330.imageshack.us/img330/7636/si9mf.jpg[/IMG][/CENTER]

---

### Post by bored2k on 2005-07-22
About blacklisted ports:
> So why is port 6881 (or whatever) blacklisted ?

Some tracker administrators are trying to avoid the slow upload that happens when ISP's throttle the bandwidth of those customers trying to connect to others on ports within the ranges used by p2p clients. This would result in slower download times for everybody. And this throttling unfortunately includes the Bit Torrent port range of 6881-6999.

So what happens is, those trackers reject any IP addresses trying to connect who are listening on any of the ports within those ranges, and some of those trackers may blacklist those IP's for 48 hours. So the torrents show red faces, and even if you change your listening port, you are unable to connect because of the 48 hour ban.[http://azureus.aelitis.com/wiki/index.php/PortIsBlacklisted](http://azureus.aelitis.com/wiki/index.php/PortIsBlacklisted)

---

### Post by k4rp0r on 2005-07-22
sry about that... my bad. I mean bittornado, there arent anything that says port in advanced section... :( do you know any other direction where i can change the ports like root terminal or something like that????

---

### Post by bored2k on 2005-07-22
[QUOTE=k4rp0r]sry about that... my bad. I mean bittornado, there arent anything that says port in advanced section... :( do you know any other direction where i can change the ports like root terminal or something like that????[/QUOTE]
 Are you using the Graphical Bittornado ? If you do, it should look like my previous picture. If you are using bittornado via the command line interface, you could set them like the following example:
```
btdownloadgui file.torrent --minport 2234 --maxport 2240
``` or
```
btdownloadgui --url http://www.foobar.foo/file.torrent --minport 2234 --maxport 2240
``` 
Where the minimum port would be 2234 and the maximum allowed 2240 (bittornado uses one port per .torrent -unlike azureus wich uses one for everything.. well, two if you count the dht tracker port-). 

You don't need root access or anything for this btw.

---

### Post by k4rp0r on 2005-07-22
ok, thanks foe the help :)

---

### Post by Mr. Electric Wizard on 2005-07-22
Hey, where in the world are you guys getting your .torrent files from?
I've been out of the loop for a while, and saw that suprnova.org does not offer files any longer...
I am looking for TV programs like Revelations, or Medium?

---

### Post by bored2k on 2005-07-22
[QUOTE=Mr. Electric Wizard]Hey, where in the world are you guys getting your .torrent files from?
I've been out of the loop for a while, and saw that suprnova.org does not offer files any longer...
I am looking for TV programs like Revelations, or Medium?[/QUOTE]
 Anyone who posts illegal torrent sites with illegal files should be aware of the consequences. This is not a forum dedicated to illegal P2P. You can browse yourself for them.

---

### Post by Mr. Electric Wizard on 2005-07-25
Ohh, no speak of bittorrents, only processing programs.
Got it.
Won't happen again.

---

