---
title: "HELP - Password not accepted at login - just removed libpam-krb what do I do?"
date: 2013-04-06
forum: General Help
---

### Post by jflock on 2013-04-06
So I can't login. 

I had tried to setup kerberos authentication to log into some ADS thing at my new university, however that didn't work and resulted in me having to enter my password twice for everything. 

So I did: sudo apt-get remove libpam-krb5

Then some authentication tool came up asking if I wanted to ignore local changes(?) to which I entered yes. 

Then I restarted, now this!

I tried to do recovery mode and enter into the root prompt, but apparently i is in read-only mode.

Please help, my soon to be due PhD thesis corrections are on that computer!

---

### Post by steeldriver on 2013-04-06
I don't know how to fix your kerberos issues, but to get into read-write mode in the recovery console you can remount at the root prompt using

```
# mount -o remount,rw /
```

(note that's there's no space between the remount,rw options)

---

