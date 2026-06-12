---
title: "ubuntu 12.04 64 bit hangs?"
date: 2013-03-30
forum: General Help
---

### Post by boy18nj on 2013-03-30
when using chromium, once in a week my laptop do hangs. then none of the keys work even tty also doesn't works. as a result i have to hard reboot my laptop.

is there way to find out what hangs my laptop and stop ubuntu hanging?

---

### Post by boy18nj on 2013-03-30
any one faced this issue or aware of this one?

---

### Post by sanderj on 2013-03-31
> **boy18nj said:**
> when using chromium, once in a week my laptop do hangs. then none of the keys work even tty also doesn't works. as a result i have to hard reboot my laptop.

is there way to find out what hangs my laptop and stop ubuntu hanging?

Did you run memtest86 from the Grub boot menu? Keep it running for a few hours.

---

### Post by Paqman on 2013-03-31
Yep the main things to look for would be overheating, bad memory sticks, etc. It's most likely to be a hardware problem. You could check the kernel logs to see if anything weird is logged just before it locks up.

---

### Post by boy18nj on 2013-03-31
> **Paqman said:**
> Yep the main things to look for would be overheating, bad memory sticks, etc. It's most likely to be a hardware problem. You could check the kernel logs to see if anything weird is logged just before it locks up.

I won't know when it would locks up, hence can't check kernel logs at that moment.

You brought a interesting point, how do i should check kernel logs?

---

### Post by boy18nj on 2013-03-31
> **sanderj said:**
> Did you run memtest86 from the Grub boot menu? Keep it running for a few hours.

no i did not run this test, but surely will run this. thanks for the tip.

---

### Post by Paqman on 2013-04-01
> **boy18nj said:**
> I won't know when it would locks up, hence can't check kernel logs at that moment.

You brought a interesting point, how do i should check kernel logs?

After it locked up and you rebooted you'd go and look for the last thing(s) it logged before locking up.

There's an application on your system called Log File Viewer, you can use this to read the logs.

---

### Post by d4m1r on 2013-04-01
Only using Chromium? That would be strange...If that is the case though, use Firefox instead.

---

