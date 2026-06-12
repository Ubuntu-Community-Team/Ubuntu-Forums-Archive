---
title: "Scripts not running"
date: 2013-03-14
forum: General Help
---

### Post by taylorpIII on 2013-03-14
I work for a small business and I help out with I.T.  

If a CSR says that the scripts are not running, what is a quick solution to the problem?  What do I/we need to do in the terminal to check why they are not running and get them running again.  They are working fine now, but periodically a CSR will visit us and say the scripts are down.  Thx!

---

### Post by iponeverything on 2013-03-14
The very first thing I would do is ask the CSR what they are talking about - and what I would need to do to replicate the issue.

 "scripts are down" sounds a bit like someone walking over to my desk and asking if "something is wrong with the Internet"

---

### Post by schragge on 2013-03-14
[thread=2118503]From previous inputs of the OP[/thread] I presume he means cgi-bin scripts on web server. Am I right, Paul?

---

### Post by taylorpIII on 2013-03-14
Yes you are right.  The cgi-bin scripts.  Sorry I wasn't clearer about that.

---

### Post by iponeverything on 2013-03-15
look in access and error logs for apache - how are the scripts being invoked? php? 

I would take a careful look at transient issues like this, as many times they are an early warning that the system has been compromised.

---

