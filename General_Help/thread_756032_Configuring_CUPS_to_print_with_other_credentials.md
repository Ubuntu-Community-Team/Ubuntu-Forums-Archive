---
title: "Configuring CUPS to print with other credentials?"
date: 2008-04-15
forum: General Help
---

### Post by WakkiTabakki on 2008-04-15
Hi all
I have this problem connecting to a CUPS server.
In short this is the situation. At the university where I work, they have just reconfigured the printing system (among a LOT of other things, so not much is working any more...). The main problem now is that I cannot print, there is no error message or anything, it just doesn't print...The support claims that the print job gets "stuck" locally, but it stays briefly in the print queue and then disappears (much as it does when all works fine). I've gone through every log but can't find anything indicating that any error occurred. It seems that the job gets sent to the sever, which simply accepts it and quietly throws it away.

So the support told me that I must create a local account with the same username and password as I have on their system, otherwise I won't get authenticated by the server.
My problem is that I use this laptop in many other situations (it's been configured for my home server and for a few other places as well) and having separate local accounts just to be able to print makes absolutely no sense to me (I would have to sync documents, mail, calendar, bookmarks etc between accounts which simply isn't doable). 

Question:
- Can I configure a printer (via CUPS ipp-protocol) to print using other credentials than my local ones. I've tried setting it up with the URL ipp://UserName:Password@Server/printer but it changes nothing


Cheers
/N

---

### Post by pointone on 2008-04-16
Try using the Samba backend:

```
DeviceURI smb://<username>:<password>@<server>/<printer>
```

---

### Post by WakkiTabakki on 2008-05-04
Nocando, I'm afraid... Can only connect via ipp (as far as I'm informed anyway, but the admins proven to be quite clueless in other respects as well so I guess you never know)...
It's via the ipp-protocol that I need to validate with other credentials. A colleague went through the source code and apparently it picks the username from whoever's logged in, so it seems a bit futile.

Thanks for the suggestion, though...

/N

---

