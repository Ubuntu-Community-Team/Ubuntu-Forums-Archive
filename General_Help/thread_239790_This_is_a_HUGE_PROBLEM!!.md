---
title: "This is a HUGE PROBLEM!!"
date: 2006-08-19
forum: General Help
---

### Post by simoncoul on 2006-08-19
I am fairly new to linux, but the last couple days I've tried to download numerous torrents and have not reached a speed faster then 20kB/s.   I have the proper ports forwarded on my router and there are lots of seeds(60+) and peers(1200+) for the torrent.   I tired the excact torrent on my windows machine and got 500kB/s.   

I have looked through the forums and many people have had this problem and people give the same advice to forward ports, make sure enough peers, and forward ports on firestarter.   I don't have firestarter and the other things are done.   

So what is the problem here, the torrent client will not connect to very many peers though only like 50 and zero seeds.   I have tired azureus, ktorrent, bittorrent, bittorano and utorrent with wine, and they all had the same results.   Does ubuntu have a internal firewall that may need forwarding.   I can download other things just fine, from repos and from websites.

Any help you could offer would be great

Thank you!

---

### Post by The Noble on 2006-08-19
Uh, lets see. You have a few things that you can try:

--Make sure you aren't uploading to fast or you will choke your download speed. I am guessing you have done this already.

--Try adding some more trackers to the torrent.

--IPtables is the built-in firewall in the Linux kernel. Firestarter is the frontend for it, so opposed to windows where you have to add a firewall, Linux has it built-in. I don't know if it is active all of the time, however, so maybe someone else can help you there.

