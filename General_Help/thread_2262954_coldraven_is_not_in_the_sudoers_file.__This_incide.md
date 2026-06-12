---
title: "coldraven is not in the sudoers file.  This incident will be reported. ??"
date: 2015-01-28
forum: General Help
---

### Post by coldraven on 2015-01-28
While trying to get Mtink to speak to my printer I have somehow removed myself from the sudoers group.
So I followed the advice here:
[http://www.maketecheasier.com/fixing-sudo-error-in-ubuntu/](http://www.maketecheasier.com/fixing-sudo-error-in-ubuntu/)

I booted to grub, dropped to root shell and did
```
usermod -a -G sudo coldraven
```

I get the result "Cannot lock etc/password, try again later"

This is Ubuntu 14.04, any tips on what I'm doing wrong?
I wish someone would fix Mtink, for old printers it's really handy :(

---

### Post by slickymaster on 2015-01-28
Do you see any **.lock** files in **/etc/**, in particular:
[LIST]
[*]passwd.lock
[*]shadow.lock
[*]group.lock
[*]gshadow.lock
[/LIST]

---

### Post by coldraven on 2015-01-28
No .lock suffix just
passwd
passwd-
shadow
shadow-
group
group-
gshadow
gshadow-

When I selected "Recovery mode" from Grub after a lot of modules etc. scrolled up the screen it stopped at [A4 Tech mouse], It's a laser mouse.
After a 30 sec. wait I hit enter a couple of times and got to the text screen where I could select "Drop to root shell".
I'm wondering if the boot process never finished entirely and the HDD got stuck in read only mode.

Edit: I will try again without the mouse and report back shortly.

---

### Post by steeldriver on 2015-01-28
did you remember to remount the root filesystem with read-write permissions? 
```

mount -o remount,rw /

```

Else you won't be able to write to the files in /etc

---

### Post by slickymaster on 2015-01-28
> **steeldriver said:**
> did you remember to remount the root filesystem with read-write permissions? 
```

mount -o remount,rw /

```

This ^^^

---

### Post by coldraven on 2015-01-28
> **steeldriver said:**
> did you remember to remount the root filesystem with read-write permissions? 
```

mount -o remount,rw /

```

Else you won't be able to write to the files in /etc

No, I never knew about that.
 I did just notice that at the top of the recovery text screen it does say (filesystem state: read-only) 
I also noticed as the modules loaded that a "kernel taint" was being caused in module wlan by (I forgot the exact words) a mixture of proprietary and "something", and that "something" was now disabled. As I tried to take a photograph it scrolled off the screen :(

Going for reboot NOW, back soon!

---

### Post by deadflowr on 2015-01-28
1) yeah, the recovery mode mounts read-only by default for the purpose of letting you look over any problems, without the possibility of accidentally breaking anything --by executing some command or doing something erroneous, which would be written to the system causing even more problems, if that makes sense.

2)kernel taints usually mean you have a close-source module, which the kernel developers cannot/will not do anything about.
You see this any time you install the ati/nvidia proprietary drivers for a graphics card.
I assume it can apply to some wifi drivers as well.

---

### Post by coldraven on 2015-01-28
Thanks everyone, that fixed it.

For your reading pleasure I just grepped the error that I mentioned before ;)
```
dmesg | grep taint
[   16.274103] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.274112] Disabling lock debugging due to kernel taint
[   16.285394] wl: module verification failed: signature and/or  required key missing - tainting kernel


```

This is probably why my bluetooth is still not fixed :(
See this thread, I was planning to bump it anyway: [URL="http://ubuntuforums.org/showthread.php?t=2260024"]http://ubuntuforums.org/showthread.php?t=2260024

[/URL]

---

### Post by slickymaster on 2015-01-28
coldraven, please don't forget to mark the thread as SOLVED.

---

