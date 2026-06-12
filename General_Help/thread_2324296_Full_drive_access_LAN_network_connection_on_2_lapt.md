---
title: "Full drive access LAN network connection on 2 laptops..."
date: 2016-05-12
forum: General Help
---

### Post by Salty-san on 2016-05-12
So I want to be able to do a 2 comp connect over whireless/bluetooth so that I can gain full access to one's drives/partitions just like it were an external HDD for some scanning/recovery. Basically  a LAN or stronger, except I rather do it without Ethernet or USB cable if possible (but those options still on the table, it will just take longer).  One will be the one I will work from and do the scanning (and Windows though it shouldn't matter) and the other with the drives I want to scan and which will run from a Live USB enviroment (so nothing installed). Both laptops. I will need to do a fully connected, stable one with no problems therefore. So my questions are...

How do I setup such a connection from Ubuntu, a detailed and step by step as possible? Mine is MATE enviroment 15.10....OR....What's the best distro (even non-Ubuntu, sure, I'm open) for setting up something like that and that can be done live without problems? Should I use some server version instead? lol...Are there softwares involved to make networks work, since it seems to me the options are very limited. Also terminal commands?? (idk anything about them).....Do I need to set up all sorts of paramaters and such for permissions?

Either way all I really want is to be make it to the network established point, so I could use some help....

---

### Post by TheFu on 2016-05-12
If you want to scan 1 system, boot that system using a flash drive or liveBoot CDROM.  What is the issue you think you are looking for?  That will determine which distro would be best.  Doing it over a network really isn't very useful.  For example, scanning a disk for failed sectors really needs direct access to the SATA command set.  eSATA/SATA are 100% equiv, but USB disk connections suck in comparison and don't provide the same access.

If you are scanning for viruses, the local boot thing is also better.  

There are lots of youtube videos about this stuff.   You'll need to know many different shell commands. Impossible to say what without knowing what you are looking for.

If you are still stuck on this "do it over the network" thing (which I think is a waste of time), then I wouldn't bother attempting anything except wired ethernet.  Any $5 switch or $15 home router can connect these two systems. That doesn't provide any protocols for the client-server to communicate.  Depending on the sort of scan, there might be better protocols, but none that I can think of now come anywhere close to booting a live Linux system off a flash drive to do the scanning.

Forget wifi, forget usb, forget bluetooth. Those physical layers suck in oh-so-many-ways for stuff like this.

---

### Post by Salty-san on 2016-05-12
> **TheFu said:**
> Forget wifi, forget usb, forget bluetooth. Those physical layers suck in oh-so-many-ways for stuff like this.

Yeah they did feel very limiting but just making sure. As for ethernet, the issue is mostly physical damage making contact a real problem which is why I was looking to wireless first. But shouldn't a USB cable connection virtually be the same?

As for what this is for,  I mentioned recovery...as in scan for missing files, recover them, and so on to be perfectly clear. It needs to be over 2 computers due to the nature of the problem, or I wouldn't ask for something so roundabout.

To make my request more clear and streamlined though...I want to be able to directly access the drive/partitions of machine B from machine A, just like they were part of machine A as much as possible. So what would allow me to enable that the best? Given the limitations of using Live USB at least. 

It's really just a network question of how do I make it to have as much access between two machines as possible, and I am mostly interested in the software side really.

---

### Post by TheFu on 2016-05-12
You cannot scan a disk from a remote system to recover files.  In fact, having the normal OS running can cause the missing files to be overwritten.

Pull the drive, find a free SATA/eSATA port on a different machine and scan using badblocks and the testdisk suite.

The first thing you learn in forensics is NEVER modify the original disk.  They use modified SATA cables to prevent **any** writes over that connection. Also, they use eSATA docks, to have access to low-level disk commands, which are not supported any other way.

USB is NOT the same as ethernet, though you can run ethernet over USB connections.  I don't know how to do this.  I have a USB-to-GigE adapter. To the system, it looks like a GigE ethernet device and the wire is plugged into a normal GigE ethernet switch.  All networking is handled just like it was a normal ethernet card.

How much are you willing to lose by running the OS on the disk you want to scan?  If you really don't care, then just ssh in and run bad blocks on the machine.  ssh is just like being there. Doesn't matter if it is 1ft away or 26K miles away, ssh works the same.  You won't be "scanning" anything from the 2nd machine.

The next best option is to remove the HDD and connect it to the 2nd machine, then run the **testdisk**/**badblocks** programs that way, but if you connect over USB, I don't know if these will work or not. They probably will, but with some limitations.  

Of course, before you begin any scanning, you should use **ddrescue** to make an image of the problem disk. Lots of guides for how to use these tools exist, so I won't post googled results.

---

