---
title: "Some file attributes are not transferred with rsync"
date: 2015-08-27
forum: General Help
---

### Post by cogset on 2015-08-27
I've just seen something unexpected: after rsyncing my installation to a new drive and having started the system, I've noticed that some attributes of the /usr/bin/dumpcap executable hadn't been transferred (or maybe I am wrong and these aren't actually file attributes) .

Following this guide [URL="http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/"]http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/ 
[/URL]I had set the capabilities of this file to **cap_net_raw,cap_net_admin=eip,** the weird thing is that such capabilities weren't transferred with rsync, which means that in order to use wireshark I had to redo this step.

Why weren't these capabilities transferred, and where is this info stored?

---

