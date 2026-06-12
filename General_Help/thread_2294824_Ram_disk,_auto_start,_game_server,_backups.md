---
title: "Ram disk, auto start, game server, backups"
date: 2015-09-13
forum: General Help
---

### Post by RageMachine on 2015-09-13
Hello everyone again! It's been some time since my last visit lol. I have a new project that i have been playing around with, its been frustrating me for about a week. Me and a few friends have been playing minecraft on my server, Its running just fine, no lag or anything but i'm a tinker and well just want the most out of everything lol. ( BRB need more coffee )

So i Finally got around to upgrading from my old socket 775 pc to a nice HP Proliant DL360 G6 U1 server. It's happily living in my DIY server rack right beside my bed lol. but ill get right to it now as to not bored you guys with stories and what not's.

server specs: DL360 G6 1U

OS Ubuntu 14.04 64bit
2X intel xeon x5550 @2.67GHz
32Gb Ram
2X 1TB HDDS
2X HP 146Gb 15k rpm sas drives ( striped or mirrored cannt remember lol)
2X 1 Gbps nic cards

Network Specs: 

Weak link 30 down 3 up
linksys wrt54g - Soon to be replaced with a Pfsence box
TP-Link 24port Gigabit switch -Unable to use nic teaming with this switch :(

Games i want to or do have servers set up:

Vanilla Minecraft -working
Ftb Minecraft -Working
Dont starve - Work in progress
ARC - Work in progress
the forest - Work in progress
and others - Work in progress lol

Now that is out of the way, Yes i am using Ubuntu 14.04 desktop as i have switch from windows to linux and like my GUI's ( although i do like Guake )..... still need windows for games though :(

i Don't run the servers at the same time as i don't have the bandwidth to do so, So what i have thus far is 2 servers that run smooth but i like to tinker, and before i switch to linux i was running my servers on windows with ram drives super simple to set up. 
for Linux not so much, i have done my googling and had a few oops that didn't work and well i got ram disk working but their is no auto save stuff or if their is i missed it

This is what i do for the ram disk still haven't added to the auto mount thingy 
> sudo mount -t tmpfs -o size=4096m tmpfs ramdisk/mcserver

and from what i have tested so far, it does not seem any faster than just loading from HDD. Also unless i messed it theirs no auto save / backup with this option, as this is going to be a 24/7 server and i wont be around to back things up all the time it would be nice to have some sort of backup in place.

my other problem is that i have to log in for my servers to auto start, i want it so if i push the power button everything just works 

Any help would be greatly appreciated, if you have any questions just ask and ill get back to you with any more info that you need.

---

### Post by TheFu on 2015-09-13
I'm lost.  1 question per thread please.

In 14.04, services starting at boot are controlled by **update-rc.d**. The service needs a start/stop script like all the others in /etc/init.d/

Backups - there are many threads in the "server" subforum about backups.

I don't know anything about ramdisks. Never needed them under linux.  Databased can be "pinned" in RAM, if you want more performance, but that is a DB feature.

None of these things use a GUI.

---

