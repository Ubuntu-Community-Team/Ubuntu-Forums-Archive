---
title: "Pidgin - Message could not be sent because an error with the switchboard occurred"
date: 2008-06-13
forum: General Help
---

### Post by Azalar on 2008-06-13
Whilst using the MSN protocol in Pidgin I occasionally get the message "Message could not be sent because an error with the switchboard occurred" 
when trying to talk to people on my contact list.
I did a bit of research into it and tried a few suggestions but can't seem to get rid of the problem.
I am trying to assess whether its Pidgin or MSN that is the problem.
Has anyone else seen this problem and know how to stop it?
Do people using other IM clients get the same problem?

---

### Post by Tom--d on 2008-06-13
I suggest to use emesene for MSN. Its in the repos and is a fully supported msn client.

A lot better than Pidgins support for msn.

---

### Post by ad_267 on 2008-06-13
Thanks for that. I don't use MSN myself but my sister's always using my computer and this is the one thing she complains about, other than that she loves Ubuntu! Hopefully emesene will fix this for her too.

---

### Post by Tom--d on 2008-06-13
It should as its very similar to Windows Live messenger :)

---

### Post by Azalar on 2008-06-16
Switched to Emesene
Much much better than Pidgin and doesn't suffer the bug.
cheers.

---

### Post by MasterJS on 2008-06-16
The problem is basically your internet connection that isn't allowing you to send your messages through Pidgin.

---

### Post by ad_267 on 2008-06-16
> **MasterJS said:**
> The problem is basically your internet connection that isn't allowing you to send your messages through Pidgin.

Can you explain that more? Why would my isp block pidgin from sending messages? How is it different to emesene? Surely they're both using the same protocol, although emesene must be implementing it more accurately as it doesn't suffer this problem.

---

### Post by ciempies on 2008-08-03
Hi guys. I'm bumping this in case someone out there is having the same issue with the "Message could not be sent because an error with the switchboard occurred." 

After reading this thread as well as [http://ubuntuforums.org/showthread.php?t=530515&page=3](http://ubuntuforums.org/showthread.php?t=530515&page=3) the problem was fixed - for now -by going to

Accounts-> Edit account -> Advanced -> Use HTTP method had to be checked (not unchecked).

thanks

---

### Post by RolandFlagg on 2008-09-07
what? it has to be checked? but the thread you linked specifically said that it should be unchecked...
and i'm just randomly starting to have this problem today

---

### Post by Keisad on 2008-10-06
Emesene works like a charm. Definitely recommended.

---

### Post by jerome1232 on 2008-10-06
Just to note I've only gotten that message in pidgin if my connection drops and gets reacquired (me being far away from the router and my wifi adapter has the psu in between it and the router this tends to happen on occasion)

---

