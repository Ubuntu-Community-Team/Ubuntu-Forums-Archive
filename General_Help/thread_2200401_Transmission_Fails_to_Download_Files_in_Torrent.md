---
title: "Transmission Fails to Download Files in Torrent"
date: 2014-01-19
forum: General Help
---

### Post by Bobby_McGee on 2014-01-19
Hey,

This is the first time in a while for me (I was Bobby McGee in the pre-open ID forum days). I put Ubuntu GNU/Linux 13.10 on a few days ago--dual booting with an HP win 7 laptop. 64bit, 6gigs RAM, 500GB HDD, etc.

In both Ubuntu and Wind'oh!z, I cannot get torrents to work. I.e., the files within torrents fail to download even when there are lots of seeders.

I had a MacBook Pro last week and it was stolen, but the torrents still worked. I am using Comcast Ethernet (i.e., my computer is plugged into my modem via a cord) and while I know Comcast is not a fan of net neutrality I do know that downloading large files through torrents worked on an Apple machine. So why not in Windows or GNU/Linux?

In particular I'm trying to download Ubuntu through a torrent--the daily build.

Thanks in advance! Have a good week!
bobby

---

### Post by iaskedalice09 on 2014-01-19
Just switched over to this account--I'm using this one from now on.

Still looking for an answer. Thanks in advance!

bobby

---

### Post by Ubi_one_2014 on 2014-01-19
what software do you use? transmission? qbittorrent?  other ?

---

### Post by iaskedalice09 on 2014-01-19
I'm using both deluge and the default transmission.

---

### Post by ajgreeny on 2014-01-19
I don't think you will ever have success downloading a daily build .iso file using a torrent client; I do not think there are any torrent files to use in the client to start with.  This is probably because there will never be enough seeders to make the daily build downloads worth trying.  How exactly are you attempting to do this; where did your **ubuntu-***daily-build***.iso.torrent** file that you need to run with a torrent client come from?

Once the final version (of 14.04?) is released a torrent will definitely be the best way to get it, as the servers for ubuntu will be overwhelmed at the start, just as they always are.

Is it just the daily build that will not work; what about other torrent downloads?

---

### Post by iaskedalice09 on 2014-01-19
I've tried other torrents--mostly music, for what it's worth--with absolutely NO success.

So yeah, any ideas?

---

### Post by ajgreeny on 2014-01-19
Firewall blocking the port needed for torrents?

---

### Post by iaskedalice09 on 2014-01-20
I don't think so. I didn't install or enable a firewall manually, so I doubt that's the issue.

Is there a way to confirm this? Will I have to confirm on both OSs?

Thanks!
Bobby

---

### Post by iaskedalice09 on 2014-01-20
I tested the ports, and they're open--i.e., the ones used by torrent clients.

What to do?

bobby

---

### Post by efflandt on 2014-01-20
Is your modem a modem only, or a modem/router. In other words do you get a public IP directly on eth0?

If your modem is a router (or using a router) you either need UPnP enabled on router and torrent program, or forward port 51413 to LAN IP of Linux. I have been using Transmission with port forwarding (static LAN IP) on my DSL gateway for some time, downloading and serving various Ubuntu and Raspberry Pi releases.

---

### Post by agross2 on 2014-01-20
First, sorry for the theft.  That sucks.

Second, can you try to download a torrent on a friend's computer?  It seems hard to imagine that its a settings issue if it occurs on both Ubuntu and Windows.

Have you ever downloaded torrents successfully in the past on this computer?

---

### Post by iaskedalice09 on 2014-01-20
> **efflandt said:**
> If your modem is a router (or using a router) you either need UPnP enabled on router and torrent program, or forward port 51413 to LAN IP of Linux. I have been using Transmission with port forwarding (static LAN IP) on my DSL gateway for some time, downloading and serving various Ubuntu and Raspberry Pi releases.

It's got a router. UPnP is enabled/checked in Deluge. As I have Comcast (cable), could I do the LAN IP option? How would I go about doing this?

---

### Post by iaskedalice09 on 2014-01-20
Thanks for the sympathy on the theft. I think I said before that torrents worked on my old laptop.

Unfortunately, I'm almost positive I am the only one in the complex with a laptop (read: public housing).

---

### Post by iaskedalice09 on 2014-01-22
At the risk of seeming obnoxious...bump. I really want (and need!) my Torrent client to work on this machine.

I'd install virtualbox but everytime I've done it in the past it's failed.

Thanks for any advice!
bm

---

### Post by QIII on 2014-01-22
Hello!

Comcast is also my ISP.  I just checked trying to torrent the most recent version of Bodhi Linux and it would not work.

However, I was able to torrent the Saucy image from ubuntu.com.

Try doing that, and let's see if it works.

By the way, a bump every 24 hours is not obnoxious -- we ask that people wait that long.

