---
title: "Very very slow boot"
date: 2015-11-30
forum: General Help
---

### Post by george134 on 2015-11-30
Ok, so, here's the jist of it:
I have this ASUS laptop, not cutting edge but decently "new".
Previously I had installed UbuntuMATE (which i renounced because I wished to try Archlinux)
Archlinux I had on it for about 1 week (bit too hard for me, I'm kind of a newbie at this unix-based-OS stuff).
Finally I decided to install Ubuntu, which worked just fine for a while but now my laptop... well, won't boot, the Ubuntu boot screen appears and then either "nothing" for dozens of minutes and i have to restart or it opens... after like 5 minutes.

Any ideas ? Anything I can do besides formatting and installing the OS again ?

---

### Post by v3.xx on 2015-11-30
Hi george

Let it take five minutes to boot then run this command in terminal

```
systemd-analyze blame
```

and please post the results [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168").

---

### Post by RobGoss on 2015-11-30
Welcome George, It would help us help you if you were to provide the specs for the machine in question.

---

### Post by sammiev on 2015-11-30
> **v3.xx said:**
> Hi george

Let it take five minutes to boot then run this command in terminal

```
systemd-analyze blame
```

and please post the results using code tags.

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

+1

---

### Post by Plumtreed on 2015-11-30
After the latest update my system is booting very slow so I thought I would try 'systemd-analyze blame' but was advised that command was not found.

---

### Post by sammiev on 2015-11-30
> **Plumtreed said:**
> After the latest update my system is booting very slow so I thought I would try 'systemd-analyze blame' but was advised that command was not found.

Works good here.

What version of Ubuntu are you using?

---

### Post by Plumtreed on 2015-11-30
Using 14.04 LTS...........copy & paste and it says command not found

---

### Post by oldfred on 2015-12-01
I think systemd was optional with 14.04, I do not have it.
But then you need to look at /var/log/dmesg

You can run this for major issues:
       sudo grep -E -i "error|warning" /var/log/dmesg

Or just post the few entries with large time stamp differences. You may have several, but most entries will just be the standard posting of boot process with very little time gaps.

---

