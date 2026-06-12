---
title: "Time unchanged since daylight saving"
date: 2008-03-20
forum: General Help
---

### Post by steveneddy on 2008-03-20
I may be the last one with this issue, but my time didn't change at the appointed time when daylight saving came in the US.

I would like to get this fixed as it's driving me bananas.

I have tried sync with internet servers, UTC on and off.

So many restarts today that it said it needed to fsck, so I let it.

My tzdata is version 2007f-3ubuntu1.

I wonder if I have the wrong version or something, or maybe there is a fix that I could perform that would correct this issue.

Thank you in advance.

---

### Post by jpkotta on 2008-03-20
```
[jpkotta@gauss w](1)$ dpkg -l tzdata
...
ii  tzdata                   2007k-0ubuntu0.7.10.1    time zone and daylight-saving time data
```

I'd do an update and an upgrade.  I remember this getting updated not too long ago.

---

### Post by DJ_Peng on 2008-03-21
I hate to say this, but I have you both beat. > peng@MyComp:~$ dpkg -l tzdata
...
||/ Name           Version        Description
+++-==============-==============-============================================
ii  tzdata         2008a-1ubuntu1 time zone and daylight-saving time data
Definitely time to update :)

---

### Post by steveneddy on 2008-03-25
Days later this is still an issue.

```

tzdata         2007k-0ubuntu0

```

This is driving me nuts!

---

### Post by DJ_Peng on 2008-03-25
If it's only ocurring in the Gmail site I'd guess it's a Gmail issue. Otherwise it's odd that it be an Ubuntu or Firefox  issue and only ocurring on that one website.

---

### Post by steveneddy on 2008-03-25
> **DJ_Peng said:**
> If it's only ocurring in the Gmail site I'd guess it's a Gmail issue. Otherwise it's odd that it be an Ubuntu or Firefox  issue and only ocurring on that one website.

Huh?

My clock is off by one hour (slow) and I would like to repair this.

It has nothing to do Gmail.

---

### Post by geraldm on 2008-03-27
set the time manually using the command date.  Check the manpage for date.

Gerald

---

