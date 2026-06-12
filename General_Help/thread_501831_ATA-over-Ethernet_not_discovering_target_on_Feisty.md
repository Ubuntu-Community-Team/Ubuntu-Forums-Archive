---
title: "ATA-over-Ethernet not discovering target on Feisty Fawn..."
date: 2007-07-15
forum: General Help
---

### Post by JohnnySkidmark on 2007-07-15
Hi.  This is my first post here.  This site has been very helpful in the few months since I've started using Ubuntu (and Linux as a whole), so hopefully it's a good place to start with the problem I'm currently having.  (By the way, I wasn't sure if this would be better posted in the "Networking & Wireless" forum, so please move this thread to whichever forum is the most appropriate.)

I have a server at home whose responsibilities I've tried to keep to a minimum: running VMware Server, NTP, and LVM2 (on top of Linux software RAID).  Any functionality beyond those three items is handled by guests.  One such guest is my file server, and both it and the host are running the AMD64 edition of Ubuntu Server 7.04, kernel version 2.6.20-16-server.  Since I'm not crazy about the idea of storing many, many gigabytes of large files in virtual disks, all of my data is stored in logical volumes on the host which the guest is able to access through iSCSI and then share with the network through Samba.  While this setup does work, I've noticed that the performance of these iSCSI volumes (both when accessed through Samba and when just doing benchmarks on the guest itself) is absolutely abysmal.  I knew going into it that iSCSI has a reputation of being very processor-intensive, but I guess I just didn't expect less than 5 MB/s with 100% processor usage on a 1.9 GHz Athlon64 X2 3600+ to be par for the course.  Compare that to 60+ MB/s when accessing the same logical volume directly from the host.  Having read up on ATA-over-Ethernet (AoE), that sounds much more appropriate for what I want to do (and much more processor-friendly), so I'd like to use that in place of iSCSI.

