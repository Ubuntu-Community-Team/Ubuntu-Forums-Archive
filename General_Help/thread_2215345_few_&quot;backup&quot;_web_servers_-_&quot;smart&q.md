---
title: "few &quot;backup&quot; web servers - &quot;smart&quot; link"
date: 2014-04-06
forum: General Help
---

### Post by Marchello_Lippi on 2014-04-06
Hi all,

I got few "backup" or "mirror" web servers. Now I'd like  to create some "smart" html link so that it checks the availability of  each my server and forwards my request to the first available one.

For example: my start page is placed at payed hosting [http://server.com](http://server.com) and user can see index.html with "start" button. My need is to check list of my home servers:

[http://web.server.com:8081](http://web.server.com:8081)
[http://web.server.com:8082](http://web.server.com:8082)
[http://web.server.com:8083](http://web.server.com:8083)

and forwards user's request to the first available home server from my list.

How do I perform it?
Is it possible at all?

Thanks for your attention,
looking forward to see your reply.

---

### Post by Marchello_Lippi on 2014-04-06
I'm sorry, I didn't explain how my home network works.
Subdomain web.server.com points to my home d-link switch which forwards requests:

port 8081 --> 192.168.5.1
port 8082 --> 192.168.5.2
port 8083 --> 192.168.5.3

One of home servers should be up.

So  my question is - how do I create html button which forwards request to  the first alive server upon pressing this button. Is it possible at all?

---

