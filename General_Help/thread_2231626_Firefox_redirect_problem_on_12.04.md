---
title: "Firefox redirect problem on 12.04"
date: 2014-06-26
forum: General Help
---

### Post by johnstondixon on 2014-06-26
Hi, 
    Using Ubuntu 12 04 on a dual boot machine and suddenly on Ubuntu but not windows I can no longer connect to my Yahoo Groups from Firefox Browser. Also cannot connect to Yahoo from Google, all other sites work ok. All my groups I can read with Firefox on windows.

Tnx
Noxid

---

### Post by johnstondixon on 2014-06-26
This is the message I get when trying to connect.

[B]Firefox has detected that the server is redirecting the request for this address in a way that will never complete.
[/B]

Tnx
Noxid

---

### Post by papibe on 2014-06-26
Hi johnstondixon. Welcome to the forum ):P

It just may be a problem with a cookie or the cache.

I'd recommend clearing both the cache and the cookies. Go to:
```
History -> Clear Recent History
```
There, expand the 'details' and make sure 'cookies' and 'cache' are selected.

When choosing the time range, choose at least one more day since it was working. If that does not work, do it again with the range 'everything'.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by collisionystm on 2014-06-26
I have seen this before and I am pretty sure its the web page try to redirect you more times than Firefox will allow. I believe by default IE has a higher threshhold. Try to increase your redirection limit from the default 20 to 30. 

about:config

search redirection

edit 'network.http.redirection-limit'

---

### Post by johnstondixon on 2014-06-27
Clearing cookies and cache did the job.
Tnx
Johnston

---

### Post by mörgæs on 2014-06-27
Good, please mark the thread 'solved'.

---

