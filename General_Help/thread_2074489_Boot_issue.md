---
title: "Boot issue"
date: 2012-10-21
forum: General Help
---

### Post by adduds on 2012-10-21
I have an odd boot issue after my system passes through Grub 2 and I select Ubuntu I get this screen.

I keep all my system up to date.

Any ideas???

Please let me know if you you need anymore information to trouble shoot

---

### Post by oldfred on 2012-10-22
I cannot read screen to tell where it is stopping, but sometimes the error is actually earlier in the process.

From liveCD you can drill down to /var/log and look at demesg to see the same commands that scroll by.

Have you tried booting from recovery or second line in grub menu.

What video card. Sometimes you need to add boot options for video or other system related issues.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ~LoKe on 2012-10-22
Nothing there indicates any issues. Post dmesg.

Also, for the hell of it, try pressing ctrl+alt+f2 and ctrl+alt+f7.

---

### Post by adduds on 2012-10-22
> **~LoKe said:**
> Nothing there indicates any issues. Post dmesg.

Also, for the hell of it, try pressing ctrl+alt+f2 and ctrl+alt+f7.

Ya I tried ctrl+alt+f2/f7 

How can I post dmesg when it just freezes

---

### Post by oldfred on 2012-10-22
Does not liveCD/USB boot?

Then from liveCD drill down into your install and find dmesg. Post it in code tags as it will be long.

---

### Post by ~LoKe on 2012-10-22
> **adduds said:**
> Ya I tried ctrl+alt+f2/f7 

How can I post dmesg when it just freezes

Boot into the LiveCD and mount your /dev/sdX partition to, say /mount/fix and look at /mount/fix/var/log/dmesg

---

