---
title: "no way for fast file transfers over msn in linux?"
date: 2007-09-03
forum: General Help
---

### Post by Batuhan on 2007-09-03
Can someone confirm that there is absolutely no way to have fast file transfers through MSN protocol because essentially all clients support file transfers only over msn servers thus not allowing direct connection?

I've gone through countless threads and noone gives a clear answer(pidgin faq says fast transfers are not possbile but i'm using amsn).

There is NO WAY in linux for an MSN user to have fast file transfers, is this right?

---

### Post by tszanon on 2007-09-03
> **Batuhan said:**
> Can someone confirm that there is absolutely no way to have fast file transfers through MSN protocol because essentially all clients support file transfers only over msn servers thus not allowing direct connection?

I've gone through countless threads and noone gives a clear answer(pidgin faq says fast transfers are not possbile but i'm using amsn).

There is NO WAY in linux for an MSN user to have fast file transfers, is this right?
Up to now, I have only used gaim and pidgin and, as stated, they say that the transfers go through msn servers, and that is responsible for the low transfer rates.

I don't know if it's possible to revert this, but I hope it is. But, for now, I suggest people to use email. :)

---

### Post by Batuhan on 2007-09-03
Yes e-mail is an option when you absolutely have to but in a conversation, one needs to send a picture or piece of music quick, and with my connection it is a matter of seconds in theory.

But it takes AGES to complete.(1-2kbps)

And I hate to annoy windows/macos people to use e-mail in those cases. Sanding a file from microsofts messenger is a matter of dragging and dopping a file. But when I say "please mail it..." they should open their mail client and go through a procedure, and it's even wors if they are using web based mail.

I personally do not see this as an option.

So there are no clients with this hot feature right?
I find this strange.

---

### Post by tszanon on 2007-09-03
> **Batuhan said:**
> Yes e-mail is an option when you absolutely have to but in a conversation, one needs to send a picture or piece of music quick, and with my connection it is a matter of seconds in theory.

But it takes AGES to complete.(1-2kbps)

And I hate to annoy windows/macos people to use e-mail in those cases. Sanding a file from microsofts messenger is a matter of dragging and dopping a file. But when I say "please mail it..." they should open their mail client and go through a procedure, and it's even wors if they are using web based mail.

I personally do not see this as an option.

So there are no clients with this hot feature right?
I find this strange.
I agree, "forcing" people to use email is a pain in the neck. But I don't know if there is any client that can send files through the msn network faster than 2 KBps. I'm gonna check if the Pidgin guys have plans to work on this.

---

### Post by Batuhan on 2007-09-03
Their faq says:

> Why are file transfers so slow? 

MSN file transfer support is limited to the proxied version of file transfer support in the protocol. This means that the files are sent to MSN's servers, then the server sends the data to the other user. We don't know if or when we will ever support any of the peer-to-peer file transfer methods available in the MSN protocol. 

[http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#Whyarefiletransferssoslow](http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#Whyarefiletransferssoslow)

Very annoying. I'll be hating it but, does MSN Live messenger work through wine on Linux by any chance?

---

### Post by hardyn on 2007-09-03
using AMSN and manually opening ports on your router, i have fast download speeds.

---

### Post by Batuhan on 2007-09-03
> **hardyn said:**
> using AMSN and manually opening ports on your router, i have fast download speeds.

Oh right, it was that easy. I forwarded the port from my wireless router and amsn goes lightning fast! Thanks!

---

