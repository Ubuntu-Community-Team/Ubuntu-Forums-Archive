---
title: "DCOPserver not running-Firefox and shutdown problems"
date: 2008-06-15
forum: General Help
---

### Post by lhc_surfer on 2008-06-15
I have experienced the same problem as 

[http://ubuntuforums.org/showthread.php?t=818241&highlight=ohiomoto+hosed](http://ubuntuforums.org/showthread.php?t=818241&highlight=ohiomoto+hosed)

> 
1. System won't shut down properly. After hitting the "power" icon the system hangs on a blank desktop.I have to power down the computer shutdown.

2. Firefox--lost all bookmarks and the ability to use bookmarks. But history is still available.

3. Firefox-- Won't browse "Back" or "Forward".


In addition I'm experiencing:

4. When I open a shell I get this message: "could not read the network connection list. Please check that **dcopserver** is running".

5. I can't print any document.

When I run firefox from shell I get:

"(firefox:17127): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
"

Then firefox opens but with the problems descripted above.



When I type "dcopserver" in shell I get:

Only one line in dcopserver file !:
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
Only one line in dcopserver file !:
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
DCOPServer self-test failed.


I tried to implement the solution described in the previous link: i.e. remove all old kernels. At least that's what I think I did, as _I'm really not an expert_. However it worked fine for 2 or 3 session, then the same problem occurred again.

Can anyone tell me if there's a more lasting solution, or specify what packages in synaptic should be removed and which shouldn't? 

Thanks!

---

