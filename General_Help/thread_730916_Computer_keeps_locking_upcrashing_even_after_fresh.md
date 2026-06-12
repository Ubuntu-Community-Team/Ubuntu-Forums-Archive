---
title: "Computer keeps locking up/crashing even after fresh install"
date: 2008-03-21
forum: General Help
---

### Post by Aquaman420 on 2008-03-21
So my computer kept locking up/freezing and I figured it was just something stupid I did while messing around with the vast array of custumizations one can do with Linux.  So I decided to just reinstall and start from scratch since it is so painless.  I mean I wiped my home folder and everything.  Then I reinstalled and the computer is doing the same exact thing.  Ok alittle about my my computer then alittle about the details of the lock up.  I am running 7.10 32 bit 3 gigs of ram pentiumD.  So my resources are good.  There are 2 things I have definitely noticed when it crashes/locks up.  I get 16 white lines in the bottom right corner of my screen.  8 columns 2 rows.  I can move my mouse sometimes but when I can versus when I can't there are 4 lines attached to the bottom of the mouse. 1 column 4 rows.   I thought it might be a graphics driver thing so when I did my fresh reinstall I opted to use the catalyst 8.3 driver instead of the one in the repos.   I am wondering if anyone else is having this problem. and if they fixed it or what not.  Any input is always appreciated.  I am by no means a linux guru but I am stellar at following directions.  Thanks

---

### Post by dannyboy79 on 2008-03-21
you didn't tell us what graphics chipset you have?

lspci -v

you can issue that from a livecd if need be. Also, does your /var/log/Xorg.0.log show anything? Or maybe /var/log/kern.log or /var/log/syslog?

---

### Post by Aquaman420 on 2008-03-21
Sorry my graphics card is in my signature. 1650xt.  The only thing I see out of the ordinary in xorg are these lines, not sure what that pertains too.
```

(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
```

This is usually what the syslog says before I have to do a hard restart.

```
Mar 21 11:52:58 aquafuck NetworkManager: <info>  Updating allowed wireless network lists. 
Mar 21 11:52:58 aquafuck NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Mar 21 12:12:27 aquafuck -- MARK --
Mar 21 12:17:01 aquafuck /USR/SBIN/CRON[6520]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

And nothing out of the ordinary in kern.log that I can see but I can post if someone wants to take a look.

btw thank you for responding so quickly dannyboy

---

### Post by dannyboy79 on 2008-03-21
well I am not familiar with ATI graphics issues. Does using the VESA driver cause these lock ups and crashes? I know you don't want to use VESA driver permanently but it would help us troubleshoot if this is really a graphics issue or otherwise. Good luck.

---

### Post by Aquaman420 on 2008-03-21
Yeah I could give vesa a shot and do alittle more gum shoeing.  I have confirmed that the lock ups happen with compiz enabled and disabled so off to debunk the next.  Well thanks again.

---

### Post by BurnUp on 2008-03-21
Hello,

Man i have exactlly the same problem and i'm with a nvidia graphics chipset.

I just try to install the unix drivers i downloaded from nvidia and it does the same white screen and sometimes it freezes.

This started to happen 2 days after a fresh installation of ubuntu.

Yhea, i think maybe it has to have with compiz, but i love compiz and i don't want to turn it off because it's candie for my eyes lolol.

Maybe there is another solution ??

---

