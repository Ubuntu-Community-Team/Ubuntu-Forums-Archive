---
title: "Unable to connect to websites, multiple browsers"
date: 2016-05-02
forum: General Help
---

### Post by Franz_Ziereis on 2016-05-02
I'm writing this from FF on the XP partition of this computer.  This morning I find that I can't connect, or connection is unreliable, to various websites under my Ubuntu partition running 14.04 32bit. All Google related sites, Gmail, Youtube and search engine are inaccessible in Chrome and FF. I could sometimes connect to some websites, Yahoo, e.g., but not others.  My access to Google and other sites seems to be fine under XP.  I switched out modems, wired only connection, and - thinking that Chrome and FF might be corrupted - installed Epiphany to no avail.  I'm at a loss. Any help would be greatly appreciated.

---

### Post by TheFu on 2016-05-02
Try troubleshooting the network connectivity first.  Stuff like you've described is usually a DNS issue.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)  ... start with those steps which will determine exactly where the issue lies (or doesn't lie).  Please post the commands and output it lists.

You can put the commands and result output into files. For example:
```
$ route >> /tmp/route.out
```
I like to name all the files the same, so **cp *out /mnt/flash-drive/** works easy.
Then copy all the output files to somewhere the XP partition can see or to a flash disk or into an email (assuming email is working). Then copy/paste the output here.

---

### Post by Franz_Ziereis on 2016-05-02
Bizarre.  It's all working again.  I'm assuming it must have been my internet connection but why did I have connectivity in XP but not Ubuntu?  Could the service provider have been finicky with Ubuntu this morning but not XP?  I shutdown and restarted Ubuntu at least twice (and tried different things) and then went back to Windows where I could post.  

Thanks for posting that link.  I'll remember that in the future and run those commands if I run into the same thing.

---

### Post by TheFu on 2016-05-02
networking isn't OS-specific.  A network is a network is a network.  IP traffic is IP traffic.  They probably don't know that you use Ubuntu at all, plus you probably have a router between them and your computers.

When I've had issues like this, it was due to gophers eating the coax line to the house. It worked fine unless the ground was wet.  After about 6 months of that, the line died completely and the ISP finally came and put in a new, thicker, coax.  They didn't pull up the old line. ;(  Plus some new neighbors came with a cat.  gopher issue solved. ;)  Sadly, the other wildlife in the area was reduced too - fewer nice snakes, turtles, raccoons, etc.  BTW, I don't live in the wilderness, just the suburbs.  Still have plenty (too many?) of rabbits and squirrels.  

Why did it work in XP vs Linux?  No way to know.  Timing?  Maybe your router is about to die?

---

### Post by Franz_Ziereis on 2016-05-02
No router connected at this time and I did change modems between shutdowns.  They're two Earthlink modems and they both seem to work fine.  I got the second one years ago when EL was giving me a hassle about a slow connection being the fault of my modem.  I knew it wasn't but buying it gave me some leverage if they ever tried to pass the buck in the future.

I cut down part of a tree that was growing up in the power and phone lines just a few months ago.  After it was cut it got caught on one of its limbs and was just swinging from the phone line until I propped my ladder up on it and cut it free.  I was surprised that the line supported that tree and didn't bugger up my connection in some way.  The thing nearly took me out when I got it free of the trunk and afterwards wound up swinging from the line.  Just inches from hitting me in the face and I was on the ladder cutting it.

Thanks again.

---

