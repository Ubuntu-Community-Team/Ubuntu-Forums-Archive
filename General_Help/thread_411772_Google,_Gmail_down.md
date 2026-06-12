---
title: "Google, Gmail down"
date: 2007-04-17
forum: General Help
---

### Post by Weaseal on 2007-04-17
Ok so where I work we can't get google.  We can't get ANYTHING google.  Gmail, google, etc.

When I do "host google.com" in a term window, I get the IP addresses and I can enter those and those work fine, but even the ones that resolve for gmail.com also only pull up google.com.  So, this solution is not only complicated for our more simple users but not fully functional.

All of our internet comes through a Windows machine (our clients are 50/50 Windows/Linux) which simply shares its connection (it can't get Google either).  We did virus scans on all of the computers and everything is clean.  We have a theory that someone maliciously did something to our internet-sharing comp (one of our tech guys was fired recently and did a few other things on his way out, although those were mostly easy fixes that are already solved).  However, I don't know enough about Windows to know what he could have done (if this problem was even created by him) to know what to do.

Tips?

---

### Post by chakkaradeep on 2007-04-17
I am able to login into my gmail account - might be ur ISP problem ?

---

### Post by Weaseal on 2007-04-17
Lol. I know Google works elsewhere.  It could be our ISP and we will investigate that.  Before we go calling them though, we want to make sure the problem's not on our end.

---

### Post by Ti_Uhl on 2007-04-17
> **chakkaradeep said:**
> I am able to login into my gmail account - might be ur ISP problem ?
 
I don't think he meant that google was down, he just can't reach it thru his corporate firewall, proxy.
 
Maybe you should check your hosts file, or firewall rules which are applied on the box that is used to share your internet. 
 
There are about a 1000 things he could have done, depending on how clever he is. But in any case, it seems a little bit daft of him to do something like that :)
 
Btw, what was the reason he got fired ? just out of curiousity :)

---

### Post by Weaseal on 2007-04-17
He was fired because we had a smoking computer and someone reported it to him and he said it wasn't a problem.  Naturally, the computer broke (specifically, it was the power supply), and was unusable for a few days, plus the cost of a new power supply.

We disabled the firewall completely and the problem persists.  Checking the hosts file -- on a Windows machine?  Where is this file?  What other related solutions could exist?  I am not at the office now but I will be tomorrow, so I will try that then.

---

### Post by Weaseal on 2007-04-18
Problem solved.  It was a spyware issue.  AVG Free killed it.

---

