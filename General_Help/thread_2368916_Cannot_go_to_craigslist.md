---
title: "Cannot go to craigslist"
date: 2017-08-16
forum: General Help
---

### Post by leunam12 on 2017-08-16
Every time I try to go to spacecoast.craigslist.org I get an error saying that the connection is not secure. The message says:

"Your connection is not secure.
The owner of accounts.craigslist.org has configured their website improperly. To protect your information from being stolen, Firefox has not connected to this website."

The same thing happens in Chrome, but it does not happens in any browser on Windows.

I will appreciate any help on this.

---

### Post by jim_deadlock on 2017-08-16
Try this:

```
sudo update-ca-certificates
```

---

### Post by leunam12 on 2017-08-17
It didn't work. Let me see if this is related to opendns somehow. Thanks

---

### Post by leunam12 on 2017-08-19
Yes, this is related to opendns. for some reason opendns is blocking craigslist. I went to opendns and whitelisted craigslist, and now it loads but everything looks wrong. I'm going to post on an opendns forum. Thanks

---

### Post by maglin2 on 2017-08-19
I use opendns and that site loads fine for me without any whitelisting.

---

