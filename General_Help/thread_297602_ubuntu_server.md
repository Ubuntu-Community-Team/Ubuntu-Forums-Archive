---
title: "ubuntu server"
date: 2006-11-11
forum: General Help
---

### Post by 13ojo on 2006-11-11
hi,

I've just installed etch into a old pentium 2 machine to use as a server.

I chose to install the DNS, and the LAMP options.


My main idea was to run this server as one i could netboot off of. Plus a few other neat things i heard off.

Here's what i need help with

1) Configuring netboot, for windows xp installer & etch's installer (preferably with the machine itself as a source as i have the cd's, just would be nice to boot from net instead).

2) set it up as a ftp server (total of 20GB worth of hardrives). Would be nice to have this thing copy repositories that are common in linux. Eg KDE   & Gnome. So this machine gets the updated repositories and then any other machine can update through it.

3) Use the server to do what i heard is called "broadband load filtering". Someone told me they run a linux box with a program that does that. This is one of the main things i want. My current setup is through a router, would i need to configure the server to be a dchp server? or can i continue to use the router (Dlink 604g+)

4)Eventual print server, in current position its not not one, but when i buy a new hub this is something i would like to do, current setup for printing is rather tragic.

5)If possible a scanner server, as this is the only pc that has a scsi card (i own old scanners).

6)Also it would be nice to use the server pc as a firewall. (Possibly with a web interface, as then not so linuxy people can still have access to the firewall)

Pc's specs are

200MHZ pentium 2 processor
a pci graphics card and accelerator card (NOT IMPORTANT ANYWAY)
not certain but most likely 128mb ram
3x HDD adding up to 20GB
10/100mb ethernet card PCI

It has ubuntu server edition 6.10 installed on it, It has DNS and LAMP installed (options on the server disc). I also installed SSH on it, so i can access it from my other machines. It has NO monitor and NO keyboard and NO mouse (trivial as i can get its console on any machine, and that's all thats really needed)

An answer to if any of the questions if possible would be greatly appreciated, as would opinions on any of this. 

Thanks

---

### Post by 13ojo on 2006-11-13
wow okay i thought someone would know something.

one of the things i asked was how to set up a ftp server!.

simple..

---

### Post by keithweddell on 2006-11-13
A quick search in the wiki shows up a couple of Howtos for ftp.

[Try this]("https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=ftp&titlesearch=Titles")

Keith

---

### Post by tminuszero on 2006-11-13
That's a huge request for help. I think you might get more help if you broke it down into separate posts.

#1 - I know little about this
#2 - See Keith's link. I would recommend proftpd. As for repositories, that's a different question entirely.
#3 - I'm not sure why you would need this. How is the load on your network now? If it's maxed out, you have other issues. Are you attempting to get a speed boost?
#4 & #5 - This can be done, I'm sure, but you would have to provide more details. Linux network only? Samba? Macs? PC's? Many users? You also need more RAM. For that machine you should be able to pick it up cheap.
#6 - After all of that you also want to make it into a firewall? Don't. While your machine can certainly *be* a firewall, you don't want everything else on this server as well as a firewall. That will open up attack vectors for anyone trying to get past your firewall, which negates it's effectiveness. IMO you have to pick - #6, or 1-5. If it's that important, buy another cheap machine .

---

### Post by 13ojo on 2006-11-15
1) no one does, thats why i asked, its very undocumented and people who do it dont seem to want to share the wealth :(

2) ftp is extremely minor, it would be more of the, im running a server why the hell not, ill check out the link later

3) was the main one, its just because of the arguments that come at hand when sum1 checks their email and someone else is playing a game or downloading. People often spit their dummies and i know at least 2 culprits who will pull out ethernet cables for other pcs because they think they will get a boost (they do but i hate having to fix this later, no one ever plugs back in)

4) &5), 4) mainly, i see it as the main use aside from load filtering/balancing. Its pretty much windows pcs, though it would be nice if it could work with the dual boot pc (windows and linux) indiscriminatly.

