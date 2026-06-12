---
title: "torrent"
date: 2007-09-26
forum: General Help
---

### Post by naoko on 2007-09-26
More specifically, torrent problems. I am NOT behind a firewall, and i am Directly conencted to the internet, (as in im not on a router) (and yes i know that i should have at least a firewall, but ill deal with that once i fix my current problems.)
 I am on Ubuntu feisty, i have been for a month now, i was able to download any torrents just fine, for this entire time, suddenly i keep getting "Connection Refused" i tried other trackers, other clients (Azureus, Bit tornado, bit torrent, etc) ive tried other torrents as well ,and all my torrents are having problems with this "connection refused". Finally i went to another torrent sie and tried a completely new download using bit tornado. Bit tornado gives me a yellow light, which describes this as behing behind a firewall or proxy server. I have my firewall off as far as i know, and im not on a router, im directly connected. Now there have been a few updates ive done recently, which were notified to me, and some updates i did using synaptic package manager. i cannot tell you what it is i updated or added into my  system because it was quite a few things, mostly revolving around media playback (codecs and the like.) could anyone here perhaps explai nthe nature of my problem if they recognize it? if you wish to provide me any information you may need to discover the nature of the problem, please leave detailed instructions to me, and i will post any info you require.

ps, i thought about my ISP maybe throttling my torrents or something similar, but ive actually phoned them, and found that is not the case, they said that my city is small enough that even if i did large 1 gig torrents every day that i would not be throttled or suspended in any form, as there is hardly any "clogging" traffic where i live (or he said something to that effect)

---

### Post by por100pre1 on 2007-09-27
ISPs are not always to be trusted, specially with uploads. Your system have a firewall installed, it's iptables. Not sure if this is the case, but lets try to ensure the ports are open. There's a tool for opening ports in the firewall, it's called Firestarter:

```
sudo aptitude install firestarter
```

[Here's]("http://www.fs-security.com/docs/policy-page.php") how to open the ports. Open it, set it up and close it, no need to keep it open.

Let me know if this works or not... :-k

---

