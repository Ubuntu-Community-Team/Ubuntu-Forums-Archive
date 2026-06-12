---
title: "Hard drive noise and freezing but only in Ubuntu"
date: 2008-04-15
forum: General Help
---

### Post by DrQuincy on 2008-04-15
I have Gutsy and XP on this machine. As of today when I boot to Ubuntu it freezes about a sixth the way through the orange loading bar and the hard drive makes a really strange beeping noise. It's a mechanical noise though, not from the speaker. You'd think the hard drive is on its way out (even though it's two months old) but XP is working fine - I'm writing this post from XP. Any idea what this could be? If I boot to Ubuntu recovery mode from GRUB that loads fine too. Any ideas? It's so odd because the hard drive sounds perfectly healthy now.

Thanks.

---

### Post by bingoUV on 2008-04-15
Be very very afraid. Verify that you are not facing this bug : [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695). Use the workaround mentioned there.

---

### Post by DrQuincy on 2008-04-15
Mine is clicking every couple of seconds and at a specific time. I don't think that's my problem. Any other suggestions? Are there any hard drive diagnostics I can run in recovery mode?

---

### Post by JayStapleton on 2008-04-15
You can download the ultimate boot CD, which has diagnostics for most harddrives

---

### Post by GCoffee on 2008-04-15
Have you got some software on ubuntu causing it that starts on startup?

---

### Post by bingoUV on 2008-04-15
Is it a Hitachi hard disk? Makes it more likely that you are facing that bug.

---

### Post by DrQuincy on 2008-04-15
> **bingoUV said:**
> Is it a Hitachi hard disk? Makes it more likely that you are facing that bug.

It's a Samsung HD321KJ.


There's nothing I can think of that's installed that would interfere. I have the same software installed on a Dell and that's fine.

I'll try the Live CD then.

Is there a log I can look at in recovery mode that would show at what point in boot up it stalls?

Thanks for your help so far.

---

### Post by DrQuincy on 2008-04-15
I don't believe it, I've fixed it and it wasn't the hard drive. It was the DVD drive! It was trying to read the DVD during boot up (not as the boot disk though, too late for that) and stalling. The noise was the drive. It sounded an awful lot like a hard drive failure though.

I'm pretty sure the drive AND DVD are okay so am not sure why it was stalling the boot up. Anyway, it works now!

Thanks again.

---

