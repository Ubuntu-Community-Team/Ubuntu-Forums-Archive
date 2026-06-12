---
title: "Sudden issues with slow applications and crashes"
date: 2020-01-24
forum: General Help
---

### Post by knoppys on 2020-01-24
Hi All

Tia for any advice you can offer. 

To give you some idea of my environment. 

On my desktop:
[LIST]
[*]Ubuntu 16.04
[*]16GB Ram
[*]4 Cores i7
[*]Lenovo
[*]Cable LAN
[*]60MB Download speed
[*]9MB Upload
[/LIST]

As suddenly as a week ago I started getting issues with slow loading programs. Everything I opened seem to take an extra 4 - 5 or even 10 seconds. Even web pages are taking extra long to resolve. 

Last night the whole thing came to a crash when I started uploading a site to the server via FTP. Everything just froze. Had to hard reset.

Ive never faced this issue before and really need to understand how I can go about resolving the issue on my own. How do I check for hardware issues, how do I check for software issues etc. 

What the best route to troubleshoot?

---

### Post by TheFu on 2020-01-24
What do the log files show?  Google "ubuntu logs" - find the *.ubuntu.com/  domains and read those.

A few commands to help determine the system state:
* free -hm
* top

Don't let the system run out of both RAM **and** swap. On a system like yours, swap should be 4.1G.  When the system starts feeling "slow", then close the program using the more RAM.  top will show that program ... near the top.

And please don't use plain FTP. That protocol should have died in 2002.  These days, a secure protocol that doesn't put credentials in clear text on the network should be used.  If the webhost doesn't support that, fire them.  Look for a webhost that supports ssh, sftp, rsync ... but if they support ssh, you get the others free.

---

### Post by oldrocker99 on 2020-01-24
There's also HTTP Everywhere, which is a free plugin for browsers straight from the Electronic Freedom Foundation (who are the Good Guys).

I highly recommend it, and be careful on sites that don't show **https://**.

---

### Post by knoppys on 2020-01-24
total        used        free      shared  buff/cache   available
Mem:            15G        4.6G        5.2G        1.4G        5.8G        9.1G
Swap:            0B          0B          0B

Top did show me the a running program using prettty much 100% CPU but, after closing it I still have issues with slow speeds. 

Ill look more into the logs.

---

### Post by CatKiller on 2020-01-24
> **knoppys said:**
> As suddenly as a week ago I started getting issues with slow loading programs. Everything I opened seem to take an extra 4 - 5 or even 10 seconds. Even web pages are taking extra long to resolve. 

Those sound like exactly the symptoms you'd get with a hard drive/cabling problem. I/O issues cause all sorts of knock on oddness. Check your logs and monitor your system for a rogue application or a misconfiguration somewhere, of course, but you can't rule out hardware.

---

### Post by knoppys on 2020-01-28
Ok so not sure what has happened but the speed seems to have resolved now. 
I wonder if this was a more global network issue than something more local. 
Thanks for the efforts though.

---

