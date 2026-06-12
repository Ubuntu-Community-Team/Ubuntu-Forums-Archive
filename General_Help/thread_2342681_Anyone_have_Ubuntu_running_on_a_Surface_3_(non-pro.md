---
title: "Anyone have Ubuntu running on a Surface 3 (non-pro)?"
date: 2016-11-08
forum: General Help
---

### Post by iry100fan on 2016-11-08
Hi Everyone,

Just curious if anyone has gotten Ubuntu (any version) to run reliably on a Surface 3 (non-pro) tablet...

I managed to get Ubuntu 16.10 installed but it seems to have numerous problems:
[LIST]
[*]Wi-Fi drops after a few minutes and won't work until rebooted.  The Network Manager indicates a good working connection though.
[*]Touchscreen doesn't recognize any input, be it from finger or stylus.
[*]The stylus is not detected in the Bluetooth manager.
[*]No sound.
[*]Can't adjust screen brightness.
[/LIST]

I tried originally installing Ubuntu 16.04LTS, but it won't boot.  At least 16.10 boots, it's just not really usable with the above problems.

Like I said,  just wondering if it is possible to get Ubuntu (or any version of Linux) running on a Surface 3 tablet.

Happy days...
-Brian

---

### Post by zx6r1033 on 2016-11-13
I came here looking for information on the same subject, so maybe we can keep this going. 

There is a custom kernel available for the surface devices that will solve the touch screen issues. Do a search for "Tigerite kernel".

Sadly, I couldn't tell you how well it works. I've been trying for a few hours now to get Ubuntu up and running on my S3, but it stops responding after the login screen. I can access terminal from the login screen without issue, and I can run Ubuntu from a live USB without issues. Not sure where to go from here. 

There are quite a few people using it, but it seems most communities these days are kind of closed off to sharing information with people who don't already know how to do things. 

One thing I have read is, when you first start out, you'll need an external mouse and keyboard. 

I hope what little bit of information I had will help you. Can't wait to see someone get it working.

---

### Post by orychalk on 2016-11-26
Hello,

I don't use Ubuntu but Fedora specific version since 6 months and this is stable for work everyday :
[https://stephenjust.ca/fedora-surface3.html](https://stephenjust.ca/fedora-surface3.html)

Good Luck

---

### Post by perryous on 2017-04-24
Ubuntu 17.04 comes with the 4.10 kernel, which fixed everything except the power manager. The battery still doesn't get read, and brightness still cannot be controlled. Stephen Just indicated in a Reddit post that his S3 power manager had not yet been pulled into development for 4.11, but hopefully will be in 4.12 or 4.13.

---

### Post by rojhack on 2017-10-28
I know this thread is old, but I have 17.04 running on my Surface non-pro 3 too, and the wifi still drops, and no battery level indicator. But sound, touchscreen, and bluetooth stylus work like a charm. Seems to me the battery drains terribly fast too? Does anyone know, is it a known issue for Ubuntu to take up a lot of battery? Could be I'm used to my laptop, which runs a long time, but this thing seems to go dead pretty quickly

---

### Post by oldos2er on 2017-10-28
Hi rojhack, please create a new thread for your question, for greater visibility. Thanks.

Old thread closed.

---

