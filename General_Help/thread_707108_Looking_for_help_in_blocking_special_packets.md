---
title: "Looking for help in blocking special packets"
date: 2008-02-25
forum: General Help
---

### Post by Zeroangel on 2008-02-25
Hey all, I play an online game called Battlezone 2. In the game there is currently an exploit circulating where one can crash any game by joining using a nickname which utilizes a certain pair of characters.

What I need to do is -- 

Packet sniff myself. Log the contents of all packets coming in on UDP port 17770 prior to the game being crashed.

Find the affected string out of the dump -- hopefully something like UserJoin(name.exploitchars.otherstuff) -- (where exploitchars are the 2 characters which cause the crash)

Find a regexp which will be able to block the whole packet no matter where in the name the exploit characters are located.

Set up a windows firewall app which watches all of the UDP packets (I dont need to worry about the TCP packets -- as the TCP packets are not the affected ones, even though the game uses TCP on that same port) and blocks out the affected ones.

Now since the game runs under WINE, I can use a linux app to watch my packets. Problem is I dont know where to begin. A hint or 2 please?

---

### Post by SpaceTeddy on 2008-02-25
it could be possible what you ask... but, seriously, wait for the game to be patched ! what you are asking here is a lot of work, not to talk about that you would slow down traffic on that port significantly.

here is what you would need to do...

you need to send the packets on the specified port into a userspace filter which you write yourself. As soon as you have control over the packet you can then parse it and look for the specified content.

a start how to use userspace filtering would be found here
[http://www.penguin-soft.com/penguin/man/3/libipq.html]("http://www.penguin-soft.com/penguin/man/3/libipq.html")

but we ware, this is pretty heavy stuff on your iptables and maybe need a recompile of iptables and your kernel...

I would wait for a patch of the game...

---

### Post by Zeroangel on 2008-02-25
Thanks for the info, unfortunately waiting for a patch isn't really an option. And a recompile of IPTables sounds pretty heavy -- would I really need to do that besides? I mean an ordinary packet sniffer like airsnort can watch packets on wireless networks and dump their raw output to file -- so shouldnt a program on my local machine be able to sniff my packets, or at the very most just set up a proxy server on my own machine with those capabilities?

I will look into userspace filtering, however.

---

### Post by SpaceTeddy on 2008-02-25
getting the pakets is not the problem. You can do that with any number of tools real easy... tcpdump, wireshark, etc...

The problem is blocking them if some content is detected. Since logging them does nothing you have no control over the paket. That is why you need userspace iptables, to be able to drop the pakets if you find something that should not go through.

maybe i misunderstood you ?

---

### Post by Zeroangel on 2008-02-25
Nope, I get what you're saying -- about the difficulty getting a program to filter packets like that. But I will deal with that later.

My first step, then is just finding out what the affected packets are. Thats all I need right now.

Run the needed program to monitor the packets
Start up Battlezone 2
Have someone crash my game using the exploit
Stop the packet sniffer and analyze the output

--------
I will work on the Blocking part later (For blocking, I will be using windows program -- as it is a Windows game)

Once I can write a suitable filter, I will be distributing the filter to the Battlezone 2 community.

---

### Post by SpaceTeddy on 2008-02-25
if you want to have the packets, use wireshark. that is pretty straight forward and gives you nice tools. But remember to log the whole paket, and not just the header, that has to be specified in the configuration.

also, you might want to consider replying to any malicious paket with a RST or FIN to instantly close the connection. also, if you have already have the paket, you might want to block someone who send that for a short period of time...
just running ideas through my head...

---

