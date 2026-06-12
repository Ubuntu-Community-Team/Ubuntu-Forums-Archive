---
title: "Port 80 seems to be throttled"
date: 2008-02-25
forum: General Help
---

### Post by dchurch on 2008-02-25
Hi all,

Since upgrading to Gutsy I have had problems with getting web pages to load - about 70% of the time they load fine (albeit a little slow), the other 30% I have to continually click refresh until eventually the page load - these are pages like google, microsoft - sites that I know are up.

My question is, is there a network watcher that I can use that will enable me to watch the traffic on port 80.

FTP downloads are fine - I downloaded a dummy 10meg file in about 3 seconds, so I know the connection is fine - other ports seem fine too, it just seems to be port 80.

Another thing that crossed my mind is that it might be a virus?

Thanks in advance,

---

### Post by Het Irv on 2008-02-25
If you want a packet sniffer you can try wireshark, it's in the repos.  You have to run it in root mode for it to work.  It is simple to use, not so simple to interpret.

---

### Post by dchurch on 2008-02-25
Thanks for that - I'll give it a try now.

---

