---
title: "Azureus - Can't connect to seeds"
date: 2008-01-19
forum: General Help
---

### Post by cyclingman on 2008-01-19
I'm using Azureus 2.5.0.0 on Gusty Gibbons, but I cannot connect to any seeds. I've tried with multiple torrents, but all of them give me, for example; seeds 0 (259). My faces are always green saying that this "means that everything is going fine".

I can connect to peers on the other hand, but never any seeds, therefore my download speed is always 0 B/s (as well as my upload speed). I've tried changing my port number; didn't work, I've only just started using it, so it can't be that EVERYONE has blocked me. anyone got any ideas?

---

### Post by cyclingman on 2008-01-22
Thanks for all the help ...  ¬_¬

---

### Post by ew16301 on 2008-01-22
You could try using the deluge torrent program.

---

### Post by Het Irv on 2008-01-22
What ISP are you using, many ISP have put blocks in place to stop people from using torrents.  Comcast is one.

---

### Post by cyclingman on 2008-01-23
I used to download with the same torrent software and ISP before, I'm pretty sure its not that (they haven't told me anything). I'm with orange broadband (in the UK).

I'll give that other software a try. For some reason, when I try installing bittorent, i can't find the program anywhere :(

---

### Post by cozmicharlie on 2008-01-23
If you have all green you should be able to download.  By seeds I take it to mean you are trying to download music or video from a bittorrent tracker.  So lets start easy - check you firewall setting first.  

Open Azureus and go to tools>NAT/firewall test.  You should see your port number listed - click "test" and wait for the results.  If it says "OK" then your port is open.  If it does not then the problem is the port is not open.

---

### Post by WinterWeaver on 2008-01-23
Also remember, Azureus is java, so make sure you have the Sun Java packages installed. I noticed in the past that Azureus runs MUCH better whith them installed.

However... lol... I'd recommend switching to Deluge ^_^

Since I started using Deluge, I've not been dissapointed :)

WW

---

### Post by WinterWeaver on 2008-01-23
> **cyclingman said:**
> I'll give that other software a try. For some reason, when I try installing bittorent, i can't find the program anywhere :(

Bittorrent isn't a app you run by itself. Just double click the torrent file, and bittorrent will open :)

WW

PS... soz for double post, but was too lazy to edit my previous post :P

---

### Post by cyclingman on 2008-01-23
I'll give everyone the FULL picture...

 
... I was pretty happy with Bittorrent, but I know that Azureus is better, so I unninstalled Bittorrent, and downloaded Azureus (useing Synaptic). 

But then, when I went to Applications > Internet, Bittorrent was still there, but just as a dead link. Although Synaptic said it was unninstalled. So being a stupid begginer, I went to System > Preferences > Main menu, right clicked on Bittorrent and clicked delete. 

However, Azureus didn't work for me. So despite me trying to install Bittorrent, completely removing it, then install it again. I can't find Bittorrent anywhere. I try right clicking on it under Synaptic and then showing downloaded files, but I can't seem to find the one that is the program itself. 

Is it there, but I just can't see it? Have I done something wrong in trying to download it?

P.S previous was posted while I was typing (I didn't read it first)
P.P.S The NAT test says that it's all OK
Any suggestions are more than welcome ... please ... :cry:

---

### Post by cyclingman on 2008-01-23
Just to let people know. I donwloaded Deluge - it's all I needed. :) :) :) :)

(you can still post!)

---

### Post by elect on 2008-02-14
Im getting problem with the nat, my upload doesnt work properly...

On Leo Azureus works fine, on Ubuntu no upload....any ideas?

---

### Post by stevejesus on 2008-02-14
You need to set up port-forwarding.  Also, I think Azureus is falling by the wayside.  I would try Deluge, of Ktorent, depending on what environment you use.

---

### Post by elect on 2008-02-14
Edit: it needed only time, nat is now ok :P

---

