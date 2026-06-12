---
title: "LightDM and KVM fail on boot; attempted fix and now stuck in boot loop"
date: 2014-04-25
forum: General Help
---

### Post by galvanick_lucipher on 2014-04-25
Hello Friends:
Running up to date ubuntu on a dual boot homebrew pc, with  linux and W7 on separate SSDs. 16G ram, Intel  i5-2500K CPU @ 3.30GHz.

Everything running smoothly until last linux update.  First boot thereafter got a quasi-BSOD desktop; rebooted into recovery mode and tried earlier versions; no change.  Then ran recovery mode and ran dpkg after starting networking.  Machine booted thereafter with an odd looking desktop  - no wallpaper, program icons were greyed out; but all programs worked.  Verbose boot mode showed this:

[http://imgur.com/Djdc0qD](http://imgur.com/Djdc0qD)

(through all of this, W7 still boots and runs fine.)

Did a little browsing through the forums and concluded that since LightDM was the culprit; in a related thread someone suggested editing lightdm.conf to add "sleep2" before the call to the manager; did that and now I get a loop boot with the Ubuntu logo and five dots changing color endlessly. 

So, in sum, I need to figure out how to undo the bad fix so I can boot into some working Ubuntu configuration; and then hopefully fix the lightdm and/or kvm issues; all of the above is way over my head. Any help appreciated.

UPDATE:  Fixed boot loop problem by booting from USB and editing lightdm.conf back to its prior state.  Still need help in getting lightdm and kvm running.

---