---

### Post by slooksterpsv on 2014-01-22
Are you using any sort of encryption on your machines such as BitLocker or filesystem encryption?

Also with the torrents, if there's anything specific you've tried downloading that has an MD5 checksum, run the checksum against the file you downloaded.

---

### Post by iaskedalice09 on 2014-01-23
As I've noted, I added the Saucy torrent (64 bit, but may do 32 bit if you think that'd work).

No files or HDD space is encrypted, so no issue there. No files downloaded at all, so the md5 check is a moot point.

---

### Post by slooksterpsv on 2014-01-23
I've heard of ISPs sending dummy data and usually (from what I've seen) torrent apps try to do an MD5 sum on it to verify that it's all downloaded and all complete and if it's not, then it deletes it. Have you tried another computer see if it behaves the same (a friends computer for example). Have you tried torrenting directly to a USB HDD or some external storage?

---

### Post by iaskedalice09 on 2014-01-23
On my old computer, it worked with no problem. It was a Mac, running Mavericks.

Here, with both Windows and Ubuntu, it does not.

Methinks it is a network problem but I can't pin down exactly where.

---

### Post by slooksterpsv on 2014-01-23
I did read that info from the previous post, but I mean can you get another computer or have someone bring theirs over to try it.

---

### Post by cybercity@localhost on 2014-01-23
post the output of sudo iptables -L.

---

### Post by iaskedalice09 on 2014-01-23
Negative.

I suppose I could try to get an Apple OS X DVD off eBay or something and make a Hackintosh machine.

I am majorly bummed by this. :-(

---

### Post by iaskedalice09 on 2014-01-23
> **cybercity@localhost said:**
> post the output of sudo iptables -L.

I was waiting for a Terminal command run request. :-) ;-)

Output is:

```


 Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


```

---

### Post by iaskedalice09 on 2014-01-23
I thought port access may be the problem, so I forwarded a wide range of ports (4300 something to mid 6000s). TCP + UDP, both. Still no luck. On Windows but I have a sinking feeling that Ubuntu would yield similar results.

I do have a video-phone (I am deaf) that works and uses a range of ports...but as I said, torrents worked on my Mac. Any ideas??

---

### Post by iaskedalice09 on 2014-01-23
Yeah, does not work on GNU/Linux either. :-( I am going to take a nap and see if this works when I walk up.

---

### Post by iaskedalice09 on 2014-01-24
thoughts on output of iptables -L?

---

### Post by iaskedalice09 on 2014-01-26
bump

---

### Post by sbnwl on 2014-01-26
Is any proxy server in your netwrork? Then you may need to first configure the system wide proxy in the network tab in settings.

---

### Post by slooksterpsv on 2014-01-26
Have we tried changing the ports for your torrent to something NOT within that block for the video phone? What about disk space, how much space do you have left on the drives?
What error do you get when it "finishes" or starts downloading torrents? If you could get us a specific error that would be good. Are you running any antivirus on Linux?

---

### Post by iaskedalice09 on 2014-01-27
Dear all,

I am thrilled to say that this is all a moot point as Transmission works! Deluge doesn't.

Thoughts:
1. set it to random ports
2. UPnP
3. forward ports


Strangely, Deluge doesn't work. Can't figure out why. There is an Errors (2) in the sidebar. I can't figure out the details and for this anyway it seems as though the devil really is in the details.

bm

---

### Post by iaskedalice09 on 2014-01-27
spoke too soon...

1. no proxy.

2. VP/ports are fine--double checked.

3. the error I get in properties is 'Connection failed', alternating with 'Failed to connect to tracker'.

How do I rectify number three?

---

### Post by PocketDog on 2014-01-27
Same for me, with Deluge. I know my way around a router, and can forward ports with my eyes closed but Deluge stubbornly refuses to connect to anyone, ever. Even left all night it won't connect. 
 If there's anyone to connect to, Transmission will connect to them. Weird.

---

### Post by iaskedalice09 on 2014-01-27
any ideas on fixing the pervasive connection issues on my end?

bm

---

### Post by iaskedalice09 on 2014-01-27
Also, it's a clean install of Ubuntu GNU/Linux and new Windows machine. so pretty empty.

thanks
bm

---

### Post by iaskedalice09 on 2014-01-28
Anyone know if transmission has daemon files that log what ports are used? Because it worked last night, and I hope that there is some log as to what port was used so I can just enter that.

---

### Post by iaskedalice09 on 2014-01-28
Installed transmission-daemon and yeah...no luck. tried the CLI version of transmission and got a similar error (could not connect to trackers).

I don't have any ideas, other than just closing and opening it again and again hoping it'll decide to work again.

---

### Post by iaskedalice09 on 2014-01-29
bump

---

### Post by iaskedalice09 on 2014-01-30
What does the output of the Terminal command mean?

bm

---

