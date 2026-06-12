---
title: "LTSP client for Windows/Linux"
date: 2006-11-02
forum: General Help
---

### Post by Jabran Asghar on 2006-11-02
Hi,

I just setup LTSP based on Dapper. Diskless clients boot fine using LAN boot.

Just wondering if there is a client  to start LTSP client login from with in a running operating system (Linux primarilly, windows optionally)? (Similar to RDP client for Windows Terminal Sertver).

I already tested the idea of using a VMWare machine with no disks etc. and used it to boot over LAN. That works, but its not really a solution that I will want to use as it requires a good chunk of resources for running VM itself on the client.

Further, is it possible to somehow connect to LTSP (as a client) over the internet? i.e. enabling multiples offsite users to use LTSP over the internet for their work.

(As you may have guessed, I am trying to findout a way to completely replace Windows Terminal Server with LTSP.)

Will appreciate any thoughts.

Thanks.

Jabran

---

### Post by jimcooncat on 2007-01-04
It's nothing to do with LTSP, but you can get to the server with vnc/ssh, or nx (freenx, nomachine, thinstation).

I use vnc/ssh over a consumer DSL and found it's adequate. 

Within the LAN, you can also connect with ssh (or PuTTy) and set the DISPLAY variable to your "client" computer. You'd need to have an X display on that (xming for windows works well for me). That's insecure, but OK if you're on a trusted LAN. You can limit the X display to accept stuff only from your server.

---

### Post by jimcooncat on 2007-01-05
For more info on that last part, see my post here:
[http://www.ubuntuforums.org/showpost.php?p=410657&postcount=3](http://www.ubuntuforums.org/showpost.php?p=410657&postcount=3)

---

### Post by Jabran Asghar on 2007-02-27
> **jimcooncat said:**
> For more info on that last part, see my post here:
[http://www.ubuntuforums.org/showpost.php?p=410657&postcount=3](http://www.ubuntuforums.org/showpost.php?p=410657&postcount=3)


Thanks for the information. 

Just tried 

$ssh -X <user@ip_address>

for a remote box on LAN. Afterwards, I can start X applications. Some of these are of reasonable performance, (e.g. kdevelop etc), but some are *very* slow (e.g. eclipse and OpenOffice).

I tried connecting through:

$ssh -X -o Compression=true -o CompressionLevel=9 <user@ip_address>

but this did not seem to make any difference in the display speed performance. 

Any hints how can I increase speed of GUI display?

Also,  have not found an answer for LTSP client application either for Linux or for Windows. Just wondering if something is up around for this kind of thing?

---

### Post by jimcooncat on 2007-03-16
Sorry, I missed your post two weeks ago, and originally misunderstood you weren't working over a LAN. Simplest way to do gui across the internet is with VNC over ssh. Freenx would probably get you better performance but is more painful to set up. There's plenty of tutorials on both in these forums.

---

