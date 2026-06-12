---
title: "Strange problem with MSN messengers"
date: 2006-10-12
forum: General Help
---

### Post by Starlight on 2006-10-12
Hello! I don't know if it's the right place to post it, because I don't even know if it's in Ubuntu problem, hardware problem or something else... Basically, the problem is that MSN messengers sort of disconnect me, without even telling me. When it happens and I'm chatting with a person, suddenly I stop getting messages from them, and they stop getting messages from me. When I try to send something, I don't get any errors, MSN still says I'm online, the buddy list is visible and it updates without any problems... But the other person sometimes doesn't see me online at all, or sometimes they see me online, but don't get any messages from me... and when they try to send me anything, they get an error that the message can't be delivered. It happens with aMSN, and with GAIM... so it's not a problem with my MSN programs, I guess. But it's really annoying. And the weirdest thing is that sometimes when I'm chatting to more than one person at the same time, that problem can only happen with one person, and not the other. I've also noticed that it happens with some people much more often than with others. Usually even disconnecting from MSN and connecting again does't help...

So... can anyone help me fix it?

---

### Post by PriceChild on 2006-10-12
It could just be a dodgy internet connection.

Are you on wireless?

---

### Post by Starlight on 2006-10-12
yes, I'm on wireless, but according to a wireless monitor applet, the quality is always between 100% and 125%, so it's very good... and even when I can't chat with one person, I can chat with other people with no problems....

---

### Post by Starlight on 2006-10-13
so... does anyone know if it's possible to fix it?

---

### Post by Rhubarb on 2006-10-13
125% ??? How did you get that signal strength?
I'm PriceChild with this, I think it'd be a poor internet connection.  Could be your drivers, could be your router.
Try downloading a big iso from the 'net and see if it lets you download it all (try this while chatting on msn).
Also try chatting on msn with a wired connection - if this still cuts out, try booting off the live cd and use gaim.

---

### Post by Starlight on 2006-10-13
That's what the gtk-wifi applet says... Well, right now it says 85%, but it's often above 100%. And it's not signal strength, it's connection quality... Some time ago when I was using KDE, I had a panel applet which gave more details... it had both a "connection quality" and "signal strength" meters, and while the first one was sometimes above 100% as well, the second one was always less than 100%... around 70%, if I remember correctly.

Well, it can be a poor internet connection, but how does that explain the fact that it happens when I chat with some people, but not other, even if I'm chatting with them at the same time? And it even happens with certain people more than with other... As for downloading large files, I don't really have any problems with it. If it's really a bad internet connection, then it works in a very selective way... only MSN, and only with some people and not other...

I have one problem with my internet connection, but it's just that the pings to the router can be as high as 2000 ms... I just did a ping to one website for a few minutes, and the connection seems really good. The average ping is 348, and the packet loss is only 9%.

---

### Post by Rhubarb on 2006-10-13
Do any of your msn buddies have problems with their buddies on msn?
It does certainly sound rather odd.
If you can, I'd still try to connect to your router via wired ethernet.  I've witnessed many strange phenomena with cheap wireless routers.
Another thing you could try is to use someone else's 'net connection and see if that makes any difference.
Maybe it is a software problem? - Try it on a wired connection from the live cd.
I hope you get this rather peculiar problem sorted out.

---

### Post by Starlight on 2006-10-13
> **Rhubarb said:**
> Do any of your msn buddies have problems with their buddies on msn?
It does certainly sound rather odd.
If you can, I'd still try to connect to your router via wired ethernet.  I've witnessed many strange phenomena with cheap wireless routers.
Another thing you could try is to use someone else's 'net connection and see if that makes any difference.
Maybe it is a software problem? - Try it on a wired connection from the live cd.
I hope you get this rather peculiar problem sorted out.
No, they don't have such problems... 

Unfortunately, I can't use a wired internet connection, because the only available internet connection here is wireless.

---

