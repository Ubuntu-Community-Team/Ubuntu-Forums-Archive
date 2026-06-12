---
title: "Malicious software installed? Possible Rootkit. Detection and Removal."
date: 2007-11-05
forum: General Help
---

### Post by arthur5005 on 2007-11-05
Ok new to ubuntu, but not a blind idiot here. Once upon a time in 1998 my friend did install slackware on my system, had my way with it, got frustrated and switched back to windows. But now I'm back in Ubuntu and loving it. I've been running it for over a year now (first Fiesty, now Gutsy of course). Know my system pretty well.

Well recently, as in a couple days ago, on my screenlets network traffic monitor, I noticed that my network traffic on the upload was a bit wack, infact way to high, although at the time I attributed it to some torrents I had running, but it was still 3 fold higher than all my uploads combined. On my network this is my only machine running in DMZ (linux.. secure.. right?) and today I started my system up, looked right into my widget layer for the weather, and noticed my upload was off the chart, but NOTHING was running.

Ok.. now I'm no networking expert, but I'm not not naive either, something's generating this traffic. So I've poked around on the net, hesitant to even be on the net, watching my upload for the session on my system monitor FLY like spikes everywhere. Closed down everything that I could my weather widget, browser, anything that I could that would do any form of networking and watched my total upload for the session hit 400 mbs in fifteen minutes. So I found some network monitoring tools, and I think i settled on Wireshark. And of course, my computers trying to make connections to IP addresses all over the internet and ip addresses to me. So I took my self off DMZ to see what kind of difference that might make. An immediate slow down in how much I was uploading, still a couple of massive spikes, but now it's leveled off to almost nothing. *phew* Almost the last time I put my self on DMZ.. ok what next well 

So I'm taking a look at these scary looking packets here, and they all look a little something like this:
1104	76.155630	124.243.157.62	192.168.2.4	UDP	Source port: 26277  Destination port: 6881
1105	76.155684	192.168.2.4	124.243.157.62	ICMP	Destination unreachable (Port unreachable)
with a WHOLE bunch of different ip address, now but wait a second.. I 'KNOW' i don't have any bittorrent clients open, why does this look like bit torrent traffic always to port 6881. Hrmm Uber suspicious and in the time it's taken me to read some more info about linux security on some other forum, even though my upload isn't going as crazy as it used to, there's still huge occasional spikes, which has driven up my upload another 100mb in about 20 minutes here.

Now I just used both rkhunter and chkrootkit, only rk hunter gave me a warning about hidden files in these directories:

[19:18:10]   Checking for hidden files and directories       [ Warning ]
[19:18:10] Warning: Hidden directory found: /etc/.java
[19:18:10] Warning: Hidden directory found: /dev/.static
[19:18:10] Warning: Hidden directory found: /dev/.udev
[19:18:11] Warning: Hidden directory found: /dev/.initramfs

otherwise netstat gave me the following:
arthur@Wintermute:~$ netstat -vat
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:nfs                   *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:sunrpc                *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:smtp          *:*                     LISTEN     
tcp        0      0 *:47739                 *:*                     LISTEN     
tcp        0      0 *:52124                 *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 *:54845                 *:*                     LISTEN     
tcp        0      0 Wintermute.local:41932  192.168.2.1:www         TIME_WAIT  
tcp        0      0 Wintermute.local:41931  192.168.2.1:www         TIME_WAIT  
tcp        0      0 Wintermute.local:41934  192.168.2.1:www         TIME_WAIT  
tcp        0      0 Wintermute.local:41938  192.168.2.1:www         TIME_WAIT  
tcp        0      0 Wintermute.local:41933  192.168.2.1:www         TIME_WAIT  
tcp        0      0 Wintermute.local:41937  192.168.2.1:www         TIME_WAIT  
tcp        0      0 Wintermute.local:41935  192.168.2.1:www         TIME_WAIT  
tcp        0      0 Wintermute.local:41936  192.168.2.1:www         TIME_WAIT  
tcp6       0      0 *:5900                  *:*                     LISTEN    

problem is I have no idea whats kosher and what's not.. isn't 5900 vino? I'm almost 100% sure I have remote desktop connections turned off. (checks) yes it's turned off.

can anyone help point me in the right direction for what I need to be doing? Just did a quick test, put my self back on DMZ to see how fast my upload'll fly.. Yup!.. Ug...

on packets it seems I get a couple of these once in a while:
1701	129.428921	192.168.2.1	224.0.0.1	IGMP	V2 Membership Query 