The problem is...well, I don't know what the problem is.  I used Aptitude to install *vblade* on the host and *aoetools* on the guest.  I ran the following command on the host to create a "target" on VMware's host-only network connection using a test logical volume as the device:
```
# vblade 1 1 vmnet1 /dev/MirrorVolume1/AOETest
```
Then on the guest I ran the following (*eth1* is the other end of the host-only connection):
```
# aoe-interfaces eth1
# aoe-discover
# aoe-stat
```
Apparently, *aoe-stat* is supposed to display whatever end points were discovered, but for me it doesn't do anything.  One of those commands is also supposed to create device nodes in */dev/etherd/*, but that doesn't happen, either.  Oddly, though, if I try to "ping" the target then here's what I get:
```
# aoeping -v 1 1 eth1
tag: 80000000
eth: eth1
shelf: 1
slot: 1
config query response:
00 0c 29 36 ea 56 00 50 56 c0 00 01 88 a2 18 00
00 01 01 01 00 00 00 00 00 20 40 0b 00 10 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00
found e1.1 with mac 005056c00001
```
That's the correct MAC address for the host's end of the host-only connection, so clearly it's able to "see" the target but for some reason is not "discovering" it.  I also tried doing a manual install of the package from [Coraid's site](http://www.coraid.com/support/linux/) (which looks like it's a few versions newer than the one in Aptitude) but got the exact same result.  All that *dmesg* tells me on the guest is:
```
aoe: AoE v32 initialised.
aoe: e1.1: setting 1024 byte data frames on eth1
```
*dmesg* on the host doesn't seem to contain anything relevant.

Like I said, I have no idea what the problem is because I'm not getting any kind of diagnostic or error messages.  So, has anyone been able to get AoE to work on Ubuntu and, if so, how did you do it?  [Here](https://help.ubuntu.com/community/ATAOverEthernet)'s one of the tutorials I've been looking at.  I've tried following that exactly several times and, unlike that document, I just don't get any output when I run *aoe-stat*.  I've also tried what they did and used a file instead of a logical volume as the target and it didn't make a difference.  I would also point out that */etc/default/aoetools* (part of the *aoetools* package in Aptitude) sets some INTERFACES variable to "none", which, in turn, causes */etc/init.d/aoetools start* to always fail, but if I change it to "" or "eth1" it still doesn't start up.  Is it safe to assume that daemon must be running for all of this to work?  Any idea what the difference is between my setup and that tutorial I referenced?  Is it because I'm using Feisty Fawn?  Or x64?  Or VMware?

Thanks for the help.

---

### Post by kidders on 2007-07-16
Hi there,

I use software-implemented AoE quite a bit, with a variety of distros; I can't say I've ever had any kind of trouble with Ubuntu. I could be *waaaay* off base, but it strikes me that, under the hood, a fair amount of routing normally goes on when you connect a virtual OS to a "real" network.

One of the things that makes AoE so attractive is its amazingly low overhead ... it's implemented right on top of Ethernet. The trouble, of course, is that this essentially makes it unroutable, since there are no IP (let alone TCP, etc.) wrappers.

My advice would be *not* to try using AoE unless what you're running it on is more like a SAN than a LAN. For things to perform properly, you need an isolated, router-free, highly burstable network segment, so your blades can chatter away, without having to contend for bandwidth.

Do you suppose I'm on the right track?

---

### Post by JohnnySkidmark on 2007-07-17
Thanks for replying.  While I do think you're on *a* right track, I also think that your track and my track are totally skew tracks.

The way I have my virtual machines set up is that each one has two virtual network adapters; one is a "bridged" connection that gives the guest access to my physical network using its own IP address, the other is a "host-only" connection which is basically a network that provides a direct connection between the host and any guests that I add to it.  This second, host-only connection is something I've added just recently in an (unsuccessful) attempt at boosting iSCSI performance, and it serves the purpose of being an "isolated, router-free, highly burstable network segment, so your [end points] can chatter away, without having to contend for bandwidth".  So, it's just a private network for the host and its guests, with the difference that it's effectively a *virtual* network; there are no actual switches or network cables, everything is taking place inside of this server machine.

Aside from that, it should be the same as if I'd had these machines all plugged into the same switch or hub.  And I can confirm that it works as such because, as I showed above, the *aoeping* command seems to be able to see the other side of the connection and return a positive result.  The issue is just why *aoe-discover* doesn't appear to do likewise.  Maybe VMware isn't correctly emulating some low-level aspect of Ethernet, or maybe it's something else completely unrelated to virtualization.  I don't know.

Now, if I understand you, you said you've gotten AoE to work with Ubuntu?  What version (Edgy Eft, Feisty Fawn, etc.), platform (x86 or x64), and install type (packaged or manual) are you using?  Does [the tutorial I'm using](https://help.ubuntu.com/community/ATAOverEthernet) seem to be correct?  What steps did you take to get AoE working?  Any helpful hints or things I may be missing?

I'd also add that I *would* try getting this to work first on physical machines before trying it on virtual machines, but, unlike with iSCSI, I've not found a free initiator for AoE to use with Windows, and the only machine I have that's running Linux is the same one that's hosting these virtual machines and providing the AoE end point.  I did try having that machine initiate an AoE connection with itself, but it didn't work and I'm not all that surprised; I don't think it works the same as, say, 127.0.0.1 does with IP.

---

### Post by kidders on 2007-07-17
Hey again,

> **JohnnySkidmark said:**
> Now, if I understand you, you said you've gotten AoE to work with Ubuntu?That's true. At one time or another, it's been running for me on Dapper and Edgy, along with various Gentoo installs, in 32-bit and 64-bit environments. I can't recall whether I've tried it with Feisty. The HOWTO you're following is very basic, but seems to describe everything that needs to be done. I can't think of anything that might be worth adding to it.

The unknown (at least for me) in your case is the virtualisation, which is what prompted me to point my finger at it. Before ever having seen your post, if someone had asked me whether I thought AoE would cooperate with a virtual machine, I'd have thought about it for a moment, and said "Hmm... probably not". I'd consider it about as likely as getting it to work over a VPN, to be honest! Just for the heck of it, I might try it later though hehe.

---

### Post by JohnnySkidmark on 2007-07-18
Bah.  I was hoping [this](https://bugs.launchpad.net/ubuntu/+source/aoetools/+bug/106348) might be the cause of the problem, but I installed that package and am still getting the same results.

When you've installed *aoetools*, did you do so from a package manager or compile it yourself?  Did you have to fiddle around with */etc/init.d/aoetools* at all?  Did you have to run *aoe-mkdevs /dev/etherd*, or were the device entries created automatically by *aoe-discover*/*aoe-stat*?

---

### Post by kidders on 2007-07-18
> **JohnnySkidmark said:**
> I was hoping [this]("https://bugs.launchpad.net/ubuntu/+source/aoetools/+bug/106348") might be the cause of the problemThat's an interesting dependency gap!

Normally, I don't have to do any fiddling around. It all seems to "just work" ... but I've never tried to manipulate AoE into doing anything odd. I don't recall ever having to manually create /dev nodes, but that doesn't mean I have *never* done it. On modern Linux systems though, these sorts of things should really be taken care of by udev.

Particularly on binary distros like Ubuntu, I don't generally like to make modifications to places like /etc/init.d, because of the impact doing so can have on future system updates. Similarly, I would be extremely resistant to compiling something like aoetools myself, in Ubuntu. I've only ever done so with Gentoo.

---

### Post by JohnnySkidmark on 2007-07-18
> **kidders said:**
> I would be extremely resistant to compiling something like aoetools myself, in Ubuntu.

Funny that you mention that, because I just got done trying to compile the latest AoE driver and tools from [Coraid's site](http://www.coraid.com/support/linux/index.html) (the .tar.gz file at the top of the page).  It actually was looking promising for a while there, but ultimately I got the same result.  And a kernel panic.  So much for that idea.

I think I'll ask on the VMware forums if anyone has actually been successful getting AoE to work on virtual machines, because I've yet to confirm if that's even possible.  I still haven't even determined if the problem lies with the target, the initiator, or VMware (though I've been kind of assuming the problem is on the initiator side).  I sure do wish these AoE tools would be nice enough to at least output some meaningful diagnostic/debugging information...

---

### Post by kidders on 2007-07-18
> **JohnnySkidmark said:**
> I sure do wish these AoE tools would be nice enough to at least output some meaningful diagnostic/debugging information...So do I. :-( Have you tried doing some packet sniffing? You should be able to establish pretty quickly whether AoE packets are even making it to their intended destinations (which I suspect they're not), and/or which end of your connection isn't working the way it should be.

In your pursuit of a solution to this vmware problem though, do bear in mind that even if you *do* manage to get vmware+aoe to cooperate, you still won't have a viable long-term storage solution. It would be utterly insane to run most normal applications of AoE (ie the storage of large volumes of highly critical data) in a virtualised (or partly virtualised) environment.

In general terms, it's also worth mentioning that you should be extremely careful when compiling or installing anything not provided through the Ubuntu software repositories. The software in them has all been carefully vetted & patched to interoperate properly. Certainly, _absolutely_ nothing outside of the official repositories belongs on the kind of box that would typically be running a distributed data storage system. The stakes are simply to high to be inviting things like kernel panics.

---

### Post by JohnnySkidmark on 2007-07-18
> **kidders said:**
> Have you tried doing some packet sniffing? You should be able to establish pretty quickly whether AoE packets are even making it to their intended destinations (which I suspect they're not), and/or which end of your connection isn't working the way it should be.

I did actually try running *tshark* on the AoE target.  I couldn't decipher the content of the packets, but I'm pretty confident I confirmed that packets sent out by the *aoe-discover* command were making their way to the target.  I didn't try running it on the initiator end, though, to confirm that the response made its way back, so maybe that'll be something to try.  I do know that the *aoeping* command gets a positive response, so I don't know why the discovery wouldn't; then again, I don't know why this whole setup isn't working, either, so I guess anything's possible.

> **kidders said:**
> In your pursuit of a solution to this vmware problem though, do bear in mind that even if you *do* manage to get vmware+aoe to cooperate, you still won't have a viable long-term storage solution. It would be utterly insane to run most normal applications of AoE (ie the storage of large volumes of highly critical data) in a virtualised (or partly virtualised) environment.

Well, this is for a home file server, so traffic comes in infrequent bursts, the data isn't *that* critical (I suppose), and the only way I'm going to have multiple servers is if they're virtualized.  I'm currently using iSCSI to make this all work, but, if possible, I'd like to use AoE in its place to get the same result with a lot less processor usage.

> **kidders said:**
> In general terms, it's also worth mentioning that you should be extremely careful when compiling or installing anything not provided through the Ubuntu software repositories. The software in them has all been carefully vetted & patched to interoperate properly. Certainly, _absolutely_ nothing outside of the official repositories belongs on the kind of box that would typically be running a distributed data storage system. The stakes are simply to high to be inviting things like kernel panics.

True, but this is VMware, which gives me a nice, easily-reversible sandbox to play in.  Also, the source code I was compiling came from the company actually responsible for the AoE drivers, and was many versions newer than what's in the Ubuntu repositories (barely a week old, while I think the ones in Aptitude are from last fall).  Not like that automatically makes it better, but at this point I guess I'll try anything, and I wouldn't doubt that some teeny, tiny bug fix might be all I need to get this working.

---

### Post by JohnnySkidmark on 2007-07-26
Hmmm, I was just about to make a post on the VMware forums, when I came across [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/75179).  Sounds like the exact problem I'm having.  That's from last year, though, so I wonder why it didn't come up in my searches before.

---