### Post by Rhubarb on 2006-10-13
I seem to recall in gaim there's a "use alternative http method" option somewhere, I think it's hiding in accounts somewhere in gaim.
There's a chance this may fix up your problem, maybe the router you're connecting to doesn't like the msn protocol or ports when going to a specific IP.  Sounds very weird though.
You sure you're not running winblows there?  :-D

---

### Post by Starlight on 2006-10-13
No. I'm sure I'm running Ubuntu :D Thanks for the idea, I'll try to do it... maybe it will work better... :)

But I still think that's one of the weirdest problems ever o_O

---

### Post by Starlight on 2006-10-13
ok.. after I did that, MSN can't connect at all... here's the error I get:

"Connection error from Notification server: Reading error"

---

### Post by Starlight on 2006-10-14
bumping this.....

---

### Post by Rhubarb on 2006-10-18
Nope, I'm stumped.
I dunno what's going on there.
Anyone else out there got any ideas?

---

### Post by Starlight on 2006-10-18
Wow, it seems I'm so unlucky enough to get a problem which no one ever experienced apart from me...

---

### Post by Starlight on 2006-10-18
update: the same thing happened on AIM... and I was chatting with the same person I chatted on MSN before when it also happened...

---

### Post by paganini on 2006-10-18
Hi,

I've seen strange problems happening when your DHCP lease is set too short. I had a problem where a session would disconnect every N minutes, exactly. A quick inspection on /var/log/messages revealed that dhclient was requesting a new IP exactly at the times I had the problem. I changed the lease time to one full day and the problem disappeared.

Of course, I'm supposing you're on a LAN, using DHCP. Could be something entirely different, and the only way to know is to sniff the network packets with tcpdump or something like that.

---

### Post by Starlight on 2006-10-23
Yes, I'm using DHCP... but I don't really think that's the problem, because it happens randomly, not regularly. And it happens with some people more often than with others... and when it happens, my internet connection still seems to work well because I can chat with other people, browse websites....

---

### Post by speedsix on 2006-10-23
I get the exact same problem, posted about it last week aswell.

It happens with all msn clients, gaim/amsn etc. It even happens with the proper MS msn under XP in VMware!

Random disconnects but like you say with the friends list still visible. Lots of 'timeout' error messages and messages not being sent.

Basically very unreliable.

---

### Post by Starlight on 2006-10-23
that sounds just like my problem! Does it also happen more often with some people than other for you?

---

### Post by Coburn on 2006-10-23
I have a similar problem.  New at Gaim.

A buddy of mine started messaging me.  Only the messages were blank.

I was using a hotmail and a yahoo login simult.

Plus I'm on dialup.

---

### Post by speedsix on 2006-10-24
> **Starlight said:**
> that sounds just like my problem! Does it also happen more often with some people than other for you?
Yes it seems to be worse with some. It's completely unreliable though and I haven't the foggiest where to begin troubleshooting the problem. I can talk fine through skype messaging to the same people.

---

### Post by Coburn on 2006-10-26
> **Rhubarb said:**
> I seem to recall in gaim there's a "use alternative http method" option somewhere, I think it's hiding in accounts somewhere in gaim.
There's a chance this may fix up your problem, maybe the router you're connecting to doesn't like the msn protocol or ports when going to a specific IP. :-D

If you are looking for this option in the latest Gaim, I found it.

Accounts > Double-click your MSN v Show more options > MSN Options > Use HTTP method

---

### Post by speedsix on 2006-11-06
Changed my router and msn works fine. I'm pretty sure it's related to the mtu setting on the router, my old one was 1492 which caused problems.

---

### Post by pinkpajamafairy on 2006-11-08
Im having similar problems as well. Im either getting signed out constantly, or get timeout errors. Tried clicking the http method, but im still getting signed out.

---

### Post by Ramses de Norre on 2006-11-08
I've experienced this in breezy, I never found a fix but it just went away after a couple of days..

---

