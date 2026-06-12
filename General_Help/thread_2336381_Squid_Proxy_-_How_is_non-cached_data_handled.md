---
title: "Squid Proxy - How is non-cached data handled?"
date: 2016-09-07
forum: General Help
---

### Post by dozy on 2016-09-07
Hello Everyone,

Thanks for taking the time to read this.

I am using squid (3.5) with squidguard and clamav (icap server). I have turned squid's caching off.

My question is...
Since squid's cache is turned off, how is data/traffic being handled by squid before it is passed off to squidguard and claimav?
Is data being cached temporarily to disk anyway then deleted after all processes are complete, or does it just keep the data in memory and then stream it to subsequent services?

I ask because I am doing web filtering and virus scanning on both http and https and I don't want any of the https data hanging around in cache anywhere.


Thanks.

---

### Post by SeijiSensei on 2016-09-07
I believe Squid retrieves the requested object, then passes it to c-icap via a connection to port 1344 on localhost.  Squid gets a yea or nay reply from SquidClamAV, then passes on or deletes the object accordingly.  I doubt the content resides on disk if there is no caching enabled, though it might reside in memory for a while.  Since there's a cap on the size of scanned objects in c-icap.conf, 131072 bytes by default on my implementation, there probably isn't much need to use the filesystem for caching during the transaction.

This is all somewhat informed speculation.

---

