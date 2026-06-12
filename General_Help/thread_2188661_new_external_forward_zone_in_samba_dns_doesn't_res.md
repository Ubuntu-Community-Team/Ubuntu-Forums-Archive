---
title: "new external forward zone in samba dns doesn't resovle internal ip addresses"
date: 2013-11-18
forum: General Help
---

### Post by casper4 on 2013-11-18
Hi all,

I have installed a ubuntu 12.04 with samba versoin 4.0.1 i think it is.. the version where i can use windows remote administration tool to create users and all that jazz...

Now i have the classic problem where my mobile won't sync with my email server when i'm on my lan.. the reason for this is because my phone is set up to sync with my email servers outside domain name and my firewall doesn't allow me to loop.. 

one windows way of solving this was to make a second forward lookup zone in your windows dns server for your external domain and have it resolve to internal IPs in my case my mail server.. problem solved... 

NOW

I tried this creating a new forward lookup zone for my external domain on my samba internal DNS server and have it resolve external domain names with internal adresses.. but it doesn't work.... 

I was told that linux DNS won't work this way because DNS was never ment to be used this way.. IE yet another case where MS breaks the "rules" :P... 

Is this true?
are there any workarounds?
or better way to do it?

Thanks

Casper

---

