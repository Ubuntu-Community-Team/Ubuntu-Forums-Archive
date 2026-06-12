---
title: "cryptsetup: failed to setup lvm device"
date: 2008-01-17
forum: General Help
---

### Post by bren21 on 2008-01-17
Today I was setting up my tablet to work on Gutsy, I have done this many times and knew what to do. I edited the xorg.conf and then did ctrl alt backspace. The bootscript froze, so I had to hold the power button down to turn comp off. I used the alternate install cd and encrypted my install, and so after I restarted my comp I entered my encryption password, and it accepted it. But then a second or two later I got the following message:
```

setting up cryptographic volume sda5-crypt

cryptsetup: failed to setup lvm device
```

I wouldn't think that this is related to the xorg.conf editing, is it? Either way, does anyone happen to know what I should do to fix this?

---

### Post by Spydr4590 on 2008-02-06
This is a little late but I am having the same issue. The only thing I could find was this [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/151532](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/151532) Hope that helps.

---

