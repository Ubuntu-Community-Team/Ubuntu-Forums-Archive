---
title: "USB Device Ownership - BitPim"
date: 2007-10-23
forum: General Help
---

### Post by kooseefoo on 2007-10-23
Okay, I'm trying to get bitpim to work on gutsy.

I purchased a cheap-o USB cable for my phone (USB to serial, I believe). It works perfectly fine on windows, for a start. It also works out-of-the-box on gutsy, provided I run it with gksudo.

However, running everything with gksudo doesn't seem to be a very good solution. And, I'd like to learn a bit about USB devices on ubuntu.

I followed the udev instructions on this page: [http://www.bitpim.org/help/howto-linuxusb.htm](http://www.bitpim.org/help/howto-linuxusb.htm)

I created the group, added myself to it, put in the proper VID and PID numbers (same as in the howto on that page), and otherwise set it up. However, once I add that file my phone cable ceases to even show up. lsusb showed it before, but with the rules file in place it somehow dies. Any suggestions?

Thanks!
Chris

On another note, there is a file /etc/udev/rules.d/50-bitpim.rules containing this:

```
# Commented out for now (November 2006) because the notifications may
# induce full scans, which don't always actually terminate. :-/

## Overkill, but merely exposing device names should be harmless.
## (Ensuring that the right user[s] can actually access them is another
## matter entirely.)
#BUS=="usb", ACTION=="add",    RUN+="/lib/udev/notify-bitpim add"
#BUS=="usb", ACTION=="remove", RUN+="/lib/udev/notify-bitpim del"

```

---

### Post by kooseefoo on 2007-10-23
Works fine now, with the bitpim website tweaks. I did change MODE="0660" to MODE="0664".

---

