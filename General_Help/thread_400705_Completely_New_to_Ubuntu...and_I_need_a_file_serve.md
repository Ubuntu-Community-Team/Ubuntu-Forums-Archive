---
title: "Completely New to Ubuntu...and I need a file server..."
date: 2007-04-03
forum: General Help
---

### Post by The Great Inert on 2007-04-03
As the title implies, I am completely new to Ubuntu and would greatly appreciate any setup advice more experienced users can offer.  I would prefer to run Ubuntu Server if at all possible, because I have had experience running Server 2003 and don't particularly care for it as a program.  

As you read, please forgive my networking ignorance.  Though I have over twenty years of experience working with desktop computers, I don't have the slightest idea of how networking works on a technical level.  If any of what I am about to write doesn't make sense, please feel free to ask detailed questions.  I will try to get the answers as soon as I can.

The first thing to know, I guess, is that I am attempting to set up a computer that will act as a common hard drive for thirty-three other computers.  This file server, for the next two years or so, will not store anything more complex than simple Office documents, the majority of which will be Word documents and Powerpoint presentations. 

All of the computers (the 33 in one main room and the other one that I have segregated as the file server) all connect to the Internet through a main server that is located off-site.  As far as I have been able to determine, the main server does nothing more than act as our gateway to the Internet.  It runs the firewall that keeps people out of our network.  It connects us to the Internet.  The server doesn't seem to do anything more than that.  It cannot (I know for a fact, because it is against security protocols where I work) be configured to act as a file server.  It is also running Server 2003.

Our IP addresses do appear to come from this computer, and they are static in that they do not change.  Once a computer has been attached to a wall jack or router, the address it gets stays the same unless you plug the computer's CAT5 into another jack in a different part of the room.  (For example, if I plug computer 22 into jack 4, its assigned IP address is 19.909.88.64.  This computer will stay 19.909.88.64 until and unless I plug it into jack two, at which time it might become 19. 909.82.61.  The same is true for routers: the IP will change only if I plug the router into a different jack--i.e., a router plugged into jack 6 will always have the same IP addresses assigned to it, unless I plug it into jack 14.)  At present, no computer is able to see any other computer on the network, but they can all access the Internet.  That reminds me: our main off-site server also runs the proxy that prevents users from accessing objectionable websites.  This proxy runs through a specific VLAN that cannot, on the user level, be bypassed.  

The 33 computers on my network are all running XP Pro.  They have been given unique station names and are part of XP's default group, WORKGROUP.  Ultimately, they should all be allowed to access each other's hard drives through the network; for now, it will suffice if each computer could save basic Office document types onto a centralized hard drive (the Ubuntu file server.)  The computers should all be able to access (save, edit, delete) these files regardless of what computer the file was created/saved on.  (In other words, if I created a Powerpoint presentation on computer 18 and saved it to that computer's hard drive, I should be able to access that same presentation from any other computer in the immediate network.)  

Ideally, the people using Windows shouldn't know that there is any difference in OSs when they save their files; the Ubuntu server should appear as another hard drive in the MY COMPUTER menu on their computers, or as a accessable network location in the OTHER category in the same menu.

---

