---
title: "Need help retrieving cookies from old partition"
date: 2008-05-09
forum: General Help
---

### Post by caiazpa on 2008-05-09
Hi All,
Total newb, need a hand.  I foolishly self-destructed my Hardy Heron installation after upgrading from Gutsy.  I have installed a fresh copy onto another partition and need to know if it is possible to retrieve my cookies from the old ext3 partition (which I can access from the new install).  

I ask because I relied on a login cookie on that partition, and without it I am completely unable to access my gmail account.  The secondary address I listed with gmail is an old employer and I can't remember my security question. 

Is there a way to retrieve the cookie from the other partition for use with the new installation?  Or should I begin the process of getting a new email address (oy vey).

Thanks for any help you can provide.

---

### Post by Irony on 2008-05-09
Locate your cookies text file in the following location;

```
~/.mozilla/firefox/mq4oxp3e.default/cookies.txt
```

Note the gobbledegook mq4oxp3e.default part will be different for you.

Once located copy it over.

---