6) then no sir i wont,i just thought it would be another app to run, (btw i thought firewalls allowed for rules between local/remote traffic, only the FTP would be remote so that could be left out, everything else is local.

I know its alot, but i figured if i asked lots of questions i would get a response from ones people knew.

I dont require someone to asnwer them all in one post, but if i get as many 2c as possible i may get most of the gaps filled in.

---

### Post by koenn on 2006-11-15
it's a bit overwhelming, all those questions, plus the answers are going to be quite long. you're asking for small howto's really ...

here's a firewall setup i once did. It's debian-based but will apply to ubuntu as well
[http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm)

here is a server setup i once did, including a basic ftp setup. again, debian-based but will apply to ubuntu as well
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#ftp](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#ftp)

I would also recommend not to have the firewall and the other functionality on the same machine. 

network boot : never tried it (don't have boot-capable NICs) but seen plenty of howto's and articles : [http://www.google.com/search?hl=en&q=linux+network+boot](http://www.google.com/search?hl=en&q=linux+network+boot)

network load balancing : this is probably something you could do on the firewall/gateway. It's a complex field : you have to have a pretty clear and concrete idea of what you want, before you can even think (or ask) about how to do it. then, there are several ways of approaching it : balancing by using DNS, or by using NAT, or use clusters, use Quality of Service / prioritize applications / etc ...

---

### Post by tminuszero on 2006-11-15
13ojo - no problem. I don't know enough to help you set up most of this, but there are some good how-to's out there. I would recommend looking in the wiki and trying to set up one service, and then try to ask questions. Otherwise most people will ignore your posts. That's my experience, at least. I tend to run on :)

The print server should be the easiest to set up. If you can set the printer up on that computer, then you should be able to share it on the samba network using the Printers interface in the Administration menu. You might have issues with your particular printer, but hopefully not. 

As for the firewall, you ***can*** do what you're talking about, but all it takes is to get burned once to never do it again. Take it from someone who's been burned ... to a crisp! It was years ago, and I was much less careful then.

As for #3 - is this for a workplace? I'm guessing not ... I'm hoping not. I would just tell them that after much work the network's load balancing is finally in place and that it will get messed up if communication with a machine on the network is cut off suddenly. If they don't know any better, maybe they'll believe you :D

---

### Post by 13ojo on 2006-11-17
ironically it is on a kind of workplace.

though i doubt this lie would affect it, a pc would get yanked, no immediate problems so people will continue on.

A find told me he used a program called QOSbalancer which he saw in synaptic (hes running kubuntu).
currently i cant find any form of load balancing that isnt to prevent your web page goign down.
Mainly i want to priotize outlook express/thunderbird applications or there ports..
Anyone else heard of QOSbalancer? or can suggest applications for me?

Currently i dont have much of a firewall installed. Theres the protection of the router persay, But thats not really a firewall. Some individual PCS have firewalls however.

With the print server, its the ubuntu server install. No monitor and keyboard on the PC. SO no real admin menu, like in normal linux. Im doing everything i do from a remote terminal. How do i set up samba via the terminal? and install printers?

With that link, ive tried googling before. Most talk about Booting installers that download what they need from the world wide web. Id prefer to store this info on the machine.

PS. would it be possible to set up the server to download all my mail?. It downloads it all, and then i can see what messages etc ive got from another pc. And choose wether to delete them from the server or not?. That way i can check my mail in either OS in my dual boot, as i wont have some messages in linux and some in windows.

---

### Post by koenn on 2006-11-17
> How do i set up samba via the terminal
I asked myself the same question once, tried it, did it, and took some notes : 
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#smb](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#smb)


> and install printers?
did not try that yet  :-)  but i'd be thinking
- install cups
- cups probably can be configured from command line or by editing config files

-if necessary, printers can also be shared via samba

[http://packages.ubuntulinux.org/edgy/net/cupsys](http://packages.ubuntulinux.org/edgy/net/cupsys)
you will have to read a decent cups howto to get this gioing, i think

---

