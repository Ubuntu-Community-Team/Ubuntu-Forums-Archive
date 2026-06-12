---
title: "Offline LAN-only networking?  (previously mistitled: &quot;Offline Intranet Networking?&quot;)"
date: 2022-09-24
forum: General Help
---

### Post by YQ002lc2 on 2022-09-24
Use Case:

1. A family does not use or want to use internet. 

2. They have some very old computers with ubuntu server and ethernet cables but no switches or networking gear. 

3. All networking must be offline and wired with no RF pollution. 

4. They want something akin to a samba file server to share home movies and files. 

5. They want to be able to collaborate on projects within shared directories. 

6. They want to be able to email (offline) and instant message (offline)

7. They want to be able to print to an offline network printer. 

Questions:
1. Can you point me to some tutorials on that type of setup?
2. I'm not sure even what to call such a use case? 
I think if I knew the correct terms, I'd perhaps be able to find what I'm looking for. 

Thank you.

---

### Post by TheFu on 2022-09-24
LAN-only networking.

Basically, setup everything like you would for internet, but don't connect to the internet and you'll need to run a local DNS so all clients can find each other.  Without a router, getting each client to communicate with the others will be more hassle than it is worth.  If off line, get a cheap router.  Depending on the number of client machines, you may want to add dumb switch to expand the number of ports the router has.  A dumb switch is effectively invisible, so you can add as many extra ports as you like 8-port dumb switches are USD$20 or less.

If there isn't any MS-Windows, your life can be much easier. No samba needed, as NFS can be used. Then all storage can be considered 'local' and if you like, you can make it so that any person can login on any workstation, yet have all their settings, programs, documents available.

Of course, none of this is 1-click installs.

As for working together, check out nextcloud.  That does storage, chat, voice, video conferencing as well as integrations for web-based libreoffice (think google-docs) all within 1 tool.  It doesn't do email, but does almost everything else.

You didn't mention calendaring.  Calendaring can be separate or part of a "communications server" like Zimbra.  

Zimbra provides enterprise calendaring, which I'm addicted to. I tried to use nextcloud's calendaring, but found it lacking.  Zimbra supports all the expected standards for SMTP, imap, ical, and some lite-DMS.  Zimbra is a bit of a hog, however.  It is complex and upgrades tend to suck.  I do that every 2 yrs and it takes hours.

Nextcloud has an app-plugin architecture which makes installing most addons 1-click, but complex addons do need manual configuration.  Nextcloud is a php+mysql webapp. I'd bet it can run on a raspberry pi, though I run it inside a KVM virtual machine. At the next upgrade, I'll try to move it into an lxd container. Should work fine.  I've moved wallabag into an lxd container and that was a fantastic choice/move.  Keeping each major network service self-contained is a best practice. LXD makes that possible with minimal overhead and not having to learn the entire "docker-way". Docker requires thinking very different.  Docker containers are like cattle, not your pet dog.  Be prepared to kill and eat the cattle.  In short, expect upgrades for docker to be a complete wipe so that data and settings need to be separate from all the code in the docker container.

With NFS, you can use normal Unix permissions with unix groups to allow everyone to work on the same files in the same directory, just at different times.  I've posted my "working together" steps in these forums a few times. Look for those. It is standard Unix stuff.  It doesn't work with Samba networking, sorry.

You can use dnsmasq as an easy DNS server. Much easier than running BIND9.

If the computers aren't 64-bit with 4G+ of RAM, you'll probably not want Ubuntu.

If you are new to all this stuff, perhaps using an all-in-one distro would be easier?  I don't know any current names of those, but "Clark Connect" was one about 10 yrs ago.  There were about 5 of them in competition.  Because they are offline, that removes many security concerns that make those all-in-one distros a terrible, terrible, choice.

I'd say using "offline" is causing you the most problems.  "offline" means to me, no networking at all.  That isn't what you want. LAN-only networking is what you want.  That is still online, just without internet.

---

### Post by MAFoElffen on 2022-09-24
I'm going to say a few things to clear up some contradictions, and confusion in your plan. Not a criticism. More of an observation.

- You can connect two computers and network them together with a cross-over cable (connected between the two computers). Any more than two, then you need a network switch. 

- To have email, even if offline, you need some sort of internet connection from an ISP. 
 -- If hardwired to the house, you need a modem/router. Most ISP's provide a combo modem/router/switch (most also come with an internal wireless router which you can turn off per your requirements) to connect to their services.
 -- You said no RF, so tethering to a smart-phone or using it's wireless access point is out.
 -- Some large cities, depending, groups there may have free, old-school land-line dial-up modem internet access. You would have to check on your own.