--Basically every torrent program in linux has at least one major problem (except maybe ktorrent, but it still isn't up to par), so I guess using windows still has some big pluses. :P

---

### Post by kaptainlange on 2006-08-20
I've had nothing but success with Azureus, and the few times I've used the torrent client that came with the install it worked flawlessly.  I don't think this is a Linux specific problem.

Some ISP's are beginning to filter specific types of traffic, ie torrents.  Double check to make sure that is not the case.  If it is be sure to let your ISP know how disatisfied you are with their service.  They could also be limiting the port you're using, try a different port.

Some settings to look out for:

The maximum number of connections your program can open to download.  Too many connections can create a heavy load on any network you are on.  

Upload rate, I generally limit my upload to 1/3 of what I'm capable of fully.  Make sure the download rate isn't capped as well.

Double check you forwarded the right ports.

There are all sorts of reasons you could be having slow downloads, more information on your network setup might help pindown the problem.

---

### Post by peabody on 2006-08-20
> **simoncoul said:**
> I am fairly new to linux, but the last couple days I've tried to download numerous torrents and have not reached a speed faster then 20kB/s.   I have the proper ports forwarded on my router and there are lots of seeds(60+) and peers(1200+) for the torrent.   I tired the excact torrent on my windows machine and got 500kB/s.   

I have looked through the forums and many people have had this problem and people give the same advice to forward ports, make sure enough peers, and forward ports on firestarter.   I don't have firestarter and the other things are done.

So what is the problem here, the torrent client will not connect to very many peers though only like 50 and zero seeds.   I have tired azureus, ktorrent, bittorrent, bittorano and utorrent with wine, and they all had the same results.   Does ubuntu have a internal firewall that may need forwarding.   I can download other things just fine, from repos and from websites.

Any help you could offer would be great

Thank you!

Hmm, never goes above 20 kB/s?  Or stays around 20 kB/s?  I have to confess that I have never had this problem with torrents on Ubuntu.  I download frequently at 500 kB/s using the default client.

I have a theory.  The nofiles ulimit in Ubuntu seems to be set to 1024.  This limit is for how many files you can open simultaneously.  This limit effects network connctions, so you basically can't have more than 1024 open network connections.  This can be adjusted manually in the /etc/security/limits.conf file.

I'm not sure what the limit in Windows is.  I was under the impression that it was actually less than this?

There are two problems with this theory, one is that 1024 is an awful lot of network connections and I'd be surprised if that wasn't enough (it seems to be plenty enough for me).  However, if you're running many torrents simultaneously from within the same client it could be a problem.  The other problem is that I would think that the bittorrent clients would (or rather "should") be spewing error messages if they weren't able to create another network connection.

So if that doesn't seem to be the problem: what is your network card?  Were you using any kind of "optimizations" of the network settings in Windows?  If so, what were they?  What is the load on your system (CPU, memory etc.) during the torrent download?  Have you tried port scanning your machine from the outside world to make sure the port was open?  What port are you using?  What client were you using on Windows to get that speed?  Did you test each of the clients (Linux vs Windows) around the same time or at least very close to each other?  If you tested them simultaneously did you make sure to rate limit each one (the Windows client could have been gobbling all of the badwidth if it was started first).  Are you doing any kind of bandwidth shaping on your router?

Lots of questions I know, but that information will help tremendously in trouble shooting the problem.

---

### Post by Tomosaur on 2006-08-20
I would expect this problem to be related to your ISP rather than Ubuntu. Some bittorrent clients have the option to encrypt the traffic, which should stop your ISP from throttling your download speeds. Try that and see if it works.

---

### Post by dasunst3r on 2006-08-20
Before I go on BitTorrent, I do these things:
1. Open port 6881 (or some other port) in my iptables firewall
2. Get the router to forward traffic from port 6881 to me
3. Restrict the upload speed to 3/4 of what my DSL line is capable of

There are instances when the ISP would restrict traffic in certain ports (see here: [http://www.azureuswiki.com/index.php/PortIsBlacklisted](http://www.azureuswiki.com/index.php/PortIsBlacklisted)).  Therefore, encrypt traffic and use a non-standard port.

---

### Post by jimmygoon on 2006-08-20
You all need to check your Azureus ports... It doesn't use the conventional ports... It uses some random one that it selects...

---

### Post by simoncoul on 2006-08-20
Alrite I installed firestarter and forwarded the ports, I don't believe that changed anything though.   I also did a firmware update to my router, which has horrible support for linux I might add.   

It had the same internal ip as the windows machine(I dual boot) but the router would not recongize it when I was running linux.   It said the ports were still forwarded for the internal IP address, but in the status log it said that it kept blocking incoming connects for it.   

I think I should probably get a new router.   Anyone could suggest a good wireless one that works well with linux??

Thanks for the help

---

### Post by peabody on 2006-08-20
> **simoncoul said:**
> 
It had the same internal ip as the windows machine(I dual boot) but the router would not recongize it when I was running linux.   It said the ports were still forwarded for the internal IP address, but in the status log it said that it kept blocking incoming connects for it.   


What do you mean by "would not recognize it"?  Can you post a screenshot of what you mean?  What is the brand of the router?  Are you saying you couldn't get an IP address from the router via DHCP?  Did you statically assign?  I've never heard of a router (out-of-the-box anyway) discriminating its port forwarding via operating system fingerprinting.  I highly doubt that's what's going on here, don't buy new router just yet.

Your ISP, on other hand, could be doing something like bandwidth shaping based on OS finger printing.  In which case, a new router is not going to do you any good.  There are ways to defeat OS finger printing in Linux.

---

### Post by simoncoul on 2006-08-21
Like I would forward the port on windows and I'd test to see if it was open, and it was.  Then on linux I tested the same port and it said it was closed, but I checked the ids of the valid computers allowed on the router and this machine was on there, but then when I tired to make changes it wouldn't allow me because it was not a valid computer.

   I really have no idea, but I have an old SMC router which is really bad, so I think it would be a good idea anyway to upgrade it.   I called the ISP people and they said the OS does not make a difference, and like I said I can download just fine from websites.

So I think a new router is what I should try.  This one is seriously like 5 or 6 years old lol, it's time to retire!

Thanks

---

### Post by peabody on 2006-08-21
Suite yourself, however, I'd be nice to try and resolve the issue while using your current router.  What I'm afraid of is that you'll go buy a new router and still experience the same problem.

---

### Post by 3rdalbum on 2006-08-21
I have a tiny little theory: Beagle could be trying to index the file as it's downloading, causing heavy I/O usage and thus limiting your speed.

Try running this command:

```
killall beagled beagled-helper
```

Then running Bittorrent.

---

### Post by simoncoul on 2006-08-21
I am not currently using beagle, and I have fairly good computer hardware as I just made this computer a year ago.   I'm pretty sure that it is a problem with the router they discontinued service on it two years ago, so I didn't get any help when I called them.  

You said that there are ways to get around OS finger printing could you offer some sujestions?

Thank you again

---

### Post by peabody on 2006-08-21
> **simoncoul said:**
> 
You said that there are ways to get around OS finger printing could you offer some sujestions?


That was under the assumption that your ISP might have been doing something to that effect.  Apparently they weren't.  Like I said before, if your router is OS fingerprinting and shaping your bandwidth out-of-the-box it will be the first time that I have ever seen such a thing.

That said there is an article over at insecure.org that talked about it.  Something about loading a kernel module that changes how the kernel sends packets to fool fingerprinting.  Let me see if I can dig it up.

---

### Post by simoncoul on 2006-08-21
I did it!

I reinstalled the fireware update and restarted the router, and now I'm getting around 350kB/s using torrents.   I believe that was the problem.

Thanks for all the help!

---

