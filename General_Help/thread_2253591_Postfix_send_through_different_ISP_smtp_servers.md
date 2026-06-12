---
title: "Postfix send through different ISP smtp servers"
date: 2014-11-20
forum: General Help
---

### Post by agillator on 2014-11-20
Posting here because I cannot find a specific postfix forum here or anywhere.

What configuration is needed for postix to send email through a user's ISP smtp server? I see how to send ALL email through one server with one password, but I need to use a different ISP server, username and password for each user. The postfix usernames are NOT the same as the ISP usernames. Any suggestions or suggestions where to search? Currently this is done by each user through Thunderbird, but I would very much like to do it at the postfix level if possible.

Thanks.

---

### Post by lisati on 2014-11-20
I haven't actually used it but the [sender_dependent_relayhosts_map]("http://www.postfix.org/postconf.5.html#sender_dependent_relayhost_maps") option sounds similar to what you are asking about.

---

### Post by agillator on 2014-11-20
You're right, does sound promising. I will check it out. That's a 'duhhhh' thing, you'd think I could have found something obvious like that. Thanks a bunch.

---

### Post by agillator on 2014-11-20
It does look as though it will work. I'll actually try to set it up later. At least now I know where to look and have a starting point. 

Thanks again!

---

### Post by lisati on 2014-11-20
> **agillator said:**
> It does look as though it will work. I'll actually try to set it up later. At least now I know where to look and have a starting point. 

Thanks again!

You're welcome.

It took me a few moments to find, I was momentarily distracted by recipient-dependent relays.... :D

---

