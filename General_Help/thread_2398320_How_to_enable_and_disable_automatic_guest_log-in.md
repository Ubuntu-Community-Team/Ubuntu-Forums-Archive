---
title: "How to enable and disable automatic guest log-in"
date: 2018-08-10
forum: General Help
---

### Post by webmiester on 2018-08-10
Hi guys,

I am using Ubuntu Mate 16.04 on a Raspberry pi, and developing kiosks with this thing.

Here is the thing:

I have all users log-into as "Guest" when they startup.

Ive read somewhere that I can automatically have the system log them into guest upon startup...

I am very interested in this... However, If things go wrong, and it automatically starts up as guest, how do I log-in as root afterwards so I can fix the problem?  Thanks


wordstar

---

### Post by webmiester on 2018-08-10
Ummm,

OK I tried out the autologin by adding the line "autologin-guest=true" at the "/etc/lightdm/lightdm.conf" file...

I figured I can probably log-out of guest and login as root...

But not... My when I restart I am stuck at the ubuntu logo, and it doesnt make it past that.  What can I do to get in my system?  Thanks

Wordstar

---

### Post by mc4man on 2018-08-10
You could try to go to a tty when boot hangs, ex. ctrl+alt+F3  If that works log in there as you, ect.
If no good then at grub screen choose Advanced > recovery.  At the recovery menu easiest is to choose to do a fsck,  press enter to do & enter to exit back to menu. Then choose the root shell prompt option and fix or remove your lightdm.conf.

This works just fine here in /etc/lightdm/lightdm.conf for auto login to guest session in 16.04
```
[Seat:*]
autologin-user=guest
autologin-guest=true
```

---

### Post by webmiester on 2018-08-12
Hi thank you mc4man for your time and suggestion,

The rpi doesnt have grub.  I was able to solve it by removing the SD card and putting it into my laptop running on linux mint.  From there I was able to erase the lightdm.conf file and redid the autologin configuration.  Thank you so much!  I really appreciate it.

---

