---
title: "Ubuntu budgie, Plex and shield"
date: 2020-07-05
forum: General Help
---

### Post by Cory_Douglas on 2020-07-05
So I've put UB20.04 on main PC at home and an having a lot of problems trying to get Plex working properly and being able to access anything on it (that are my own files)from other devices such as NVIDIA shield. Xbox 1 and phones. Keep getting no soup for you or can't connect to server  Can see and access everything on main PC just fine. Shield and Xbox are connected by cable and everything else by wifi. Just changed main PC from windows to UB. This is the only thing I'm having any dramas with. Have tried searching and figuring out out myself. Would appreciate any help in this matter as I don't want to go back to windows, but I need my theatre room content. Thanks in advance

---

### Post by CelticWarrior on 2020-07-05
Welcome.

Have you ever had the Plex running as you wanted in the same network but with Windows as the Plex server?

---

### Post by TheFu on 2020-07-05
How are you trying to connect?  There are 10,000+ different protocols?

I've never seen "no soup for you" as any error message.  Normally, the EXACT ERROR can be google'd for a solution. We don't want images. We want text, error, messages.

Have you looked at the system log files? Those **will** show any denials. If there aren't any denials in the logs, the problem is upstream, so check firewalls, DNS, avahi. 

What is your skill level with Unix?

> Shield and Xbox are connected by cable and everything else by wifi. is vague. This PC is also wifi?  Servers shouldn't be wifi and should have static IPs assigned.

---

### Post by Cory_Douglas on 2020-07-05
With windows I had the Plex server running on the PC and it was fine, all on the same network and was fine 99 percent of the time.

---

### Post by Cory_Douglas on 2020-07-05
Sorry about the confusion. PC, Xbox and shield are all connected by cable. Everything else like phones, tablets etc are over wifi and were able to connect to Plex in windows without problem and stream content. Skill level is above beginner level but I learn quick and can follow advice and instructions ok. If you could point me to any guides etc regarding getting log files or what I'm looking for in the firewall and such I will have a good crack at sussing it out wouldn't mind learning about these protocols as well Cheers for the reply

---

### Post by Cory_Douglas on 2020-07-05
From the PC end I can look into the shield. But when I'm on the shield trying to look at the Plex server which I've populated with files or dress that they Plex server is there but server is unavailable to check connection and retry

---

### Post by TheFu on 2020-07-05
Sounds like you have less than 2 yrs of daily Unix experience.

How is the plex PC connected to the network? Wired?  Does it have a static IP? It should. Can all the clients "find" the plex server using 'ping'?  They should. These are things the admin should configure. It is standard IP networking stuff.  There's no "magic" here.

What protocols are being used that you want the clients to find the server using?  NFS? DLNA? Something else? 5 other things?  I use NFS and DLNA with my plex setup, but some people use other protocols. DLNA is handy for some clients. NFS is handy for Unix-to-Unix access.

As for guides, google is your friend.  I've been at this way to long to be good at making suggestions for someone relatively new. I'd just read the manpage to get the poop on programs. Sadly, Plex doesn't provide a manpage, which sucks. The Plex team has strange ideas about many things - but they do make a good DLNA server. I'm much less thrilled with most other stuff they do and where they place things by default on our systems.

As for logs, search for "ubuntu log files" will find a how-to guide, but really all Unix systems use logs the same way and put them in the same, /var/log/ directory.  There must be thousands of guides on help.ubuntu.com and the Ubuntu Wiki and in the "Ubuntu Desktop/Server Guides"

**Update:**
Plex sorta just works, assuming you know to setup DNS and understand Unix file permissions.  There are lots of things to do to make things "easier" over the long term, but most Unix noobs don't because that seems like too much trouble.  Helped a friend setup a plex server on a cloud provider last week. There was only 1 complexity, that was accessing the http://{IP}:32400/web/ after the initial install. In a home environment, access from the same LAN should just work.  I don't have plex on 20.04. That release is too new for me.  I'm on 16.04 still. Sometime this fall, I'll consider moving to a new LTS.  New is the enemy of stable, especially with non-FLOSS programs like Plex.

---

### Post by Cory_Douglas on 2020-07-05
Thanks. Will have a hunt tomorrow

---

