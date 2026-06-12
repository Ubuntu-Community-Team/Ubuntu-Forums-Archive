---
title: "Remote clients / thin clients?"
date: 2007-04-29
forum: General Help
---

### Post by spiker611 on 2007-04-29
Hey guys, i'm a bit curious if this is possible.

My dream setup would be having my current computer (very powerful) upstairs where is, hooked up to a wired and wireless network.  Downstairs I want to put a very small PC with my HDTV where I can have something like mythTV to record shows and stuff, but I want everything to be saved on either my computer upstairs, or my server (also on the network).  I'd also like to play games in large resolutions on the HDTV downstairs, but do not want to pay a ton for hardware, so is it possible to somehow play a game on the upstairs computer, and like transfer it downstairs to the 'weaker' computer?

Is this possible?

Thanks!

---

### Post by m.musashi on 2007-04-29
Yes, very possible. I've actually been looking at little thin client boxes from HP to do basically the same thing. I want the desktop to hold all sorts of video files and then browse them with MythTV and play what I want without having to deal with the DVDs anymore. I don't have the knowhow yet to actually do it, but after talking to some people I know I can.

I don't know about the game part though. Sorry.

---

### Post by spiker611 on 2007-04-29
In order to make myself a bit more clear:

What I want to do is have a sort of (virtual) KVM over the network to my upstairs computer, but with no KVM switches or anything.  It would need to be able to transfer at least 720p HD video and video games if possible.

---

### Post by craigsharp on 2007-04-30
There might be a way,  just not any i know about.  Y not have you powerfull computer downstairs, where it seems like you'll be using it the most.  and a less powerfull computer upstairs with maybe a cheap pentium D processor and decent vid card for light gaming.  You can get a pretty good gaming rig for under 500 bucks.

---

### Post by spiker611 on 2007-04-30
'Cause I need a very small PC for downstairs, like even fanless.  My powerful one is huge and has 10 12cm fans going all the time, so it's a bit out of the question.

---

### Post by craigsharp on 2007-04-30
good grief,  what do you have in that thing?  what's ur specs please?

---

### Post by m.musashi on 2007-04-30
If you are looking to buy hardware, take a look at these [thin client](http://h10010.www1.hp.com/wwpc/us/en/sm/WF04a/12454-12454-321959-338927-89307.html) options. I bet something like this would work. The rest will just be setting it up to do what you want.

---

### Post by Jose Catre-Vandis on 2007-04-30
If you have the kit to try things out, have a look at edubuntu. This has a thin client setup (LTSP) (Linux Terminal Server Project)by default. If nothing else this will at least help you to see the direction you need to go in. I run edubuntu on my server and family use thin client logins to access their data. LTSP may not be up to coping with HD V or gaming, but if your supercomputer "upstairs" can dish it out, I don't see why it wouldn't work?

---

### Post by craigsharp on 2007-04-30
How would a person be able to play games off of another computers processor on a thin client.  This too interests me now.

---

### Post by spiker611 on 2007-04-30
> **craigsharp said:**
> good grief,  what do you have in that thing?  what's ur specs please?

an Athlon x2 4400 oc'd to ~2.75ghz (air)
2gb DDR (its a s939) oc'd to ~300mhz
x850xt pe (waiting for r600 because I blew out my geforce :lolflag: )

My monitor with the computer is a 19 inch and i'd really love to tap into that 1080i/720p goodness downstairs.  I'm thinking of maybe doing a KVM switch downstairs between the mythTV box and an extension of my computer's cables.  Hmm

But i'd still really love to find a way to do this, theres definitely enough bandwidth (1gb/s).

My only concern is that taking the screen and compressing / sending it downstairs via the network would be extremely processor intensive, but with a dual core I could run the game one one core and the compressor on the other.  And 2gb of ram is more than enough to run both.

I'd even be interested in partnering up with someone to program something like this!

---

### Post by spiker611 on 2007-05-01
Okay, so I tested this out between my newly installed server and my computer.  I used XMDCP to connect to my computer via a 100mbps connection (although my router is crap, so who knows..and im working on getting a 1gbps router).  The server has nothing special except what it needs to get by, but when I used XMDCP to access my computer and opened up a 720p HD trailer, I was impressed.  It was running at like 10fps at fullscreen.  I'm not sure if there's improvement to be done in the fact that the server's graphics / CPU are terribly comprimised for HD playback, and besides I plan on having a decent solution for hardware for my 'thin' media box downstairs.

My question is, is there any way I can optimize XMDCP and/or the display manager running across the network in order to reduce traffic and junk?

Also, is there a way to take advantage of dual core goodness, such as having all of the remote junk (xserver, XMDCP, gnome?, etc) running on one CPU while having the system / applications running on another?

---

### Post by spiker611 on 2007-05-02
Update:

I noticed that network usage during HD XMDCP streaming was hovering between 8 and 10 MB/s.  Thats about 80mb/s, very close to the theoretical max of my network, showing that it really is bottlenecked.  Anyone know the true mbps of 720p?  Ah, well, I can find it.

---

