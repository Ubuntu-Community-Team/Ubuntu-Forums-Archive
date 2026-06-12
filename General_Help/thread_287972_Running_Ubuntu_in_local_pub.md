---
title: "Running Ubuntu in local pub"
date: 2006-10-29
forum: General Help
---

### Post by jbodell on 2006-10-29
Hello all,
I run a pub in the UK, and I've set up a PC running Ubuntu for the customers to use for free internet. The reaction has been very good. The PC I am using is a very old compaq with only 128 ram. The computer will not boot if you attempt to put more ram in. 

At the moment I have the computer running KDE, and there are no speed/efficiency problems at all. I have tried XFCE and IceWM, but most of the customers find KDE the most familiar and so I have stuck with KDE. In fact, most people do not even know they are not using xp. 

I have run into a couple of problems which I'm sure someone will know how to solve. 

Firstly, i keep finding that the panel is being modified by some of the customers. This is probably inadvertant. This means I keep having to reconfigure the panel. Ideally I would like things like the desktop Icons and panel to be unchangeable to anyone but myself. 

Secondly, the customers are downloading files and executing them. The PC is not intended for anything but web use, so ideally they would not be able to download files, or double-clicking the files would do nothing. On one occassion for example, I had a customer who had downloaded and then doubleclicked a video file 28 times! XFmedia was running 28 times and I had to reboot!

Thirdly, obviously I want the content to be suitable since it is a family pub. So far, I have just used the firefox extension Pro/Con and this has been extremely successful. While this has worked well, it is only a click of a button away from being turned off, since this extension has no password protection. Is there any way I can make sure it can't be turned off?

Overall, I must say this has been very successful, and the PC gets a lot of use everyday. Those who noticed the PC was not running XP were shocked by its ease of use, some have asked me for a copy of Ubuntu.

These are not major problems, but could spare me some time if I can fix them. Any advice would be of use. 

Thanks in advance!

---

### Post by PriceChild on 2006-10-29
> **jbodell said:**
> The PC I am using is a very old compaq with only 128 ram. The computer will not boot if you attempt to put more ram in. Check that the ram you're adding is of the same freq.

---

### Post by Choad on 2006-10-29
just an idea off the top of my head, but could you not create a new user, and then *not* give it write permission to its own home space.

that way everything you do will require sudo authentication

or, alternitavely is could scream and die....

just tried it, and it screamed and died. you would probably be better to go down the other route, and leave it fully enabled then go round specifically removing write privileges from the .mozilla directory to stop tampering with extensions for example.

*or* very simply, you could trust the people to do what they like, and maybe set the background of the desktop to be a message saying "please dont do this, that and the other" then (the clever bit) back up the whole /home/user directory to a protected part of the filesystem. then if anything goes wrong, its a simple 

sudo cp -r /backup/ /home/user/

maybe?

---

