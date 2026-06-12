---
title: "Firefox is selective about which sites to load"
date: 2007-10-21
forum: General Help
---

### Post by Matticus on 2007-10-21
First of all I dont know if this is in the right place, but im sure if its wildly wrong it will be moved.

2 days ago, I booted up my laptop running ubuntu 7.10 (dual boot with xp), and I try to load google, and it doesnt, it takes ages to do anything, then eventually says the connection has timed out/taking too long to respond or whatever the exact words.

So I went on my main PC running xp and tried google, that worked just fine, tried my downstairs PC also xp, works just fine, so I assumed it was ubuntu not the net, but just to be sure I rebooted the modem and the router. Still no joy.

Also it will "half load" gnome-look, ie the logo and some of the nav bar loads but it hangs there forever, same with tv-guide.co.uk (gotta know whats on tv).

So I tried to first of all reinstall firefox through the package manager, didnt work, I completely removed and reinstalled didnt work, I dont think the actual complete removal worked either as when I loaded up firefox again my bookmarks where all still there :confused:

Also I installed epiphany web browser to check, and that will load gnome-look fine, but not google or these very forums.

I read on other threads about /etc/dhcp3/dhclient.conf and editing it to add in my isps dns. And checking /etc/resolv.conf to make sure the dns is right, well /etc/resolv.conf the dns was fine, and I editing and decommented the dns line on /etc/dhcp3/dhclient.conf

So anyone got any ideas short of a complete reinstall, oh btw im using wicd for my wireless incase it matters, the internet was fine and rock solid untill this point.

---

### Post by Matticus on 2007-10-21
OK hilarious solve here.

For some reason moblock had decided to start blocking google, and just randomly blocking things, I had set it up before I upgraded to gutsy, and it must have updated itself with it and changed all the config, but I dont know why it took a week or however long to do it.

Ah well, my fault being stupid and not realising it, my girlfriend who knows nothing about pcs said to me "Are you sure there isnt something on there blocking it?" and I gave her the whole "I think I would know if there was lark" boy is my face red!:oops:

---

### Post by NilsE on 2007-10-21
Your the second person today to have the problem with moblock blocking search engines.  Must be something going on with auto updates or something in moblock.

---

### Post by Darganot on 2007-10-21
I have the same problem

Using firefox, pages take forever to load, especially when it (for some reason) connects to [www.google-analytics.com](www.google-analytics.com) (it does so for ubuntuforums.org for instance).  When I disable moblock:

> $ sudo moblock-control stop

All problems go away and pages load fine.  I can't give up moblock, I do a lot of p2p  :).  It didn't do this before, about 3 months ago the last time I used moblock (was using ktorrent in between)

When I check the tail end of the log, it looks like this:

> 
$ tail /var/log/moblock.log
Blocked OUT: Google Inc,hits: 14,DST: 64.233.165.104
Blocked OUT: Google Inc,hits: 15,DST: 64.233.165.104
Blocked OUT: Google Inc,hits: 16,DST: 64.233.165.104
Blocked OUT: AltaVista Company,hits: 19,DST: 209.73.188.78
Blocked OUT: AltaVista Company,hits: 20,DST: 209.73.188.78
Blocked OUT: AltaVista Company,hits: 21,DST: 209.73.188.78
Blocked OUT: Google Inc,hits: 17,DST: 64.233.165.104
Blocked OUT: Google Inc,hits: 18,DST: 64.233.165.104
Blocked OUT: Google Inc,hits: 19,DST: 64.233.165.104

Odd, no?  I've even seen digg ip's on the list.  I can post more output if anyone wants.  I believe the solution is to edit the moblock config file and whitelist said ip's.  If I get it fixed I will try to check back.

If anyone has an easier solution, it would be much appreciated.

---

### Post by bedake on 2007-10-22
How would one go about white listing the IPs?

---

### Post by Matticus on 2007-10-22
to white list you need to sudo gedit /etc/moblock/moblock.conf

and on the whitelist IP section you can spend the rest of your life adding IPs you dont want to block.

theres that or you can go to /etc/moblock/blocklists.list and comment out some of the preloaded blocklists,

go to /var/spool/moblock/ and check out the IPs on each list, you can also remove specific IPs from theses lists too.

hope that helps

EDIT: I think a moblock configuration thread should be made sticky if more and more people keep having problems with it and we get a good fix. Atleast for a month or so while everyone gets it sorted.

---

### Post by Darganot on 2007-10-23
The answer to your moblock questions is in this thread:

[http://ubuntuforums.org/showthread.php?t=192559](http://ubuntuforums.org/showthread.php?t=192559)

The answer to OUR problem is to edit the moblock.conf file and uncomment the line that whitelists port 80 (duh!).  After this sites load fine.  I felt rather foolish after learning this...

---

