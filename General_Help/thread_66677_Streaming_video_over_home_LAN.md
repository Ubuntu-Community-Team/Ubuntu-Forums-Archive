---
title: "Streaming video over home LAN?"
date: 2005-09-18
forum: General Help
---

### Post by master_b on 2005-09-18
Hi,

I've got a home LAN of 4 PCs, one of which is a file/print server.

I have stored my media files on the Server, including ogg files, mpegs and ripped DVD iso's.

I want to be able to watch the dvd's, mpegs and listen to the ogg's on any of the other 3 PCs on the LAN.

I've Googled, searched Forums etc but still haven't found out how to do this.

I have found many ways to remotely access the Server and play the various media on it, but as it is Headless this is useless.

Help/Links/Suggestions please.

Much appreciated

Bill

---

### Post by fordfan753 on 2005-09-18
There are a few different ways I can think of to do this.

1. Set up the machine with all the cool files as a samba server.
This would suck if all your PCs were Linux, because samba is a Windows file share protocol, and Windows doesn't have the best way of doing things over networks. If you have a Windows PC on the network this may be the best way.

2. Set up the machine with all the cool files as an NFS server.
This is much cooler, although NFS is known to be a bit insecure, compared to samba it's like a bomb shelter. Basically it'll let your other PCs mount a folder on the media PC as if it was just another local partition, which is cool. Be careful if you want Windows compatibility because Windows has no builtin NFS client.

There are probably a couple of other ways I don't know, which may, or may not be better, but I have set up both samba servers and NFS servers on Warty, Hoary, and Various Debian versions pretty easily.

---

### Post by master_b on 2005-09-18
Hi fordfan753

Nice to hear from a fellow Aussie. Thanks for the reply.

I've already got Samba setup and running ( do have dual boot XP and Linux) and I can access media files without problems.

Doing things this way however, causes the files to be downloaded to the Workstation from the Server ( temporarily only - they are not saved on the Workstation) and this works and allows me to play the media.

However, what I want is to be able to stream the files - ie play them on the Server but watch them on the Workstation.

Not sure if I'm making sense or even if I understand Streaming properly.

I know that viewing Video/playing Audio over the Net in a Browser requires downloading/buffering, so maybe what I'm doing is correct.

Bill

---

### Post by fordfan753 on 2005-09-18
ok, now I get what you're trying to do, and I did read somewhere that it is possible to set up streaming servers without too much difficulty, I don't remember how to do it, but I've seen it done.

Does NFS, like Samba, temporarily save the files on the client while they are in use? I might have to try that with a diskless client one day. :P

---

### Post by master_b on 2005-09-19
Hi fordfan757

>>Does NFS, like Samba, temporarily save the files on the client while they are in >>use? I might have to try that with a diskless client one day. :P

I've no idea, not having tried NFS, but I think that it would have to.

One solution to my "problem" would appear to be mythtv - haven't tried it yet though did try an install of Knopmyth some time ago without success as it didn't like my HDTV DVB-T card, though I now have a 2nd card - Avermedia DVB-T 771 which works fine under Kanotix 2005.3 Lite.


MythTV should be  what you need for video on a diskless client I guess.

Oh well, guess I'll try downloading and installing mythtv onto my server (Mepis SOHO beta).

Stay tuned!

Bill

---

### Post by maxdevis on 2006-03-12
i found out, for me, streaming audio is the easiest with edna.
but what with video?

---

