---
title: "USB problem"
date: 2013-08-08
forum: General Help
---

### Post by tapasray on 2013-08-08
I have installed Ubuntu 12.04 LTS alongside Windows 7 and it's working very nicely, on the whole. So much so that I do not feel like using Windows 7 at all. But there's a big problem. A little while after booting up, the USB ports stop recognizing anything I plug in, namely mice and pen drives. Would really appreciate some help here.

---

### Post by VMC on 2013-08-08
What kernel are you using?

```
uname -r
```

---

### Post by tapasray on 2013-08-08
Thanks, VMC! This is what I got, using your code -- 3.5.0-37-generic.

---

### Post by VMC on 2013-08-08
Interesting. I find that anything above kernel-3.5.0-38, the USB stick memory fails. You could knock it up a notch using this
```
sudo apt-get install linux-generic-lts-quantal
```

That's what I did to get to 3.5.0-38. As I've said, anything above that up to and include 3.11 causes my USB flash disk to take excessive amount of time to mount.

Another thing is monitor syslog and plug in your USB flash and see long long it takes to mount.

---

### Post by tapasray on 2013-08-08
OK, I'll try that and report back. Thanks again, VMC!

---

### Post by nicholas3 on 2013-08-11
I tried typing in [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install linux-generic-lts-quantal and I get a message saying "unable to locate package linux-generic-lts-quantal". I currently have [/FONT][/COLOR]3.8.0-27-generic and can't open a USB drive as well. The file on the USB is an ISO if that makes any difference. 

Thank you,
Nick

---

### Post by VMC on 2013-08-11
You might check your software sources.

---

### Post by tapasray on 2013-08-11
VMC, the issue seems to have gone away, though I haven't gotten around to trying your step. But I have another issue, which may or may not be related, with my Nokia E5 phone - 12.04 does,t see it at all. Posting a new thread on that.

Thanks again!

---

