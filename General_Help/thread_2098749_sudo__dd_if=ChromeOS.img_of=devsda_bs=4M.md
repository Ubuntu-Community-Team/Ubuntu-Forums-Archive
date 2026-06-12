---
title: "sudo  dd if=ChromeOS.img of=/dev/sda bs=4M"
date: 2012-12-27
forum: General Help
---

### Post by pookieman on 2012-12-27
Hi

I was trying to install Vanilla Chromium onto a USB drive, and I typed in the command in the title.. the process completed, then the computer shutdown, and not I get a grub loading error.. 

how can I recover from this? Or do I have to reinstall ubuntu.. I don't want to do that.. is there way i can fix it?

Many Thanks

---

### Post by AlexDudko on 2012-12-27
I presume /dev/sda was the Ubuntu installation drive not a USB one. You've simply wiped it and put Chrome image on it. The only way out would be to reinstall Ubuntu.
Be careful with dd command in future and choose the proper drive.

---

### Post by sgage on 2012-12-27
> **pookieman said:**
> Hi

I was trying to install Vanilla Chromium onto a USB drive, and I typed in the command in the title.. the process completed, then the computer shutdown, and not I get a grub loading error.. 

how can I recover from this? Or do I have to reinstall ubuntu.. I don't want to do that.. is there way i can fix it?

Many Thanks

It looks like you just over-wrote your primary drive, taking out the MBR.  :(  You probably wanted something like /dev/sdb or whatever your USBWhat were you running that dd command from? Your main Linux install? 

Unless someone else sees something I'm overlooking, I'd say you are pretty well hosed, and will have to start from scratch.

---

### Post by pookieman on 2012-12-27
> **AlexDudko said:**
> I presume /dev/sda was the Ubuntu installation drive not a USB one. You've simply wiped it and put Chrome image on it. The only way out would be to reinstall Ubuntu.
Be careful with dd command in future and choose the proper drive.

Yes basically.. :( have I completely overwritten, or can I rescue? I was reading about a supergrub utility.

---

### Post by AlexDudko on 2012-12-27
> **pookieman said:**
> Yes basically.. :( have I completely overwritten, or can I rescue? I was reading about a supergrub utility.

Unfortunately no rescue is possible only to reinstall.

---

### Post by Habitual on 2012-12-27
Hell, I'll admit doing this to an incorrect target once before. I think everyone is required to have this experience.

They don't call it "disk destroyer" for nothing!

---

### Post by pookieman on 2013-01-02
Thanks for responses.. I threw in the towel and re-installed.. wasted evening but on the other hand I gained 10Gb disk somehow?

:D

---

### Post by dcstar on 2013-01-02
> **pookieman said:**
> Thanks for responses.. I threw in the towel and re-installed.


Then MARK the thread.

---

### Post by Habitual on 2013-01-02
> **pookieman said:**
> ...I threw in the towel and re-installed.. wasted evening but on the other hand I gained 10Gb disk somehow?

:D

I don't consider getting experience "wasted" but it's your story, you
can tell it any way you like ;)

---

