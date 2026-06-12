---
title: "Firefox 1.0.6 Has Slowed WAY Down"
date: 2005-09-15
forum: General Help
---

### Post by JNewman on 2005-09-15
A day or two after upgrading to Firefox 1.0.6, I'm suddenly seeing very slow throughput. I loaded IE under Wine to compare the two, and the results are very different. Using the bandwidth tester at lenon.com, I see throughput of about 40-50 Kbps under Firefox and of about 4-5 Mbps under IE. Same computer, same cable modem, same everything.

What could be causing this?

I started checking because I noticed horribly slow loading for web pages I frequently visit that normally load quickly. I don't know what else could have changed, other than the upgrade to 1.0.6.

I've disabled all my extensions and restarted Firefox -- heck, I've restarted the computer -- in the hope of fixing this, but with no success. 

Any help would be really appreciated. This is really hurting my day.

Thanks!

---

### Post by Zelut on 2005-09-15
Have you tried the minor setting changes outlined in the Ubuntu Guide?  There are a few things you can change.  See these instructions below & see if this helps.

Address Bar -> about:config

Filter: ->
network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

---

### Post by JNewman on 2005-09-15
First of all, thanks for your reply.

I'm afraid I did already have those settings configured. Ran another comparison; this time I'm seeing around 300kbps in Firefox vs. about 6 Mbps in IE. That difference does not make sense to me. Would upgrading to 1.0.6 somehow "de-tune" Firefox to so great an extent?

What else might I check?

---

### Post by JNewman on 2005-09-15
I think I have solved my problem ... after one more try to remove a mis-behaving extension, I looked for its leftover settings in about:config and reset them all. That seems to have given me quite a bit more throughput - back to the responsive "feel" I'm used to (and that's borne out in a speed test too).

Whew.

---

### Post by matthew on 2005-09-15
Just for our information, which extension was misbehaving and got removed?

---

### Post by Zotova on 2005-09-18
I've found personally that RIP (remove it permentally) effects the speed of Firefox a lot on ubuntu - not only the page loading time but also the stability of Firefox, with the extension enabled Firefox would often hang for me.

---

