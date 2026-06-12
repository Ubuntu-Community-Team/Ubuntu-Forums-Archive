---
title: "After 15.04--&gt;15.10 Upgrade -- USB DVD Drive No Longer &quot;Recognized&quot;?"
date: 2016-03-26
forum: General Help
---

### Post by neu5eeCh on 2016-03-26
Okay, here's another one.

After upgrading 15.04 to 15.10, none of my systems Kubuntu or Ubuntu, recognize my eternal USB DVD drive.

[B]However: 

[/B]```
sudo lshw -C disk


```
And the result is:

```
*-cdrom                 
       description: DVD-RAM writer
       product: SuperMultiPA3761
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: TO01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
```

So, the OS sees that it's there, but neither Dolphin, nor Nautilus not Thunar (tried installing that) see it? Suggestions?

---

### Post by neu5eeCh on 2016-03-26
Just tried a different external USB DVD drive. Also doesn't work:

  *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW DRU-830A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: SS15
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom


So... it seems that there's a serious bug in 15.10 that makes USB DVD drives unusable?

---

### Post by mc4man on 2016-03-26
> logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
Do any of those actually exist?
(- at least here they seemed to have gone missing for a while in Ubuntu though have re-appeared in 16.04

---

### Post by neu5eeCh on 2016-03-27
Just woke up. Am deciding whether to bypass this altogether and upgrade to 16.04 beta. However, in answer to your question:

No. None of these actually exist. The Kernel sees the drive, but not userspace.

---

### Post by mc4man on 2016-03-27
For the various posted lshw's - was there media in the drive & what type?
Maybe put some media in that has a filesystem (ie. pretty much anything except audio cd) & see if whatever app(s) that should be able to access files can.
(using /dev/sr0

A variation would be to leave above media in the drive & reboot
Also check dmesg, /var/log/syslog after inserting above media

edit: at the end of the day 15.04/15.10 aren't that important to have and or keep going. While 16.04 has some ongoing issues there's nothing close to a deal breaker for most users.

---

### Post by neu5eeCh on 2016-03-28
> **mc4man said:**
> For the various posted lshw's - was there media in the drive & what type?

Yes, and I tried it with and without.


> **mc4man said:**
> Maybe put some media in that has a filesystem (ie. pretty much anything except audio cd) & see if whatever app(s) that should be able to access files can.

Yes, but the trouble is: I can't mount what the userland doesn't "see"? It doesn't even show up in gparted.

> **mc4man said:**
> A variation would be to leave above media in the drive & reboot. Also check dmesg, /var/log/syslog after inserting above media.

I'll try that. I did try unplugging and re-plugging the USB cable.

> **mc4man said:**
> edit: at the end of the day 15.04/15.10 aren't that important to have and or keep going. While 16.04 has some ongoing issues there's nothing close to a deal breaker for most users.

Well, funny you should mention that. I upgraded one installation to 16.04 to see if that would fix the problem. It did and didn't. The behavior is bizarre. Still no recognition of the drive in userland. However, I can play the DVD's menu in VLC. If I try to play the movie, VLC goes blank/black. Sometimes I can click the menu choices. Sometimes I can't.

I'm thinking there's a pretty bad regression somewhere?

---

