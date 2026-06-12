---
title: "Memory management - spawing java"
date: 2005-10-19
forum: General Help
---

### Post by SpiroChronis on 2005-10-19
Hello Ubuntu Masters,

I have a spawning issue with java and ubuntu. 

Background: I have a java IRC control, which i call a SessionParent. This SessionParent listens for specific commands to spawn new IRC SessionChildren. When the SessionParent receives it's prompt, it spawns a new SessionChild. This SessionChild basically registers itself to the IRC server on a specific channel and then starts dealing with commands appropriately. The SessionParent currently spawns the child via this terminal command:
java SessionChild -sessionid 89

Previously, this all was working perfectly, up until a couple of days ago.

Problem: It seems that the newly spawned SessionChild apps are now only able to receive around 100 commands and then they freeze [or are dormant]. it's as though the commands following the 100 are queuing up in memory, waiting to be processed. If the SessionParent is forcefully destroyed the SessionChild apps continue processing the following requests.  
If the SessionChild app is not spawned by the SessionParent, but is manually started the SessionChild works perfectly. 

I feel that it may be a problem with memory allocation to the spawed java apps, and that the spawed documents are only allocated 100 processes each? 

This problem is beyond me, can anyone help?

Note: normal security updates etc. took place over the last few days

---

