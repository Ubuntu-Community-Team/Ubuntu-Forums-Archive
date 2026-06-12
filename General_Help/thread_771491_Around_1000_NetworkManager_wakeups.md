---
title: "Around 1000 NetworkManager wakeups"
date: 2008-04-27
forum: General Help
---

### Post by aeleneski on 2008-04-27
I have just upgraded from Kubuntu 7.10 to 8.04 this past weekend. Now when running powertop with nothing open I receive this:

Wakeups-from-idle per second : 1072.1   interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  88.8% (830.0)    NetworkManager : input_open_polled_device (delayed_work_timer
   2.7% ( 25.3)       <interrupt> : ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3
   2.7% ( 25.3)   USB device  1-3 : USB-PS/2 Optical Mouse (Logitech)
   1.6% ( 14.6)           firefox : futex_wait (hrtimer_wakeup)
   1.2% ( 11.1)       <interrupt> : ide0
   1.0% (  9.5)   <kernel module> : ide_do_rw_disk (ledtrig_ide_timerfunc)



Now before upgrading I was able to be around 40 ~ 50 wakeups total per second. What is causing this?
Also, I do not know if this is also the cause, but when using firefox it seems to freeze for periods at a time when trying to scroll or submitting a form.

---

### Post by aeleneski on 2008-04-29
Does anyone else have this problem?

---

