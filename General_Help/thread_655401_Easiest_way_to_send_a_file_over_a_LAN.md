---
title: "Easiest way to send a file over a LAN?"
date: 2008-01-01
forum: General Help
---

### Post by Bou on 2008-01-01
Hi,

One of my flatmates has finally installed Ubuntu on her PC. I would like to be able to easily send her files from my computer, but I don't know how to do it. I thought Pidgin and Bonjour would be the way to go, but it seems you can not send a file through that protocol.

Is there an avahi-related solution that will allow me to send her files without having to share folders and telling her to download this and that? Just throw stuff at her?

---

### Post by icheyne on 2008-01-01
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Borbus on 2008-01-01
Well you will be glad you are using Linux now, setting up NFS is approximately 10x easier than smb (windows file sharing).

---

### Post by Bou on 2008-01-02
Well, I meant something faster and simpler not requiring any setting up on the receiver's side.

Please take a look at [this bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus-sendto/+bug/179808") to see a couple screenshots of what I had in mind. Anything remotely similar to that would do.

---

### Post by chewearn on 2008-01-02
> **Bou said:**
> Well, I meant something faster and simpler not requiring any setting up on the receiver's side.

Please take a look at [this bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus-sendto/+bug/179808") to see a couple screenshots of what I had in mind. Anything remotely similar to that would do.

I sure would want such feature; think of all the files spammer will want to send your
way.

Wait, thinking of spammer, why don't you use email then?
 :lolflag:

---

### Post by Bou on 2008-01-02
I'm no expert but AFAIK email has to go through an AMTP and POP server to reach its destination, is much slower and has size limitations. I would prefer to send files right over the lan, unless you can do that by email?

---

### Post by shad0w_walker on 2008-01-02
Surely you could just use a USB drive? It's not over the network but sneaker nets can still be a whole load faster than networks at times. Not to mention it's not in danger of the cable being yanked or anything.

---

### Post by Bou on 2008-01-02
> **shad0w_walker said:**
> Surely you could just use a USB drive?

Sure, that's what I currently do. I mean, it's a feature I can do without but it would be cool nonetheless. "Send to &#8594; my friend" would be handier that looking for a drive, see if it has enough free space, copy stuff, take it over to my pal's room and tell him what it is he must get from the drive. It's just a couple clicks and be done with it.

---

### Post by icheyne on 2008-01-02
You could always FTP to the web or even use something like [http://drop.io/](http://drop.io/).

---

### Post by danwood76 on 2008-01-02
You could use MSN or ICQ, both have file sharing features and can be used under linux ;)
Much simpler than setting anything up anyway.

regards,
Danny

---

### Post by Bou on 2008-01-02
Yeah, those are all perfectly good methods. I didn't know drop.io, thanks! :)

---

### Post by Borbus on 2008-01-02
Thing is, setting up NFS is just as easy as setting up msn or icq. I think people are too afraid of a little config file editing sometimes. With NFS you get a much faster and better solution too.

---

### Post by notwen on 2008-01-02
I also recommend NFS.  You can mount a folder on your friend's Ubuntu PC locally on your machine.  Setup is very simple.  I use NFS to stream music/video from my desktop/server to my laptop.  Check out the how-to [here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server").  I have NFS server setup on my server/desktop and i store everything on it and access it from my laptop or my gf's laptop using NFS.  Hope this helps and good luck. =]

---

### Post by icheyne on 2008-01-02
> **Borbus said:**
> Thing is, setting up NFS is just as easy as setting up msn or icq. I think people are too afraid of a little config file editing sometimes. With NFS you get a much faster and better solution too.

[I totally agree.]("http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing")

---

