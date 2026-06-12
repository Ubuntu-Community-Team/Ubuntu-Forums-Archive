---
title: "After upgrading 18.04 to 20.04 machine sometimes fails to wake up"
date: 2020-10-11
forum: General Help
---

### Post by anewbie on 2020-10-11
I have a desktop configured to go into suspend mode after an hour or non use. about 1/4 times when i hit the keyboard the light on the machine will stop flashing indicating it is waking up but after that it won't respond to the keyboard (I never get a login prompt the monitor never gets a signal and the caps lock key doesn't toggle state). I've tried unplugging and replugging the keyboard in but as far as i can tell it is not helping and i am forced to hard power cycle to use the machine. This is the end of the syslog on a reboot (it shows no indication it was waking up at before the hard power cycle). I'm not sure if this is an event problem with usb or some other issue and no clue where to look in the logs for what is happening. This never happened with 18.04 just with buggy 20.04.

```

Oct 10 19:43:41 noone-desktop systemd-sleep[36832]: Suspending system...
Oct 10 19:43:41 noone-desktop kernel: [23856.435990] PM: suspend entry (deep)
Oct 11 12:43:36 noone-desktop systemd-modules-load[338]: Inserted module 'lp'
Oct 11 12:43:36 noone-desktop systemd-modules-load[338]: Inserted module 'ppdev'


```

---

