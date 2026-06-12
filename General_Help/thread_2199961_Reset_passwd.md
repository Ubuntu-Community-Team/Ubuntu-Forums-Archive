---
title: "Reset passwd"
date: 2014-01-16
forum: General Help
---

### Post by mayagrafix on 2014-01-16
I changed my password this morning but now have found out that new password does not work. Is re-start necessary for new password to become effective? 

I haven't logged out yet, what do u recommend? :confused:

---

### Post by papibe on 2014-01-16
Hi  mayagrafix.

It takes effect immediately. If you can't sudo, then you won't be able to do much.

I recommend this course of action described here: [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword").

Hope it helps. Let us know how it went.
Regards.

---

### Post by mayagrafix on 2014-01-16
mount -o rw, remount /
messages says no device with that name. Seems to be help screen for mount, text is large size so I only see last part of message screen which says name should be sba1 or uuuid etc.

---

### Post by Dave_L on 2014-01-16
There should be no space between "rw" and "remount":

```
mount -o rw,remount /
```

---

### Post by papibe on 2014-01-16
there should be no space mouting between options:
```
mount -o **rw,remount** /
```
that is 'rw', then comma, then remount. No space in between.

Let us know how it goes.
Regards.

---

### Post by mayagrafix on 2014-01-16
OK, got it. Back inside. Everything worked A-OK.

THANKS A MILLION :)

---

