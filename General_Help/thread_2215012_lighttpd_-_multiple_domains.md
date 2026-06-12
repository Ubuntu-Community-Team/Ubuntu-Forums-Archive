---
title: "lighttpd - multiple domains"
date: 2014-04-04
forum: General Help
---

### Post by Marchello_Lippi on 2014-04-04
[COLOR=#333333][FONT=Helvetica Neue]Hi all, [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]I'm about to use lighttpd as web server. I got few domains and hope to use the same computer to host them all. Is it possible at all with lighttpd? One of ideas was to start few lighttpd processes to listen on different ports. But I hope so much that someone can advise me more clever decision. [/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]Looking forward to see your reply.[/FONT][/COLOR]

---

### Post by m_duck on 2014-04-04
I'm not familiar with lighthttpd but from using Apache, what you need is virtual hosts. The "Linode Library" is a really good source of information for running servers (doesn't have to be one of theirs either). Their lighthttpd on Ubuntu document is [here](https://library.linode.com/web-servers/lighttpd/ubuntu-12.04-precise) and there are multiple sections on virtual hosts.

I hope this helps :)

---

