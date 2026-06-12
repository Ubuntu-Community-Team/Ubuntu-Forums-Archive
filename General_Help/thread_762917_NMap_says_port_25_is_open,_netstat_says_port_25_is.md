---
title: "NMap says port 25 is open, netstat says port 25 is closed"
date: 2008-04-22
forum: General Help
---

### Post by tallman23 on 2008-04-22
[FONT="Arial"]Hello,
First, I have read this post [http://ubuntuforums.org/showthread.php?t=237820](http://ubuntuforums.org/showthread.php?t=237820)
But I have some different points to brainstorm on.

I ran an nmap scan against my local machine (Win XP)(sorry I test lots of operating systems) from an Ubuntu Gutsy Gibbon virtual machine (VM) today. 

The results came back that port 25 was open along with port 902 (associated with VMWare). This was not expected as usually a verbose nmap scan of my machine returns little or no results. I run nmap every few days and this was the first this appeared. Running netstat -a on my host did not show Port 25 was open or that I had a socket connection on that port. I was able to telnet from the Ubuntu VM to port 25 on my local machine. After establishing a Telnet connection, i typed the helo command. About 10 seconds later, it times out and says "Connection closed by foreign host." 

A friend suggested a rootkit, so I ran rootkit revealer from sysinternals, nothing materialized there. I also ran TCPView to get a handle on the running processes; however, nothing was out of the ordinary (no rogue processes, no rogue outbound connections). Also, I used Wireshark to sniff the wire as I executed the telnet connection, and no packets went across the wire. Weird! 

Does this make sense why an nmap scan from a Linux VM would show port 25 was open and netstat on the host shows no connection? [/FONT]

---

### Post by HermanAB on 2008-04-22
The best way to check if there is a listener, is with telnet:
$ telnet localhost 25

If nothing answers then there is nothing to worry about.

---

### Post by tallman23 on 2008-04-23
> **HermanAB said:**
> The best way to check if there is a listener, is with telnet:
$ telnet localhost 25

If nothing answers then there is nothing to worry about.

I tried this and was unable to get a socket connection.

However, from a security perspective, I'm not convinced the port is closed. Why would nmap say the port is open? A friend said that netstat could be trojaned ... and the rootkit revealer does not work on a cloaked root kit.

So how do you get accurate results?

---

### Post by tallman23 on 2008-04-24
I've been doing some additional testing. 

I was able to sniff the traffic of the telnet session form the Ubuntu VM to my localhost (I had the wrong interface set to sniff in Wireshark - groan!). 

I saw the three-way handshake establishing the telnet session at port 25, yet upon issuing the "helo" command, my localhost returned a packet with the RST flag set and the connection was dropped.

Then something dawned on me: 

My first question: +*Does anyone know of worms or viruses that are able to bypass virtual machines to infect a localhost?*+

About two weeks ago, I was testing the behavior of the agobot worm within a Windows XP virtual machine with no service packs or patches applied. While running the worm, I also sniffed the wire and noticed a lot of traffic directed at my localhost. I sit behind an IPCop box and neither IPCop or my SW anti-virus or SW firewall picked anything up. Additionally, agobot is rather old and any current AV utility should evaporate it immediately. Nevertheless, I checked the registry and system32 folder (with hidden files enabled) of my localhost and did not find anything abnormal. 

Was agobot able to penetrate the VM to get to my localhost and open port 25?

---

