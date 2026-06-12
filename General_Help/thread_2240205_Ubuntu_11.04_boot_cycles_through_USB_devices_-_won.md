---
title: "Ubuntu 11.04 boot cycles through USB devices - won't boot"
date: 2014-08-18
forum: General Help
---

### Post by DantePasquale on 2014-08-18
I'm having an issue with a Ubuntu 11.04 server that won't boot up completely.

It discovers a couple of USB devices (keyboard and mouse).

Then seems to time-out and re-discovers the same 2 USB devices.

Any ideas on how to debug this? I tried disabling USB from BIOS (HP DL 360 g7) but then no keyboard so it wouldn't boot from the Ubuntu menu ;(

Also, the hard drive is encrypted and I don't know how to boot up on a USB stick, mount the luks files to edit them and possibly black-list the USB devices to see if I can get it to boot.

Anyone know how to do this?

---

### Post by sandyd on 2014-08-18
> **DantePasquale said:**
> I'm having an issue with a Ubuntu 11.04 server that won't boot up completely.

It discovers a couple of USB devices (keyboard and mouse).

Then seems to time-out and re-discovers the same 2 USB devices.

Any ideas on how to debug this? I tried disabling USB from BIOS (HP DL 360 g7) but then no keyboard so it wouldn't boot from the Ubuntu menu ;(

Also, the hard drive is encrypted and I don't know how to boot up on a USB stick, mount the luks files to edit them and possibly black-list the USB devices to see if I can get it to boot.

Anyone know how to do this?

Hi, Ubuntu 11.04 has reached End of Life as of October 28, 2012 and no longer receives updates of any kind. In addition, its repositories have been disabled and moved to the old repositories URL.

Upgrading (or installing) a newer version of Ubuntu may help you solve your your issues.

---

### Post by vipulkumar7 on 2014-08-18
Yes Ubuntu 11.04 reaches to EOL (End of life)

---

