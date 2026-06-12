---
title: "Evolution are &quot;DNS cache happy&quot;"
date: 2006-12-27
forum: General Help
---

### Post by Aleksandersen on 2006-12-27
Hi,

I have recently changed host from Made2Own to GoDaddy. This also include e-mail host.

And I have had no problem with Firefox, which got the new DNS right after just under half an hour. However, I still experience problems with Evolution which attempts to get e-mail off my old server.

How can I get Evolution to retrieve the messages from my new server (same URI address, but different IP)?

---

### Post by dcstar on 2006-12-27
> **Aleksandersen said:**
> Hi,

I have recently changed host from Made2Own to GoDaddy. This also include e-mail host.

And I have had no problem with Firefox, which got the new DNS right after just under half an hour. However, I still experience problems with Evolution which attempts to get e-mail off my old server.

How can I get Evolution to retrieve the messages from my new server (same URI address, but different IP)?

Close the Evolution client, open the System Monitor and end the Evolution-data-server process, restart the client and see if things work.

---

### Post by Aleksandersen on 2006-12-28
[http://opendns.com/cache/](http://opendns.com/cache/)

Refreshing the domain at my DNS provider helped.

---

