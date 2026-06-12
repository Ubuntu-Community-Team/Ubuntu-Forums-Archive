---
title: "Can we make Ubuntu 22.04 desktop as a phone"
date: 2023-07-09
forum: General Help
---

### Post by satimis on 2023-07-09
Hi all,

Would it be possible to call on Ubuntu 22.04 desktop?

Can following software help?

**[COLOR="#FF0000"]Introducing the new Bing in Skype[/COLOR]**
[https://www.skype.com/en/](https://www.skype.com/en/)

**[COLOR="#FF0000"]Signal für Mobiltelefone[/COLOR]**
[https://signal.org/de/download/](https://signal.org/de/download/)
Kein Linux? (not for Linux)
    Signal für Mac (signal for Mac)
    Signal für Windows (signal for Windows)

[B][COLOR="#FF0000"]
Telegram Desktop[/COLOR][/B]
[https://desktop.telegram.org/](https://desktop.telegram.org/)

Thanks

Regards

---

### Post by TheFu on 2023-07-09
I used Skype for my home phone for a few months and had it on a Nokia N800 tablet for long international travels. It worked well enough for me to call others, but it didn't work very well for others to call me.

Ubuntu Desktop on a phone would suck.  The GUI needs to be custom for the screen.  The Nokia N800 ran a debian-based OS with a Maemo for the interface. At the time, it was amazing, but when I traveled, I still needed a keyboard.

For phone calls, you'll want to use any SIP client and pay for a SIP service so you can connect to real people who use regular phones (landlines) and businesses.  Over the decades, I've been using SIP, it has long been great as a home phone.  I pay $60/yr for phone service with excellent quality and can connect to my home account from a tablet or phone or computer when traveling (most of the time).  Some hotels block nearly all UDP, so a VPN that can tunnel the SIP UDP traffic to the internet is needed.  I use wireguard for that.

The 20-something people seem to have all switched to whatsapp for communicating. Guess they don't care about privacy.  

Telegram fails on many levels.  Maybe you'd want to use Signal if you want something like that. 

For my family, I run a Nextcloud Talk voice/video chat system to use. [https://nextcloud.com/talk/](https://nextcloud.com/talk/) We can all see each other and talk.  Because all the traffic is on my server and uses https tunnels, it is secure enough.

I've considered running a Matrix server. [https://matrix.org/](https://matrix.org/)  It seems to have the ability to hook into most other communications apps, so I'd only need 1 view to see everything or to respond.

If you don't care about privacy at all, check out **meet.jit.si**. Any webRTC web browser can be used.  A few LUGs have been using meet.jit.si since covid kept us all at home. We routinely have 5-25 attendees to our virtual meetings. The last 6 months, it has been more like 15+.

---

### Post by satimis on 2023-07-09
> **TheFu said:**
> I used Skype for my home phone for a few months and had it on a Nokia N800 tablet for long international travels. It worked well enough for me to call others, but it didn't work very well for others to call me.

Ubuntu Desktop on a phone would suck.  The GUI needs to be custom for the screen.  The Nokia N800 ran a debian-based OS with a Maemo for the interface. At the time, it was amazing, but when I traveled, I still needed a keyboard.

For phone calls, you'll want to use any SIP client and pay for a SIP service so you can connect to real people who use regular phones (landlines) and businesses.  Over the decades, I've been using SIP, it has long been great as a home phone.  I pay $60/yr for phone service with excellent quality and can connect to my home account from a tablet or phone or computer when traveling (most of the time).  Some hotels block nearly all UDP, so a VPN that can tunnel the SIP UDP traffic to the internet is needed.  I use wireguard for that.

The 20-something people seem to have all switched to whatsapp for communicating. Guess they don't care about privacy.  

Telegram fails on many levels.  Maybe you'd want to use Signal if you want something like that. 

For my family, I run a Nextcloud Talk voice/video chat system to use. [https://nextcloud.com/talk/](https://nextcloud.com/talk/) We can all see each other and talk.  Because all the traffic is on my server and uses https tunnels, it is secure enough.

I've considered running a Matrix server. [https://matrix.org/](https://matrix.org/)  It seems to have the ability to hook into most other communications apps, so I'd only need 1 view to see everything or to respond.

If you don't care about privacy at all, check out **meet.jit.si**. Any webRTC web browser can be used.  A few LUGs have been using meet.jit.si since covid kept us all at home. We routinely have 5-25 attendees to our virtual meetings. The last 6 months, it has been more like 15+.
Hi,

Lot of thanks for your detail advice.  This is solely an experience.  I'll start testing Matrix

I'm running VirtualBox and KVM here.  I can install any Linux distribution on VM/Guest

With a brief search on Internet I found following links:

1)
**[COLOR="#FF0000"]Install Synapse Matrix Server on Ubuntu 22.04 (Jammy Jellyfish)[/COLOR]**
[https://techviewleo.com/install-synapse-matrix-server-on-ubuntu/?expand_article=1](https://techviewleo.com/install-synapse-matrix-server-on-ubuntu/?expand_article=1)

2)
**[COLOR="#FF0000"]How to Install Matrix Synapse Chat Server on Ubuntu 22.04[/COLOR]**
[https://www.howtoforge.com/how-to-install-matrix-synapse-chat-on-ubuntu-22-04/](https://www.howtoforge.com/how-to-install-matrix-synapse-chat-on-ubuntu-22-04/)

3)
**[COLOR="#FF0000"]Create a Chat Server Using Matrix Synapse and Element on Ubuntu 22.04[/COLOR]**
[https://www.vultr.com/docs/create-a-chat-server-using-matrix-synapse-and-element-on-ubuntu-22-04/](https://www.vultr.com/docs/create-a-chat-server-using-matrix-synapse-and-element-on-ubuntu-22-04/)

4)
**[COLOR="#FF0000"][Matrix] Matrix Synapse auf Ubuntu Server 22.04 LTS mit nginx, PostgreSQL, Let&#8217;s Encrypt SSL und ufw installieren sowie mit Element verbinden[/COLOR]**
***[COLOR="#0000FF"](Install Matrix Synapse on Ubuntu Server 22.04 LTS with nginx, PostgreSQL, Let's Encrypt SSL and ufw as well as connect to Element)[/COLOR]***
[https://www.c-rieger.de/matrix-synapse/](https://www.c-rieger.de/matrix-synapse/)
**This German article is quite detail**

5)
**[COLOR="#FF0000"]How to install Matrix Synapse Home Server[/COLOR]**
[https://upcloud.com/resources/tutorials/install-matrix-synapse](https://upcloud.com/resources/tutorials/install-matrix-synapse)

I'll go through them first.

Regards

---

### Post by TheFu on 2023-07-09
Getting voice traffic to work without lots of signal latency can be a challenge. If you hear stuttering or delays, check the latency.  I have dedicated VoIP hardware to avoid this. I used to run VoIP servers inside VMs and I don't even want to admit some of the hacks I did to get skype-Out working. It was buggy and a pain. Mainly, not getting calls from businesses when I was using skype was a big issue.

Youj'll know more about matrix than I do fairly quickly.  I only have a 10,000 ft view from a few zealots that run Matrix as their communications all-in-one solution. The main problem with Matrix is that native clients don't seem to exist or suck. I haven't looked in about a year, so maybe that has changed?  You'll want to find the voice bridges to see which networks matrix supports, so your friends and family don't need to switch just to talk with you.   Matrix does have a SIP bridge, which is how to get calls from normal people.  Hummmmm.  I like having my phone system ring rather than needing to keep computers or tablets or smartphones connected.  There are 6 handsets around the house, so getting to a phone to answer or place a call isn't a big deal.  OTOH, I couldn't tell you where my smartphone is located right now. I'm not attached to it and sometimes forget about it for a week at a time.

---

### Post by satimis on 2023-07-09
> **TheFu said:**
> Getting voice traffic to work without lots of signal latency can be a challenge. If you hear stuttering or delays, check the latency.  I have dedicated VoIP hardware to avoid this. I used to run VoIP servers inside VMs and I don't even want to admit some of the hacks I did to get skype-Out working. It was buggy and a pain. Mainly, not getting calls from businesses when I was using skype was a big issue.

Youj'll know more about matrix than I do fairly quickly.  I only have a 10,000 ft view from a few zealots that run Matrix as their communications all-in-one solution. The main problem with Matrix is that native clients don't seem to exist or suck. I haven't looked in about a year, so maybe that has changed?  You'll want to find the voice bridges to see which networks matrix supports, so your friends and family don't need to switch just to talk with you.   Matrix does have a SIP bridge, which is how to get calls from normal people.  Hummmmm.  I like having my phone system ring rather than needing to keep computers or tablets or smartphones connected.  There are 6 handsets around the house, so getting to a phone to answer or place a call isn't a big deal.  OTOH, I couldn't tell you where my smartphone is located right now. I'm not attached to it and sometimes forget about it for a week at a time.
Hi TheFu,

I'll follow the German article to install Matrix server

4)
**[COLOR="#FF0000"][Matrix] Matrix Synapse auf Ubuntu Server 22.04 LTS mit nginx, PostgreSQL, Let&#8217;s Encrypt SSL und ufw installieren sowie mit Element verbinden[/COLOR]**
**[COLOR="#0000FF"](Install Matrix Synapse on Ubuntu Server 22.04 LTS with nginx, PostgreSQL, Let's Encrypt SSL and ufw as well as connect to Element)[/COLOR]**
[https://www.c-rieger.de/matrix-synapse/](https://www.c-rieger.de/matrix-synapse/)

I'm now going through this article first.  Coming to;
**[COLOR="#FF0000"]Im Rahmen der Installation werden Sie zuerst nach ihrer Matrix-Domain (bspw. matrix.ihredomain.de) gefragt und dann[/COLOR]**
**[COLOR="#0000FF"]During installation you will first be asked for your matrix domain (e.g. matrix.yourdomain.de) and then[/COLOR]**

I suppose **[COLOR="#0000FF"]"matrix.yourdomanin.de"[/COLOR]** is a subdomain.  Can I create it on any of my domains?  Then create its website?

**[COLOR="#FF0000"]Do you know where is the Matrix server help forum[/COLOR]**

I haven't used my German for long time and have some difficulty reading the article.  Language is very strange.  You need to use it frequently.

Regards

---

