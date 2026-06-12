---
title: "Slow Network Performance"
date: 2007-01-08
forum: General Help
---

### Post by statictonic on 2007-01-08
I transfer files between this computer and a linux file server running samba a lot.  Now when I'm in windows on this computer, I get about 70-75% usage of a 100mbit connection, so 7-.75MB/sec, pretty decent.  However in linux I get about 30% usage tops, about 3MB/sec.  I'm currently use the onboard nForce 2 network controller for my connection.

Another possibly related issue is, I've mounted some shared samba directories on linux, when I play video from the mounted samba directory, the video often stutters, amarok often stops playing a song for about 30 seconds in the middle of a song, then starts back up playing.  Neither problems occur when a windows machine accesses the samba share.

Any ideas on what the problem might be?

---

### Post by statictonic on 2007-01-08
Well i tried transferring a file using apache on the server and downloading via http, got about 80% network usage, so it's just samba causing the problem...

---

### Post by nix4me on 2007-01-08
Yes.  Samba is notorious for having speed issues.

Use NFS for transferring from linux to linux, its much faster.  You can share the same files/folder with both Samba and NFS.

nix4me

---

### Post by dcstar on 2007-01-09
> **nix4me said:**
> Yes.  Samba is notorious for having speed issues.

Use NFS for transferring from linux to linux, its much faster.  You can share the same files/folder with both Samba and NFS.

nix4me

Do a search on using CIFS with Samba.

---

### Post by Kaladar on 2007-01-12
What if the slowness is getting files from Linux --> Windows?

The two computers are on a 10/100 LAN.
I dropped over 1000 mp3s from my Windows box to my Linux box in no time (less than 10 minutes). Now, if I want to move even ONE file (7mb) back to the Windows machine, it estimates over 4 minutes.

Any suggestions?

---

### Post by tribble222 on 2007-01-14
> **Kaladar said:**
> What if the slowness is getting files from Linux --> Windows?

The two computers are on a 10/100 LAN.
I dropped over 1000 mp3s from my Windows box to my Linux box in no time (less than 10 minutes). Now, if I want to move even ONE file (7mb) back to the Windows machine, it estimates over 4 minutes.

Any suggestions?

I ran into this problem recently.  I found a post here that completely solved my problem [http://www.vmware.com/community/thread.jspa?threadID=34497&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=34497&tstart=0)

> Problem is caused by TCP Segment OffLoading of the intel e1000 network card I'm using (although the problem occurs in other 1gig or 10gb cards). Even though the information I found suggests the relevant bugs were fixed in kernel 2.6.12 (I'm using 2.6.15.4) I got instant results turning it off. 

The other thing I had problems with is HOW turn it off inlinux. Windows is quite easy look under advanced network properties ofthe card, its called 'large send' and set to none.

Linux download a useful tool called 'ethtool' and run 'ethtool-K eth0 tso off' where eth0 is whatever network interface u are using.

Doing this will (or should) reduce your network throughput although will greatly increase stablility.  
My tests actually show this has improved throughput by 10% on my system ....

Now I get full speed both ways

---

### Post by Kaladar on 2007-01-16
That function is not available to me (it seems like a function of Gigabit ethernet nics). I was using a Netgear Fast Ethernet card (using the natsemi module) and even tried switching to a Belkin card (RealTek module 8139), but that didn't help either. Both cards showed they were using full duplex and were in 100Mb mode.

I used jnettop to check speeds from each box to the other, and my MS box sends to the Ubuntu box at about 7.2 m/s while the reverse is only around 50-70 k/s.

If I use HTTP (ssh via WinSCP), the speed goes between 160-220 k/s.

I'm still convinced its a setting somewhere, but I'm just not sure which one/where. Could this be a Samba setting? Its send and receive size are set at 8192.

Any other suggestions?

---

### Post by Kaladar on 2007-01-18
Solved my particular issue. The Marvell 10/100/1000 NIC has a 'media type' setting of 'AutoSense' on the Windows machine. It had been set at 100 Full Duplex. After changing it, the speed immediately increased to the same rate both ways.

---

