---
title: "Multiple simultaneous local users - doable?"
date: 2023-06-17
forum: General Help
---

### Post by eosha on 2023-06-17
Forgive me if this is an obvious or stupid question; I've never tried this and I'm trying to learn the answer before I buy more hardware. 

I'm looking for a graceful way to allow multiple users (my kids) to use a single relatively beefy PC (locally, not SSH or remote access) simultaneously. For example, say I had 3 monitors, 3 keyboards, 3 mice. How do I create 3 different graphical user sessions and assign each their own monitor & input devices?

I see this is referred to as "multiseat". Reading old guides suggests that multiple graphics cards make this much easier.

---

### Post by TheFu on 2023-06-17
If it were me, I'd use cheap, low powered, used, desktops as X/Stations, then use xdmcp to access the main system. xdmcp has effectively zero security, so that could be an issue.  Or you could use x2go in a client/server setup.  Where I worked, my team of 5 would remote into the same "desktop" using x2go and work on the same documents together.

[https://tldp.org/HOWTO/XDMCP-HOWTO/index.html](https://tldp.org/HOWTO/XDMCP-HOWTO/index.html)

Heck, you might be able to find some excess free/cheap X/terminals (hardware) to use. I'd be afraid of the power they'd draw.  When Raspberry pi v4 come back in stock, they would be viable alternatives too - at $55/ea.  Every year, successful companies "excess" 1/3 of their desktops - including keyboards and mice, so if you have them at a local "computer showcase" - usually at the local city conference center over a weekend, these things are $5/ea.  In the 1990s, I picked up 3 IBM 101M keyboards for $0.50ea at one of those "computer shows".  Best $1.50 I've spent that I can recall - ever.

---

### Post by dragonfly41 on 2023-06-18
In past years I have also tried recycling parts (drives etc.) from local authority junk piles. But there in much work in cleaning and getting junk yard parts back to work. I do not use recycled goods available through Amazon.

My thinking in my late years as grandparent is to simply create a Virtual Desktop through an Azure account which is available on a Pay as You Go basis. Then use the current bare metal Ubuntu desktop as "Bob the Controller" transferring ideas and training between  parental (or grandparental in my case) Desktop and Virtual Desktop with 3 user (kids) accounts on Virtual Desktop. Advantage is that users can access from anywhere.

This is based on concurrent ruminations today about transferring knowledge and ideas to others remotely, between Desktop sessions.  Also in my case remote family members.

Going further there is the aim for the "master" desktop to train remote users (kids) in various subjects (and vice versa) and for this we can turn to automation scripts.

One vendor is Zapier.

There are others.

But passing structured knowledge (tips) on subjects such as backups (from pros such as @TheFu et al)  becomes a new skill to develop. There must be  better way than kids browsing forums and social media.

Knowledge transfer to next generation, in a structured way. A topic of interest to this old developer.

I am also using a ZeroTrust data vault so that family (and other) archives are secure.

Tresorit.com

---

### Post by yancek on 2023-06-18
The link below is to the Debian wiki which is detailed and current.

[https://wiki.debian.org/Multi_Seat_Debian_HOWTO](https://wiki.debian.org/Multi_Seat_Debian_HOWTO)

Another link, a little dated.

[https://docs.google.com/document/d/1LGUJnEZ7c6VP3upGLUYFddncEqKEW4GCDJKc0esoJbw/edit](https://docs.google.com/document/d/1LGUJnEZ7c6VP3upGLUYFddncEqKEW4GCDJKc0esoJbw/edit)

---

### Post by kinddolphin8827 on 2023-06-19
Just because a laddie or gentleman is older doesn't mean he or she can give up in their quest for knowledge. At many point in my short 35 year total life 16 of which I've been a proud participant in society and contributor to several Free and Open Source Software project although not as a developer and more so as a knowledgeable user. The prior is because for a great deal of the past 23 years. I was also taught by my parents that I should not only appreciate others for their knowledge but also respect them based upon not just on the merit of age but also their cumulative accrued knowledge of how the world works.

No question is a dumb or needless question, nor should anyone subject themself s to the at times degrading viewpoints of those around them. I'm a living example of this mantra as I was a special needs student (SPED), through out my primary and secondary and threw most of my short lived higher education career  and no matter how cruel the the bullies taunts and defaming comments towards me I quickly learned that I had  to and pretty much could only seek safety and reassurance from the adults in the room.  If any thing thees trials and tribulations made me into a fighter and I managed to graduate High school with not only a diploma but a prestigious award issued to me by the state of New Jersey for excelling in Cooperative education.

---

