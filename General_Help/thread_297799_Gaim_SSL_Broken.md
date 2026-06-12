---
title: "Gaim SSL Broken"
date: 2006-11-11
forum: General Help
---

### Post by JoshHendo on 2006-11-11
Recently I tried to compile Gaim2 beta5. I wasn't successful in doing so, so I decided to stick with beta4 until someone put a deb on the forums.

When I opened up beta 4, and tried to logon, it wasn't able to log on to either Google Talk or MSN, and it came up with the following error for MSN:

```

(account) was disconnected due to an error: SSL support is needed for MSN. Please install a supported SSL library. See http://gaim.sf.net/faq-ssl.php for more information.
Gaim will not attempt to reconnect the account until you correct the error and re-enable the account.

```

When I saw that, I decided I would login to amsn for now until I can fix that, but it has a similar problem with SSL.

What would I need to do to fix this :)?

Thanks.

---

### Post by Qew on 2006-11-11
I use "./configure --enable-gnutls=yes" when I compile Gaim. I have a working version of Gaim 2.0 beta 5 working on MSN, Jabber, AIM, Yahoo and ICQ. Ensure you have libgnutls-dev installed, along with the other dev packages that you'll need. Saying all this, I'm using Dapper rather than Edgy, but there shouldn't be a difference.

---

### Post by JoshHendo on 2006-11-11
> **Qew said:**
> I use "./configure --enable-gnutls=yes" when I compile Gaim. I have a working version of Gaim 2.0 beta 5 working on MSN, Jabber, AIM, Yahoo and ICQ. Ensure you have libgnutls-dev installed, along with the other dev packages that you'll need. Saying all this, I'm using Dapper rather than Edgy, but there shouldn't be a difference.
Tried that, didn't seem to make a difference :(

---