a couple of series of these
1501	64.470299	192.168.2.4	72.39.213.124	TCP	3602 > 29221 [RST] Seq=0 Len=0
1502	64.480190	72.39.213.124	192.168.2.4	TCP	[TCP ACKed lost segment] [TCP Previous segment lost] 29221 > 3602 [ACK] Seq=2920 Ack=1 Win=65135 Len=0
1503	64.480198	192.168.2.4	72.39.213.124	TCP	3602 > 29221 [RST] Seq=1 Len=0
(in that order from some random ip addresses)
some friendly http stuff
but the majority of these packets when I go to DMZ look like this:
1697	127.412680	77.176.225.219	192.168.2.4	UDP	Source port: 63039  Destination port: 6881
1698	127.412740	192.168.2.4	77.176.225.219	ICMP	Destination unreachable (Port unreachable)

and I just want a reliable to figure out where all my upload traffic is coming from!! what I might be able to do in face of a cracker on my machine
help plz?

Best
Arthur

---

### Post by p_quarles on 2007-11-05
Yeah, this sounds kinda bad. Up front, I can tell you that the *only* good solution for a cracked system is to disconnect it, make copies of all the log files (for further investigation) and then reinstall the OS. 

If you want, you can get a pretty comprehensive list of standard port numbers [here]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers"). That probably won't be particularly useful, though, since if you are looking at a rootkit, the bad guy can use whatever port for whatever service they want. 

To get the names and numbers of whoever is connecting to your computer, you always use the whois database:
```
whois *numeric-ip-address*
```
I would do this from a non-cracked computer, though. You really should keep the compromised system off your network at this point, until the drive is wiped. 

Anyway, a few suggestions for preventing this from happening again:
-Running an X-server in a DMZ is a pretty big risk. Just like with Windows, running a functional GUI requires some security compromises, and it's therefore much easier to find exploits. There are command line torrent clients, and those might be your safest bet.
-If you haven't done so, make sure your system is locked down at a basic level. I would suggest, installing intrusion detection software (i.e., snort), performing some system hardening (bastille is a decent package for this), and checking your logs regularly.

---

### Post by arthur5005 on 2007-11-05
I hear ya on the DMZ thing, I know the risk, never had a problem b4. In the end, this is probably what i'll do, just format the beast. I was hoping someone could shed a bit light into 'what to look for'. Any native linux tools that'll help me? (btw Bastille looks great, will install it next time around which will probably be tomorrow)

---

### Post by p_quarles on 2007-11-05
You could always take a look at the currently running processes, and seeing if there's anything you don't recognize:
```
ps -e
```
Again, though, if it's a rootkit, that won't help, because a rootkit by definition disguises itself as a process that you *do* recognize.

I've never attempted this, but I know there are some advanced forensic procedures available for determining what happened. I'm nowhere near knowledgeable enough about that to help, other than to say that you would need to make an image of the hard drive to another medium before wiping it. If you have the storage space and time, doing this would be an interesting learning experience if nothing else. 

Hope this helps. Like I said, though, the nastiness of a rootkit is the fact that it's designed to cover its tracks. The rootkit detection utilities don't really work that well unless you run them from a remote system and compare the results with a stored snapshot image of the infected drive.

---

### Post by arthur5005 on 2007-11-05
thanks again for all the info!

---

### Post by arthur5005 on 2007-11-05
Hmmm I bet I know what's going on, but I still can't imagine how it drives up that much traffic in terms of sheer volume. I'd now rethink my position and say that some bittorrent trackers still have my ip address as client to try and connect to, throws that to other client, and every client that is thrown my way sends me this
(schema) SOURCE - DESTINATION 
1104 76.155630 124.243.157.62 192.168.2.4 UDP Source port: 26277 Destination port: 6881
and I send them back this essentially saying f* off:
1105 76.155684 192.168.2.4 124.243.157.62 ICMP Destination unreachable (Port unreachable)
great and all, but the sheer volume that those requests come in (which is ALOT when I'm on DMZ) force me to send quite a bit out.. enuf to generate a couple hundred mbs in traffic though? maybe..

I found out that these requests 
1701 129.428921 192.168.2.1 224.0.0.1 IGMP V2 Membership Query  are aOK, they have something to do with Group Multicasting over a local network. 244.0.0.1 is simlpy a group Ip address, send a request to all on the network..

I'm just surpised that all those torrent requests would generate my box to flood out copious amounts of traffic. unfreal.

---

### Post by HermanAB on 2007-11-05
Hmm, looks like there is a torrent running.  It is very easy to re-install Linux - takes only about half an hour.  This time, ensure that you use long passwords for all accounts >= 9 characters.  I use 16 character semi-pronounceable passwords on my systems.

---

