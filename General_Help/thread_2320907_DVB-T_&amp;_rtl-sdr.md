---
title: "DVB-T &amp; rtl-sdr?"
date: 2016-04-18
forum: General Help
---

### Post by sylkarp on 2016-04-18
Hello,
I had working dvb-t usb tv card.
It works fine with kaffeine a fiew weeks back.!!! Kaffeine seen my tv card avable (and that wasn't on Fedora :-) )

I like to use it wth VLC 

I installed dvb-t tools and scaned w-scan , 
I have a ch list but vlc wont play it.

When tested with rtl-sdr got msg.

```
rtl_test -t
Found 1 device(s):
  0:  , , SN: 

Using device 0: Lifeview LV5TDeluxe
usb_open error -3
Please fix the device permissions, e.g. by installing the udev rules file rtl-sdr.rules
Failed to open rtlsdr device #0.

```

---

### Post by howefield on 2016-04-18
Not really a *Networking & Wireless* question so thread moved to the "*General Help*" forum.

---

### Post by sylkarp on 2016-04-18
Try making sure you are included in the group "rtlsdr":
PCC -> system -> Manage users on system, 
select the groups tab and add your username to the group "rtlsdr" if it isn't there.

And this blog was helpful BUT I DID NOT  get a driver for dvb-t usb dongle on kernel 4.4.0-14-generic

[URL="http://webdarek.tumblr.com/post/53945913679/dvb-t-on-usb-not-only-tv-lv5t-deluxe-for-linux-1"]http://webdarek.tumblr.com/post/53945913679/dvb-t-on-usb-not-only-tv-lv5t-deluxe-for-linux-1
[/URL]

---