- Any printer hooked to a networked computer can be a shared network asset.

- On your network server, set up file shares. Those files shares, once you shard them users of groups, can share what is in them. That is what Samba Server is, for sharing file shares and printers. Though you don't necessarily need Samba Server do do either. That is just one way, of many ways, of doing that.

If you go to a computer recycler, you can get networking devices real cheap. You just need to know what you are looking for.

A good place to start for reading resources would be the Ubuntu Server Guide. Then a suggestion of joining a LUG. (A local Linux User's Group)

---

### Post by TheFu on 2022-09-25
Just want to point out that it is possible to have local-only email between people on the same LAN. 

They won't be able to communicate outside the LAN with anyone else, so it won't be very exciting for just a few people, but it is possible.  Most of my systems send emails to a central email server on the LAN. If they are to my local domain users, they don't go anywhere else. Because that email server knows how to send to external addresses too and is connected to an SMTP gateway with internet access AND my ISP connection allows direct SMTP on the internet, emails to the world, bi-directional, are possible.  Running an email server just for a family really isn't very useful, but it isn't hard either.  As soon as all the anti-malware, anti-spam, stuff required on the internet is removed (not needed), email becomes really, simple.

A little postfix, some dovecot, and you have an email server that can accept authenticated emails via SMTP (587/tcp or 465/tcp) and allow clients to read those emails via IMAP (993/tcp).  The server-to-server email part (25/tcp) wouldn't happen ... that's what allows email servers around the world to communicate directly.

I'd think that using nextcloud chat/talk on a LAN-only setup would replace the need for email completely.

---

### Post by grahammechanical on 2022-09-25
I may be talking a lot of nonsense but as I understand things every network adapter (ethernet or WiFi) has its own IP address. It is these IP addresses that allow machines on a network (WAN = Wide Area Network = Internet or LAN = Local Area Network) to communicate with each other.

You will need a Router/Hub (which will have its own IP address) that every machine must be connected to by ethernet cable. This then becomes a LAN.

It might be possible to use a standard email client to send messages (emails) to other machines on the LAN using the IP address of such machines. I think that you will need to dedicate one machine as an email server which should be switched on all the time. You might also be able to use the same machine as file server for the movies. There are certainly applications that can do this but i am not familiar with them.

The first problem is physically setting up the LAN. If the router/hub is not connected to a telephone landline or to a broadband cable and the WiFi adapter is switched off in the router settings then the LAN will be isolated from the WAN. Any WiFi adapters in the machines will need to be switched off in the OS settings and in the BIOS. Then there will be no more WiFi or internet pollution.

Regards

---

### Post by TheFu on 2022-09-25
grahammechanical - good points.  

I jumped passed all the physical connection stuff. Figured it was obvious, but maybe it isn't?

While computers should be able to find each other using pure ethernet, it is a hassle and I've never seen that actually work, hence the need for a cheap router to make that issue go away.  Plus a cheap router will provide DNS, DHCP, and prevent IP collisions.
[https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) tries to explain.  That article is from over 10 yrs ago. Good news is that newer routers make this solution much, much, much, easier.

Plan on getting a router. $10 or $100 really doesn't matter.  I am a bit concerned about really old computers being used. That usually means really old networking and slow networking makes for a bad experience on a LAN. I suppose 100 base-tx should be fine.  My network has been 1000 base-tx for over 15 yrs now because 100Mbps is slow when large files are involved or remote X11 windows are used.  Here's hoping that 10 base-tx isn't involved. That is like having 2400 baud dialup. Too painful for consideration on a LAN.  Before 1000 base-tx, cables had to be specific. With the GigE standard, the NIC automatically discovers and handles different cable connections.  The cables all need to be CAT5e or better too.  Avoid CAT5 cables. Today, I doubt there is any real price difference between CAT5e and lesser cables.

All of this will be overwhelming to a non-technical person, I fear.  If the OP doesn't have much Linux experience or any networking experience, it is doubtful to get this working in any reasonable time.  If I were trying to setup all this, and assuming I know what I'm doing, it would be at least 20 hrs of effort between networking, OS, servers, backups, email, nextcloud, and setting up the clients.  At least.  If MS-Windows is involved, add 5 hrs extra for each system, since in a small environment, it would need to happen via point-n-click on each box, unlike linux desktops which could be handled over ssh all at once using clusterSSH or ansible.  With Linux, managing 2 or 2000 desktops really isn't any more effort thanks to network tools and free, F/LOSS, automation.

---

### Post by grahammechanical on 2022-09-25
@The Fu

Lacking networking/server experience I am trying to imagine a solution by working from the bottom up. Right now I am wondering about these machines. Did the family buy second hand machines with Ubuntu server already installed? Are they happy using command line programs that run on a server OS or would they prefer a desktop environment? What Linux or Ubuntu distribution would depend upon the hardware specification of these machines which we do not have knowledge of.

From time to time users of this forum have asked questions about email servers and media servers. An internet search will provide a selection of applications.

Regards

---

### Post by MAFoElffen on 2022-09-25
If you had a bit more skills and experience, your server could be your router as 'some' of it's services.

For a LAN without a router, you can do that with static addresses and a basic network "switch". <<< Notice I didn't say hub. 

You would really have to look for a 'hub' these days, because they cause network collisions. A hub is really dumb and just broadcasts an Ethernet packet to all it's ports at once. I have one as a network diagnostics tool. (To tap into a network with a network sniffer).

A basic network switch keeps a MAC address table, that is sort of like a router table, which it uses to direct Ethernet traffic to a (single, directed) destination at the MAC address level.

As for chat, you can chat between computers on a LAN with XMessage. Really old-school, low-level basic chats, but is still there in the Linux Graphics Layer. It is a learned skill.

I think what you need as basic skills:
- What a Local Area Network is, basic Networking, and how to set one up.
- Setting up groups, adding users, access and permissions.
- What a server is, basic server services, how to setup file shares.
- Other mid-level server services.

Been thinking about this. I think you might want to look at "Zentyal" Community Edition. It is an Ubuntu Based server, that is visually GUI based from a browser, geared as a Small Business Server. Not as many technical skills to learn to get it up and running. Since not really wanting to connect to the internet, not many outside security concerns or considerations. I think it fits into your use case.

Now waiting on your feedback to clarify what you might want to do.

---

### Post by HermanAB on 2022-09-26
There is also Retroshare.

---

### Post by TheFu on 2022-09-26
> **HermanAB said:**
> There is also Retroshare.

I was thinking about RetroShare too. It meets many of the checkboxes, but I feared the gpg security of getting everything setup and the 1980s "feel" of the program would turn them off.  If you want to securely share stuff (almost anything) within a group of people, RetroShare uses gpg encryption for storage and transfer to all nodes.  Within a LAN, it should be relatively easy for 1 person to setup.  

Over the internet connections are a bit harder.  At least 1 of the systems needs to be accessible to all the others and performing gpg key management in a secure way is a steep learning curve to use the system.  Within a small LAN, it is probably 100x easier, as only 1 person would really need to understand everything and the security would be secondary ... almost in the way.

Zentyal was one of those all-in-one distro names I couldn't remember. Definitely worth a look. May be exactly what you need.  I've considered setting it up, just to use the LDAP user management stuff.

---

### Post by YQ002lc2 on 2022-09-27
Thank you all for your responses!
I was expecting maybe 1 response, but it was really heartening to see so many amazing responses! 
I feel like I'm in a master class learning a lot from everything you all are saying.

I now know I want an "offline lan-only network".
And it sounds like I probably need to get some sort of network switch. 

[B]
Clarification of the Use Case:[/B]

1. The computers:
a. are old windows machines people were getting rid of, 10-15 years old, some 32-bit and some 64-bit with between 3 and 4 GB of RAM. 
b. I put ubuntu server on them because it doesn't require much RAM and because I've casually used ubuntu and the command line since about 2008.  
c. The console with the occasional lightdm and fluxbox are more than sufficient for this family's needs.
d. There will be no Windows machines in this network.  

2. I have zero networking experience other than I managed to directly connect two ubuntu machines via an ethernet cable and SSH in the past. 
I'm just trying to help them set this up and hoping to learn through the process.

3. The number one goal of this setup is to connect these computers to share files within a family that lives pretty much all in one place.

For instance: 
Computer 1 makes a home movie of grandma's 90th birthday accessible to the network.
Computer 2 and 3 work within a directory of photos to prepare a montage for the family get together. 
Computer 4 accesses the home movie and the prepared montage to display it at the family get together. 

4. Email, voicemail, instant messaging, calendaring, etc. are all interesting hypotheticals (I'd like to learn about), but are not absolutely essential as these users can see each other face to face and chat via other means.
(I will explore those more once #3 is basically achieved.)

5. No one in this family has an IT security background so keeping everything offline is hopefully just simpler and worry free in terms of not getting hacked or something like that. 

6. The family is very concerned about RF and EMF exposure. Any ideas for faraday caging wired offline computers and electronics are also appreciated.  

7. Printing to a network printer is also a goal, but is secondary to #3 above. I'll work on it more once the basic network is setup. 




Thank you again for all your responses! 

I'll be studying them and querying with the correct terminology now.
Thanks so much!

---

### Post by TheFu on 2022-09-27
Do yourself a favor and get a router, not a switch.  Someone needs to do the routing and enabling routing on a linux desktop is a security problem. Any old $10-$20 router will suffice and make your life 1000x easier than dealing with a network switch-only network.

RF that is disabled in the BIOS, assuming there is any at all will be sufficient.  The whole EMF sensitivity stuff is a boondoggle.  

Claims of hyper sensitivity to EMF have always failed scientific research.  Nothing in any dwelling has enough power. Some of the double-blind study results are pretty funny, since the participants usually perform worse than random guessing would return.
RF exposure power follows a 1/r² law, I'm sure you know, so the power is exponentially less as distance from the source increases.  Even commercial cell tower output becomes harmless if you are farther from the tower than it is high.  Being nearer isn't an issue, unless you spend 10+ hrs a day for over a year in the exposure area.  I can see a cell tower from where I'm sitting now, during daytime.  It doesn't worry me at all, but there are 15 houses and a church closer. None of the houses are in what I'd consider the danger area.  The church is, but nobody sleeps there every day, so I'm not worried about the weekly 2 hr exposure.

---

### Post by ian-weisser on 2022-09-27
Here's how I would do it:

Design:
- A router is indeed a good idea for the physical networking. Makes all the networking easy and is very much worth the low price.
- I would select Nextcloud, a pre-configured, web-based file sharing, file storage, collaboration, messaging, calendar, etc. server. There are other ways to do it, but Nextcloud is easy for the users to understand and for a beginner admin to install quickly and easily.

Implementation:
1. Put your server hardware online long enough to install Ubuntu Server and the [Nextcloud snap]("https://snapcraft.io/nextcloud"). The snap avoids all that tedious mucking about configuring the web server and the database.
2. You spend an afternoon learning how to use Nextcloud (LAN-only) for your proposed workflows and setting up the other user logins.
3. Install your cabling and physical LAN network.
4. You give each user a 10-minute orientation of what you learned. Since Nextcloud uses a web page to access all activities, 10 minutes is all most people need.

---

### Post by The Cog on 2022-09-28
I disagree about needing a router. A router generally has few interfaces: common is to have one network port for connecting to the internet, and perhaps 4 switch ports for connecting local kit to. This gives you at most 4 local devices, maybe 3 PCs and a printer. Is that enough? I think you probably want an 8-port switch. An ethernet switch does not need an IP address.

You could set up using static IP addresses, manually configured in each PC, and just use IP addresses when connecting from one to another. You can use a hosts file in each computer to map names to addresses so you can connect to them by name instead of an address. 

Or you could use a DHCP server to hand out IP addresses to devices as they connect and ask for one. This would be a machine that you always leave on, one of your computers, or a raspberry pi, or a small cheap router. If you use a DHCP server, you will want to configure it so that it always gives the same IP address to the same machine that asks for an address. If you use a router, you only need a single connection to it to just use it as a DHCP server.
In a small wires-only network, I think using a DHCP server is probably an unwanted complication. New additions to the network will be rare so configuring an IP address in each PC is likely simpler than maintaining a separate device.

However, if you choose to use a local server like the Nextclout that ian-weisser suggests, I think that can also act as the DHCP server.
My main point is don't go for a router just because people say you need a router - know what you want it for first. You will likely want a switch as well unless your router has enough enough ports from its internal switch exposed.

Also think about the physical layout - are all the PCs in one room? How will you cable them all up to a single switch? Maybe two switches in different rooms, connected by one cable would be better (in which case a router could serve as a 4-port switch and DHCP server as one of the switches).

P.S. Re-reading your original requirements:
* You something akin to a samba server would be the logical place to run a DHCP service for handing out IP addresses.
* No RF pollution - depending on how strict this is, you may be able to use ethernet-over-mains adapters to reduce the amount of ethernet cabling you have to install. A bunch of these adapters will effectively form a physically distributed switch.

---

