---
title: "Wake up from Suspend, I am halfway there!"
date: 2017-11-27
forum: General Help
---

### Post by frappe792 on 2017-11-27
Hi all,

I want my Logitech mouse/keyboard to be able to wake up my PC from a suspended state. I have followed the instructions found at [https://ubuntuforums.org/showthread.php?t=1938480](https://ubuntuforums.org/showthread.php?t=1938480) and I am successfully able to suspend and wake up from Logitech device. I can do this repeatedly, that is UNTIL I shutdown and reboot my PC, then all is lost again.

The command I have used is   echo enabled > /sys/bus/usb/devices/2-1.2/power/wakeup

What else do I need to do in order for that to stick in the event of a complete shutdown?

Is there a further tweak where I will be able to boot from a complete shutdown using same logitech device?

---

### Post by frappe792 on 2017-12-06
Any idea? Sorry are we allowed to bump a topic?

---

### Post by leunam12 on 2017-12-06
Have you checked if your BIOS has settings for enabling wake-up from USB device?

---

### Post by vasa1 on 2017-12-06
> **frappe792 said:**
> Any idea? Sorry are we allowed to bump a topic?
See #14 in our [Posting Guidelnes]("https://ubuntuforums.org/showthread.php?t=2158945"):
> Bumping your thread if you receive no answer is acceptable. Premature and excessive bumping could attract staff attention and action. If you wish to bump, consider time zones - the one with your answer might be asleep.So bumping after about 12 hours is fine.

---

### Post by frappe792 on 2017-12-06
> **leunam12 said:**
> Have you checked if your BIOS has settings for enabling wake-up from USB device?

Yes, it is enabled. Always has been and still is. It's always resume from sleep in windows using bluetooth keyboard or mouse. Either action always brought it back to life on my external monitors.

Unfortunately, I can't make this happen with Linux.

---

### Post by frappe792 on 2017-12-09
Bump

---

### Post by frappe792 on 2017-12-16
bump

---

